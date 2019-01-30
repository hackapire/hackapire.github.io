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

lo user `hackapire4` ha `id` che vale`43306b20-9675-4b61-a184-92c32373688a` che useremo nel RequestBody
I valori degli `id` degli users possono essere ricavati dalla API `GET` `:API_ENDPOINT/obp/v3.1.0/users`
<!-- 99.01 Get All Users -->


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

in caso si conto già presente la risposta sarà del tipo: 
``` json
{
    "error": "OBP-30208: Account_ID already exists at the Bank."
}
```

<!--
per prova è stato inserito anche: 

`:BANK_ID` is `hackapire-bank-1`
`:ACCOUNT_ID` is `conto-di-ant-man`

{
    "user_id": "43306b20-9675-4b61-a184-92c32373688a",
    "label": "ant-man",
    "type": "CURRENT",
    "balance": {
        "currency": "EUR",
        "amount": "0.00"
    },
    "branch_id": "041",
    "account_routing": {
        "scheme": "OBP",
        "address": "IT000001"
    }
} 
--->


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

<!--
create couterparty 

{
    "error": "OBP-20017: Current user does not have access to the view. Please specify a valid value for VIEW_ID."
}

{
    "error": "OBP-30004: Counterparty not found. The BANK_ID / ACCOUNT_ID specified does not exist on this server. Current BANK_ID = hackapire-bank-2. and Current ACCOUNT_ID = conto-di-ant-man. "
}


esempio OK ( con il token di user: `hackapire4` )
http://hackapire-sandbox.westeurope.azurecontainer.io:8080/obp/v3.1.0/banks/:BANK_ID/accounts/:ACCOUNT_ID/:VIEW_ID/counterparties

:BANK_ID hackapire-bank-1
:ACCOUNT_ID conto-di-ant-man
:VIEW_ID owner

{
    "name": "counterparty conto-di-ant-man ",
    "description": "Hackantini S.p.A.",
    "other_account_routing_scheme": "accountNumber",
    "other_account_routing_address": "conto-di-ant-man",
    "other_account_secondary_routing_scheme": "IBAN",
    "other_account_secondary_routing_address": "DE8937000440532013001",
    "other_bank_routing_scheme": "bankCode",
    "other_bank_routing_address": "hackapire-bank-1",
    "other_branch_routing_scheme": "branchNumber",
    "other_branch_routing_address": "10020",
    "is_beneficiary": true,
    "bespoke": [
        {
            "key": "englishName",
            "value": "english Name"
        }
    ]
}

response: 
``` json 
{
    "name": "counterparty conto-di-ant-man ",
    "description": "Hackantini S.p.A.",
    "created_by_user_id": "43306b20-9675-4b61-a184-92c32373688a",
    "this_bank_id": "hackapire-bank-1",
    "this_account_id": "conto-di-ant-man",
    "this_view_id": "owner",
    "counterparty_id": "47622cad-70fb-45cc-be36-5d37b1c7cf43",
    "other_bank_routing_scheme": "bankCode",
    "other_bank_routing_address": "hackapire-bank-1",
    "other_branch_routing_scheme": "branchNumber",
    "other_branch_routing_address": "10020",
    "other_account_routing_scheme": "accountNumber",
    "other_account_routing_address": "conto-di-ant-man",
    "other_account_secondary_routing_scheme": "IBAN",
    "other_account_secondary_routing_address": "DE8937000440532013001",
    "is_beneficiary": true,
    "bespoke": [
        {
            "key": "englishName",
            "value": "english Name"
        }
    ],
    "metadata": {
        "publicAlias": "ALIAS_1D37B7",
        "moreInfo": "",
        "url": "",
        "imageURL": "",
        "openCorporatesURL": "",
        "corporateLocation": null,
        "physicalLocation": null,
        "privateAlias": ""
    }
}
```




-->