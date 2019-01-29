# 02 - Ottenere una lista dei conti correnti 
# 02.01 - Get Accounts at Bank ( minimal )
la lista dei conti è quella relativa all'utente delle API;  
occorre passare quindi nella testata `Authorization` il [token ottenuto durante la fase di autenticazione](00-00-token.md) per evitare di ottere l'errore:
 `{"error":"OBP-20001: User not logged in. Authentication is required!"}`

`GET` `:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID/accounts/private`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` per l'hackathon: `http://hackapire-sandbox.westeurope.azurecontainer.io:8080`
##### Parametri:
- `:BANK_ID` di esempio: `hackapire-bank-1`

Da questa API possiamo ottenere un valido `accounts[0].id` che è il dato chiave del conto che ri-useremo nelle successive chiamate , ad esempio per verificare il saldo del conto.

### Esempi richiesta/risposta:
#### Primo esempio: lista conti di `hackapire2`

``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/accounts/private' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.n0_0ZnC0q14fRCS1QJiNPAGFswMQlLm_WDP4m3CqqO4"' \
-H 'Content-Type: application/json' | jq
```

Notare che riceviamo anche `account_routings` e `views` che possono esserci utili 
per chiamare altre API ( es: per la verifica della desponibilità di fondi )

``` json
{
  "accounts": [
    {
      "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
      "label": "Label",
      "bank_id": "hackapire-bank-1",
      "account_type": "CURRENT",
      "account_routings": [
        {
          "scheme": "OBP",
          "address": "UK123456"
        }
      ],
      "views": [
        {
          "id": "owner",
          "short_name": "Owner",
          "description": "Owner View",
          "is_public": false
        }
      ]
    }
  ]
}
```
#### Secondo Esempio: lista conti di `hackapire4`
ripetiamo la stessa chiamata dell'esempio precedente ma ora con il token di `hackapire4` (  per info su come staccare un tolen per la DirectLogin vedi [qui](./00-00-token.md) )
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/accounts/private' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.AAqLZhUv3rWkQSFYU3FNMKq0_Rpq-CYYoZYLkhw6GTU"' \
-H 'Content-Type: application/json' | jq
```
``` json 
{
  "accounts": [
    {
      "id": "conto-di-iron-man",
      "label": "iron-man",
      "bank_id": "hackapire-bank-1",
      "account_type": "CURRENT",
      "account_routings": [
        {
          "scheme": "OBP",
          "address": "IT123456"
        }
      ],
      "views": [
        {
          "id": "owner",
          "short_name": "Owner",
          "description": "Owner View",
          "is_public": false
        }
      ]
    }
  ]
}
```