# 04 - Effettuare transazioni  
# 04.02 - Bonifico SEPA con IBAN 

<!--
per il funzionamento del SEPA occorre che sia stato inserita la COUNTERPARTY
tabella: PUBLIC.MAPPEDCOUNTERPARTY
vedi anche tabelle: PUBLIC.MAPPEDCOUNTERPARTYMETADATA

http://hackapire-sandbox.westeurope.azurecontainer.io:8080/obp/v3.1.0/banks/:BANK_ID/accounts/:ACCOUNT_ID/:VIEW_ID/counterparties

- :BANK_ID
- :ACCOUNT_ID
- :VIEW_ID
{
    "name": "CounterpartyName",
    "description": "Zadkielini S.p.A.",
    "other_account_routing_scheme": "accountNumber",
    "other_account_routing_address": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
    "other_account_secondary_routing_scheme": "IBAN",
    "other_account_secondary_routing_address": "DE8937000440532013000",
    "other_bank_routing_scheme": "bankCode",
    "other_bank_routing_address": "hackaton-bank-1",
    "other_branch_routing_scheme": "branchNumber",
    "other_branch_routing_address": "10010",
    "is_beneficiary": true,
    "bespoke": [
        {
            "key": "englishName",
            "value": "english Name"
        }
    ]
}

se manca la couterparti si otterrà l'errore
{
    "error": "OBP-50000: Unknown Error.  <- OBP-30004: Counterparty not found. The BANK_ID / ACCOUNT_ID specified does not exist on this server. Current Value: BANK_ID(counterparty.otherBankRoutingAddress=hackaton-bank-1) and ACCOUNT_ID(counterparty.otherAccountRoutingAddress=conto-44c51a80-4877-4d6b-abc8-2befaa8d3624), please use correct OBP BankAccount to create the Counterparty.!!!!! "
}
-->

`POST` 
`:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID/accounts/:ACCOUNT_ID/:VIEW_ID/transaction-request-types/:TRANSACTION_REQUEST_TYPE/transaction-requests`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` dell'hackathon: http://hackapire-sandbox.westeurope.azurecontainer.io:8080
##### Parametri:
- `:BANK_ID` per esempio `hackapire-bank-1`
- `:ACCOUNT_ID` per esempio `conto-44c51a80-4877-4d6b-abc8-2befaa8d3624`
- `:VIEW_ID` per esempio `owner`
- `:TRANSACTION_REQUEST_TYPE` is `SEPA`

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
    "value": {
        "currency": "EUR",
        "amount": "2"
    },
    "to": {
        "iban": "DE8937000440532013000"
    },
    "description": "Prova di una richiesta di transazione SEPA per Hydro Man",
    "charge_policy": "SHARED",
    "future_date": "20190128"
}
```

esempio risposta: 
``` json 
{
    "id": "231636f4-6e94-47a2-ab88-bd46afcfc8b4",
    "type": "SEPA",
    "from": {
        "bank_id": "hackapire-bank-1",
        "account_id": "conto-di-iron-man"
    },
    "details": {
        "to_sepa": {
            "iban": "DE8937000440532013000"
        },
        "value": {
            "currency": "EUR",
            "amount": "2"
        },
        "description": "Prova di una richiesta di transazione SEPA per Hydro Man"
    },
    "transaction_ids": [
        "8291a103-043e-49aa-b8e8-a9d93918a4ee"
    ],
    "status": "COMPLETED",
    "start_date": "2019-01-24T03:45:50Z",
    "end_date": "2019-01-24T03:45:50Z",
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


## 03.02.01 - Bonifico SEPA ( beneficiario specificato con IBAN ) con approvazione per  importi superiori 1000 euro 
Esempio Body Richiesta: 
``` json 
{
    "value": {
        "currency": "EUR",
        "amount": "1870"
    },
    "to": {
        "iban": "DE8937000440532013000"
    },
    "description": "",
    "charge_policy": "SHARED",
    "future_date": "20190128"
}
```
Se l'impoto supera 1000 EUR è necessaria una conferma ed i conti non variano fino a quando non viene data tale conferma tecnicamente detta `Answer Transaction Request Challenge`

Esempio risposta
``` json
{
    "id": "12506be5-f2b3-4099-9541-969cdd367675",
    "type": "SEPA",
    "from": {
        "bank_id": "hackapire-bank-1",
        "account_id": "conto-di-iron-man"
    },
    "details": {
        "to_sepa": {
            "iban": "DE8937000440532013000"
        },
        "value": {
            "currency": "EUR",
            "amount": "1870"
        },
        "description": ""
    },
    "transaction_ids": [
        ""
    ],
    "status": "INITIATED",
    "start_date": "2019-01-24T04:23:22Z",
    "end_date": "2019-01-24T:04:23:22Z",
    "challenge": {
        "id": "b78fd65c-07a8-470f-b2cf-9a1ef35ba8d4",
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

per la `Answer Transaction Request Challenge`  occorre riprendere dalla risposta precedente: 
- 1) "id": "12506be5-f2b3-4099-9541-969cdd367675", 
- 2)  "challenge.id": "b78fd65c-07a8-470f-b2cf-9a1ef35ba8d4"
e passarli alla API seguente: 

`POST` `:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID/accounts/:ACCOUNT_ID/:VIEW_ID/transaction-request-types/:TRANSACTION_REQUEST_TYPE/transaction-requests/:TRANSACTION_REQUEST_ID/challenge`

`:BANK_ID` per esempio `hackapire-bank-1`
`:ACCOUNT_ID` per esempio `conto-di-iron-man`
`:VIEW_ID` per esempio `owner`
`:TRANSACTION_REQUEST_TYPE` is `SEPA`
`:TRANSACTION_REQUEST_ID` per esempio `12506be5-f2b3-4099-9541-969cdd367675` ovvero l'`id` raccolto dalla precente risposta 

Nel Body della richiesta dovremo ivece riportare il `challenge.id` preso dalla risposta precedente ed una `answer` fissa `123` 
``` json 
{
    "id": "b78fd65c-07a8-470f-b2cf-9a1ef35ba8d4",
    "answer": "123"
}
```
se tutto è corretto la transazione verrà confermata e si avrà la movimentazione sui conti come atteso.

Esempio di risposta relativa all'esempio precedente 
``` json
{
    "id": "12506be5-f2b3-4099-9541-969cdd367675",
    "type": "SEPA",
    "from": {
        "bank_id": "hackapire-bank-1",
        "account_id": "conto-di-iron-man"
    },
    "details": {
        "to_sepa": {
            "iban": "DE8937000440532013000"
        },
        "value": {
            "currency": "EUR",
            "amount": "1870"
        },
        "description": ""
    },
    "transaction_ids": [
        "1c5165c6-7703-4b5d-a000-1e1c3caf9fbc"
    ],
    "status": "COMPLETED",
    "start_date": "2019-01-29T00:00:00Z",
    "end_date": "2019-01-29T00:00:00Z",
    "challenge": {
        "id": "b78fd65c-07a8-470f-b2cf-9a1ef35ba8d4",
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



## Riferimenti alla documentazione OBP ( link esterni ): 
### Create Transaction Request (SEPA)
https://psd2-apiexplorer.openbankproject.com/?version=3.1.0&list-all-banks=false&core=&psd2=true&obwg=&ignoredefcat=&bank_id=psd201-bank-x--uk&account_id=Hackathon&view_id=owner#vv2_1_0-createTransactionRequestSepa

### Answer Transaction Request Challange
https://psd2-apiexplorer.openbankproject.com/?version=3.1.0&list-all-banks=false&core=&psd2=true&obwg=&ignoredefcat=&bank_id=psd201-bank-x--uk&account_id=Hackathon&view_id=owner#vv2_1_0-answerTransactionRequestChallenge