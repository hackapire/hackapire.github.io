# 04 - Effettuare transazioni  
# 04.01 - Bonifico interno 

`POST` 
`:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID/accounts/:ACCOUNT_ID/:VIEW_ID/transaction-request-types/:TRANSACTION_REQUEST_TYPE/transaction-requests`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` dell'hackathon: http://hackapire-sandbox.westeurope.azurecontainer.io:8080
##### Parametri:
- `:BANK_ID` is `hackapire-bank-1`
- `:ACCOUNT_ID` is `conto-44c51a80-4877-4d6b-abc8-2befaa8d3624`
- `:VIEW_ID` is `owner`
- `:TRANSACTION_REQUEST_TYPE` is `SANDBOX_TAN`

Attenzione, se l'importo della tranzazione supera 1000 (EUR) la transazione non viene staccata subito , anzichè terminare ( stato `COMPLETED` ) resterà in stato `INITIALIZED` in attesa di una *Challange* , per questo motivo nella risposta non si ottiene alcun `transaction_ids` ma avremo  un `id`  ed un `` che dovremo usare nella chiamata alla API di conferma ( cosidetta: *Answer Transaction Request Challenge* vedere qui sotto secondo esempio per caso di questo tipo )

Richiede autenticazione:
Se si usa il `token` staccato da uno user non titolato ad effettuare trsansazioni dal conto specificato otterremo come risposta 
``` json 
{
    "error": "OBP-40002: Insufficient authorisation to create TransactionRequest. The Transaction Request could not be created because you don't have access to the owner view of the from account or you don't have access to canCreateAnyTransactionRequest."
}
```

Esempio `POST`
Request Body: 
``` json 
{
    "to": {
        "bank_id": "hackapire-bank-1",
        "account_id": "conto-di-iron-man"
    },
    "value": {
        "currency": "EUR",
        "amount": "170"
    },
    "description": "IronMan for president"
}
```
risposta
``` json 
{
    "id": "d6ba8bd7-3ec4-47ba-a1d6-52c9fba34a00",
    "type": "SANDBOX_TAN",
    "from": {
        "bank_id": "hackapire-bank-1",
        "account_id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624"
    },
    "details": {
        "to_sandbox_tan": {
            "bank_id": "hackapire-bank-1",
            "account_id": "conto-di-iron-man"
        },
        "value": {
            "currency": "EUR",
            "amount": "170"
        },
        "description": "IronMan for president"
    },
    "transaction_ids": [
        "c6f75ba7-b1fd-4aa5-b9ba-1c70713e14f6"
    ],
    "status": "COMPLETED",
    "start_date": "2019-01-28T18:33:49Z",
    "end_date": "2019-01-28T18:33:49Z",
    "challenge": null,
    "charge": {
        "summary": "Total charges for completed transaction",
        "value": {
            "currency": "EUR",
            "amount": "2.0"
        }
    }
}
```

### CASO di transazione superiore a 1000 
Request Body: 
``` json 
{
    "to": {
        "bank_id": "hackapire-bank-1",
        "account_id": "conto-di-iron-man"
    },
    "value": {
        "currency": "EUR",
        "amount": "1500"
    },
    "description": "ricarica millecinquecento euro sul conto di iron-man"
}
```

risposta: 
``` json 
{
    "id": "82fa5e63-4b6d-4466-8043-60942e4ce167",
    "type": "SANDBOX_TAN",
    "from": {
        "bank_id": "hackapire-bank-1",
        "account_id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624"
    },
    "details": {
        "to_sandbox_tan": {
            "bank_id": "hackapire-bank-1",
            "account_id": "conto-di-iron-man"
        },
        "value": {
            "currency": "EUR",
            "amount": "1500"
        },
        "description": "ricarica millecinquecento euro sul conto di iron-man"
    },
    "transaction_ids": [
        ""
    ],
    "status": "INITIATED",
    "start_date": "2019-01-28T17:34:57Z",
    "end_date": "2019-01-28T17:34:57Z",
    "challenge": {
        "id": "d7f71814-dd60-4bad-bd6a-373e6a6e7569",
        "allowed_attempts": 3,
        "challenge_type": "SANDBOX_TAN"
    },
    "charge": {
        "summary": "Total charges for completed transaction",
        "value": {
            "currency": "EUR",
            "amount": "2.0"
        }
    }
}
```
in questo caso, avendo superato i 1000EUR è necessaria una conferma ed i conti non variano fino a quando non viene data tale conferma tecnicamente detta `Answer Transaction Request Challenge`

per questo occorre riprendere dalla risposta precedente: 
- 1) "id": "82fa5e63-4b6d-4466-8043-60942e4ce167",
- 2)  "challenge.id": "d7f71814-dd60-4bad-bd6a-373e6a6e7569"
e passarli alla API seguente: 

`POST` `:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID/accounts/:ACCOUNT_ID/:VIEW_ID/transaction-request-types/:TRANSACTION_REQUEST_TYPE/transaction-requests/:TRANSACTION_REQUEST_ID/challenge`

`:BANK_ID` is `hackapire-bank-1`
`:ACCOUNT_ID` is `conto-44c51a80-4877-4d6b-abc8-2befaa8d3624`
`:VIEW_ID` is `owner`
`:TRANSACTION_REQUEST_TYPE` is `SANDBOX_TAN`
`:TRANSACTION_REQUEST_ID` is `82fa5e63-4b6d-4466-8043-60942e4ce167` ovvero l'`id` raccolto dalla precente risposta 

Nel Body della richiesta dovremo ivece riportare il `challenge.id` ed una risposta fissa `123` 
``` json 
{
    "id": "d7f71814-dd60-4bad-bd6a-373e6a6e7569",
    "answer": "123"
}
```
se tutto è corretto la transazione verrà confermata e si avrà la movimentazione sui conti come atteso.

Esempio di risposta relativa all'esempio precedente 
``` json
{
    "id": "82fa5e63-4b6d-4466-8043-60942e4ce167",
    "type": "SANDBOX_TAN",
    "from": {
        "bank_id": "hackapire-bank-1",
        "account_id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624"
    },
    "details": {
        "to_sandbox_tan": {
            "bank_id": "hackapire-bank-1",
            "account_id": "conto-di-iron-man"
        },
        "value": {
            "currency": "EUR",
            "amount": "1500"
        },
        "description": "ricarica millecinquecento euro sul conto di iron-man"
    },
    "transaction_ids": [
        "a27c9e2c-aced-4fef-9ded-0d22496c7afd"
    ],
    "status": "COMPLETED",
    "start_date": "2019-01-28T00:00:00Z",
    "end_date": "2019-01-28T00:00:00Z",
    "challenge": {
        "id": "d7f71814-dd60-4bad-bd6a-373e6a6e7569",
        "allowed_attempts": 3,
        "challenge_type": "SANDBOX_TAN"
    },
    "charge": {
        "summary": "Total charges for completed transaction",
        "value": {
            "currency": "EUR",
            "amount": "2.0"
        }
    }
}
```
notare che abbiamo ottenuta una `transaction_ids` , se interrogghiamo i conti ora vedremo la variazione dei saldi.

Se , per sbaglio viene confermata una richiestra di transazione che era già stata confermata si otterrà in risposta:
``` json 
{
    "error": "OBP-40011: Transaction Request Status is not INITIATED."
}
```

## Riferimenti alla documentazione OBP ( link esterni ): 
### Create Transaction Request (SANDBOX_TAN)
https://psd2-apiexplorer.openbankproject.com/?version=3.1.0&list-all-banks=false&core=&psd2=true&obwg=&ignoredefcat=&bank_id=psd201-bank-x--uk&account_id=Hackathon&view_id=owner#vv2_1_0-createTransactionRequestSandboxTan

### Answer Transaction Request Challange
https://psd2-apiexplorer.openbankproject.com/?version=3.1.0&list-all-banks=false&core=&psd2=true&obwg=&ignoredefcat=&bank_id=psd201-bank-x--uk&account_id=Hackathon&view_id=owner#vv2_1_0-answerTransactionRequestChallenge
