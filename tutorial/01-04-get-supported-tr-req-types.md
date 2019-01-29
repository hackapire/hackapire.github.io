# 01 - API Esplorative 
# 01.04 -  Get Bank supported `transaction_request_types` 
Elenca i tipi di richiesta di transazione supportati

`GET` `:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID/transaction-request-types`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` per l'hackathon: `http://hackapire-sandbox.westeurope.azurecontainer.io:8080`
##### Parametri:
- `:BANK_ID` di esempio: `hackapire-bank-1`

esempio richiesta:
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/transaction-request-types' 
``` 
risposta:
``` json
{
  "transaction_request_types": [
    {
      "transaction_request_type": "SANDBOX_TAN"
    },
    {
      "transaction_request_type": "COUNTERPARTY"
    },
    {
      "transaction_request_type": "SEPA"
    }
  ]
}
```

Nota: questi `transaction_request_type` devono essere usati quando si richiede  una transazione o si conferma una transazione, in questo tutorial prevediamo un paio di esempi per i tipi: `SANDBOX_TAN` e `SEPA`
