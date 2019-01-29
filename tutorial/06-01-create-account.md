# 06 - Varie:  
# 06.01 - Create Account 
Creazione di un nuovo conto
<!-- 
per i conti vedi tabella: 
    PUBLIC.MAPPERACCOUNTHOLDERS
-->
`PUT` `:API_/obp/v3.1.0/banks/:BANK_ID/accounts/:ACCOUNT_ID`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` per l'hackathon: `http://hackapire-sandbox.westeurope.azurecontainer.io:8080`
##### Parametri:
`:BANK_ID` is `hackapire-bank-1`
`:ACCOUNT_ID` is `conto-di-iron-man`
lo user `hackapire4` ha id `43306b20-9675-4b61-a184-92c32373688a` che useremo nel RequestBody

RequestBody (JSON):
``` json
{
    "user_id": "43306b20-9675-4b61-a184-92c32373688a",
    "label": "iron-man",
    "type": "CURRENT",
    "balance": {
        "currency": "EUR",
        "amount": "0"
    },
    "branch_id": "041",
    "account_routing": {
        "scheme": "OBP",
        "address": "IT123456"
    }
}
```
risposta: 
``` json
{
    "user_id": "43306b20-9675-4b61-a184-92c32373688a",
    "label": "iron-man",
    "type": "CURRENT",
    "balance": {
        "currency": "EUR",
        "amount": "0.00"
    },
    "branch_id": "041",
    "account_routing": {
        "scheme": "OBP",
        "address": "IT123456"
    }
}
```




## Note e possibili eccezioni
L'entitlement `CanCreateAccount` per la BANK_ID specificata deve essere in possesso di chi esegue la creazione di nuovi conti per evitare l'errore: 
``` json 
{
    "error": "OBP-20006: User is missing one or more roles:  CanCreateAccount or create account for self"
}
```
il valore iniziale di `balance.amount` deve essere a `0` per evitare l'errore:
```
{
    "error": "OBP-30109: Initial Balance of Account must be Zero (0)."
}
```