# 05 - Verificare la disponibilità di fondi di un conto 
# 05.01 - Check Available Funds

`GET` `:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID/accounts/:ACCOUNT_ID/:VIEW_ID/funds-available?amount=:AMOUNT&currency=:CURRENCY`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` dell'hackathon: http://hackapire-sandbox.westeurope.azurecontainer.io:8080
##### Parametri:
- `:AMOUNT` è l'importo per cui si vuole ottenere risposta relativa alla disponibilità sul conto  
- `:CURRENCY` è la valuta, esempio `EUR`

esempi:
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/accounts/conto-44c51a80-4877-4d6b-abc8-2befaa8d3624/owner/funds-available?amount=1&currency=EUR' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.n0_0ZnC0q14fRCS1QJiNPAGFswMQlLm_WDP4m3CqqO4", consumer_key="a5v4pkonyuqz5a5f5jcphchym5v3carluotwk24o"' \
-H 'Content-Type: application/json' | python -m json.tool
```
``` json
{
    "answer": "yes",
    "available_funds_request_id": "node03fcx3q92snqz1oix1yua4s53j6",
    "date": "2019-01-28T11:12:21Z"
}
```
...riproviamo con un importo maggiore
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/accounts/conto-44c51a80-4877-4d6b-abc8-2befaa8d3624/owner/funds-available?amount=100000&currency=EUR' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.n0_0ZnC0q14fRCS1QJiNPAGFswMQlLm_WDP4m3CqqO4", consumer_key="a5v4pkonyuqz5a5f5jcphchym5v3carluotwk24o"' \
-H 'Content-Type: application/json' | python -m json.tool
```
``` json
{
    "answer": "no",
    "available_funds_request_id": "node015hbxhxf5jtpetgaghtyd9ewg7",
    "date": "2019-01-28T11:14:06Z"
}
```

## Caso in cui non si disponga di una view con `can_query_available_funds` la `answer` resta vuota
per vedere cosa è permesso nella `view` vedi [bank-accounts-views](./06-02-bank-accounts-views.md)
se la view di nome `owner` ha `"can_query_available_funds": false,` allora la risposta sarà vuota, del tipo: 
``` json
{
    "answer": "",
    "date": "2019-01-27T09:48:33Z",
    "available_funds_request_id": "node01ah8fl1mikgsrugp1nnp6lyca363"
}
```