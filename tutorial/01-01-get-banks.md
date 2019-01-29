# 01 - API Esplorative 
## 01.01 - Get Banks 
Ottiene l'elenco delle `Banks` disponibili nella sandbox. 

`GET` `:API_ENDPOINT/obp/v3.1.0/banks`

##### Endpoint: 
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` per l'hackathon: `http://hackapire-sandbox.westeurope.azurecontainer.io:8080`

esempio richiesta:
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks' 
``` 
risposta:
``` json
{
    "banks": [
        {
            "bank_routing": {
                "address": "bank-xxx",
                "scheme": "OBP"
            },
            "full_name": "The Bank of XXX",
            "id": "bank-xxx",
            "logo": "https://static.openbankproject.com/images/sandbox/bank_x.png",
            "short_name": "Bank XXX",
            "website": "https://www.example.com"
        },
        {
            "bank_routing": {
                "address": "hackapire-bank-1",
                "scheme": "OBP"
            },
            "full_name": "First Hackathon Bank",
            "id": "hackapire-bank-1",
            "logo": null,
            "short_name": "Hackathon Bank 1",
            "website": null
        }
    ]
}
```
