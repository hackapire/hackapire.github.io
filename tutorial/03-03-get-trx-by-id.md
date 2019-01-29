# 03 - Interrogare Saldi e Movimenti di conto 
# 03.03 - Get Transaction By Id 

`GET` `:API_ENDPOINT/obp/v3.1.0/my/banks/:BANK_ID/accounts/:ACCOUNT_ID/:VIEW_ID/transactions/:TRANSACTION_ID/transaction`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` dell'hackathon: http://hackapire-sandbox.westeurope.azurecontainer.io:8080
##### Parametri:
- `:BANK_ID` di esempio: `hackapire-bank-1`
- `:ACCOUNT_ID` di sesempio: `conto-44c51a80-4877-4d6b-abc8-2befaa8d3624`
- `:VIEW_ID` di esempio: `owner`   ( vedere 04-01 per avere la lista delle possibili view per account )
- `:TRANSACTION_ID` di esempio   ( puà essere presa da transactions[0].id della lista transazioni discussa in 02.02 ) 
esempio richiesta:
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/accounts/conto-44c51a80-4877-4d6b-abc8-2befaa8d3624/owner/transactions/76d23c70-463c-4280-bad4-3bfa2059c109/transaction' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.n0_0ZnC0q14fRCS1QJiNPAGFswMQlLm_WDP4m3CqqO4", consumer_key="a5v4pkonyuqz5a5f5jcphchym5v3carluotwk24o"' \
-H 'Content-Type: application/json' | jq
```
risposta:
``` json
{
  "id": "76d23c70-463c-4280-bad4-3bfa2059c109",
  "this_account": {
    "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
    "holders": [
      {
        "name": "hackapire2",
        "is_alias": false
      }
    ],
    "number": "3047035405",
    "kind": "CURRENT",
    "IBAN": null,
    "swift_bic": null,
    "bank": {
      "national_identifier": null,
      "name": "Fist Hackaton Bank"
    }
  },
  "other_account": {
    "id": "dgXNPveMloP2VacdX3NJPA-upQsqIoi2wai7H8UwsdE",
    "holder": {
      "name": "hackapire2",
      "is_alias": false
    },
    "number": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
    "kind": "CURRENT",
    "IBAN": "UK123456",
    "swift_bic": "hackapire-bank-1",
    "bank": {
      "national_identifier": null,
      "name": "hackapire-bank-1"
    },
    "metadata": {
      "public_alias": "ALIAS_C2C5D2",
      "private_alias": null,
      "more_info": null,
      "URL": null,
      "image_URL": null,
      "open_corporates_URL": null,
      "corporate_location": null,
      "physical_location": null
    }
  },
  "details": {
    "type": "SANDBOX_TAN",
    "description": "Sponsor campagna elettorale Hydro-Man ",
    "posted": "2019-01-22T09:48:11Z",
    "completed": "2019-01-22T09:48:11Z",
    "new_balance": {
      "currency": "EUR",
      "amount": "50004.00"
    },
    "value": {
      "currency": "EUR",
      "amount": "-10.00"
    }
  },
  "metadata": {
    "narrative": null,
    "comments": [],
    "tags": [],
    "images": [],
    "where": null
  }
}
```