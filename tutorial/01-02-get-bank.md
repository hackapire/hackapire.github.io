# 01 - API Esplorative 
# 01.02 - Get Bank 
Verifica l'esistenza di una specifica bank tra quelle presenti nella sandbox.
<!-- può essere utile per recuperare il `bank_routing` -->

`GET` `:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` per l'hackathon: `http://hackapire-sandbox.westeurope.azurecontainer.io:8080`
##### Parametri:
- `:BANK_ID` di esempio: `hackapire-bank-1`

esempio richiesta:
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1' 
``` 
risposta:
``` json
{
  "id": "hackapire-bank-1",
  "short_name": "Hackathon Bank 1",
  "full_name": "First Hackathon Bank",
  "logo": null,
  "website": null,
  "bank_routing": {
    "scheme": "OBP",
    "address": "hackapire-bank-1"
  }
}
```