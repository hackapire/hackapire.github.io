# 03 - Interrogare Saldi e Movimenti di conto 
# 03.01 - Get Account by Id ( core )

`GET` `:API_ENDPOINT/obp/v3.1.0/my/banks/:BANK_ID/accounts/:ACCOUNT_ID/accou\nt

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` dell'hackathon: http://hackapire-sandbox.westeurope.azurecontainer.io:8080
##### Parametri:
- `:BANK_ID` di esempio: `hackapire-bank-1`
- `:ACCOUNT_ID` di sesempio: `conto-44c51a80-4877-4d6b-abc8-2befaa8d3624`

## Esempi richiesta/risposta:
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/my/banks/hackapire-bank-1/accounts/conto-44c51a80-4877-4d6b-abc8-2befaa8d3624/account' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.n0_0ZnC0q14fRCS1QJiNPAGFswMQlLm_WDP4m3CqqO4"' \
-H 'Content-Type: application/json' | jq
```

``` json
{
  "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
  "bank_id": "hackapire-bank-1",
  "label": "Label",
  "number": "3047035405",
  "owners": [
    {
      "id": "hackapire2",
      "provider": "http://127.0.0.1:8080",
      "display_name": "hackapire2"
    }
  ],
  "type": "CURRENT",
  "balance": {
    "currency": "EUR",
    "amount": "50024.00"
  },
  "account_routings": [
    {
      "scheme": "OBP",
      "address": "UK123456"
    }
  ],
  "account_rules": []
}
```

..proviamo con conto di un altro utente
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/my/banks/hackapire-bank-1/accounts/conto-di-iron-man/account' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.n0_0ZnC0q14fRCS1QJiNPAGFswMQlLm_WDP4m3CqqO4"'  \
-H 'Content-Type: application/json' | jq
```
``` json 
{
  "error": "OBP-20017: Current user does not have access to the view. Please specify a valid value for VIEW_ID."
}
``` 

cambiamo `token` e usiamo quello dello user: `hackapire4` che ha visibiltà sul `conto-di-iron-man`
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/my/banks/hackapire-bank-1/accounts/conto-di-iron-man/account' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.AAqLZhUv3rWkQSFYU3FNMKq0_Rpq-CYYoZYLkhw6GTU"' \
-H 'Content-Type: application/json' | jq
```
``` json 
{
  "id": "conto-di-iron-man",
  "bank_id": "hackapire-bank-1",
  "label": "iron-man",
  "number": "3542773224",
  "owners": [
    {
      "id": "hackapire4",
      "provider": "http://127.0.0.1:8080",
      "display_name": "hackapire4"
    }
  ],
  "type": "CURRENT",
  "balance": {
    "currency": "EUR",
    "amount": "0.00"
  },
  "account_routings": [
    {
      "scheme": "OBP",
      "address": "IT123456"
    }
  ],
  "account_rules": []
}
```

dopo avere effettuato una transazione sul contro avremo: 
``` json
{
  "id": "conto-di-iron-man",
  "bank_id": "hackapire-bank-1",
  "label": "iron-man",
  "number": "3542773224",
  "owners": [
    {
      "id": "hackapire4",
      "provider": "http://127.0.0.1:8080",
      "display_name": "hackapire4"
    }
  ],
  "type": "CURRENT",
  "balance": {
    "currency": "EUR",
    "amount": "170.00"
  },
  "account_routings": [
    {
      "scheme": "OBP",
      "address": "IT123456"
    }
  ],
  "account_rules": []
}
```
