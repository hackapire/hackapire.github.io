# 01 - API Esplorative 
# 01.03 - Get Bank Products

Elenca i `products` della `bank` specificata

`GET` `:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID/products`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` per l'hackathon: `http://hackapire-sandbox.westeurope.azurecontainer.io:8080`
##### Parametri:
- `:BANK_ID` di esempio: `hackapire-bank-1`

esempio richiesta/risposta:
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/products' 
``` 
``` json
{
  "products": [
    {
      "bank_id": "hackapire-bank-1",
      "code": "0dae-DS",
      "name": "Generic Credit Card Product",
      "category": "Credit Card",
      "family": "Credit Card",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "0e5c-F45",
      "name": "RESERVE ACCOUNT",
      "category": "Account",
      "family": "Service",
      "super_family": "Service",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "23ba-FD2",
      "name": "Generic Savings",
      "category": "Savings",
      "family": "Credit",
      "super_family": "Credit",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "2bc8-DF4",
      "name": "Generic Overdraft Product",
      "category": "Overdraft",
      "family": "Loan",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "30f0-KJH",
      "name": "Generic Savings",
      "category": "Savings",
      "family": "Credit",
      "super_family": "Credit",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "3d0c-SD4",
      "name": "Generic MTA/Current Account",
      "category": "Current Accounts",
      "family": "Account",
      "super_family": "Service",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "3ded-FDF",
      "name": "Red Mastercard",
      "category": "Credit Card",
      "family": "Credit Card",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "601d-FD5",
      "name": "Generic MTA Upgrades Product",
      "category": "MTA Upgrades",
      "family": "MTA Upgrades",
      "super_family": "MTA Upgrades",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "6056-M35",
      "name": "Mutuo di sera bel tempo si spera",
      "category": "Mortgage",
      "family": "Mortgage",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "7f3d-FDS",
      "name": "OFFSET FLEXIBLE MORTGAGE",
      "category": "Mortgage",
      "family": "Mortgage",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "8ed0-FDFD",
      "name": "Generic Overdraft Product",
      "category": "Overdraft",
      "family": "Loan",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "9499-JF",
      "name": "Loan Quote",
      "category": "Loan",
      "family": "Loan",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "a1c5-FD1",
      "name": "Generic Credit Card Product",
      "category": "Credit Cards",
      "family": "Credit Card",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "a24a-M55",
      "name": "Generic MTA/Current Account",
      "category": "Current Accounts",
      "family": "Service",
      "super_family": "Service",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "b192-J87",
      "name": "Premier Mastercard",
      "category": "Credit Card",
      "family": "Credit Card",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "bcef-H44",
      "name": "Big Boss Account",
      "category": "Account",
      "family": "Service",
      "super_family": "Service",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "be7a-DFD",
      "name": "Generic MTA Upgrades Product",
      "category": "MTA Upgrades",
      "family": "MTA Upgrades",
      "super_family": "MTA Upgrades",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "e401-DFD",
      "name": "Generic Credit Card Product",
      "category": "Credit Cards",
      "family": "Credit Card",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "ef2e-DF4",
      "name": "Generic MTA Upgrades Product",
      "category": "MTA Upgrades",
      "family": "MTA Upgrades",
      "super_family": "MTA Upgrades",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    },
    {
      "bank_id": "hackapire-bank-1",
      "code": "ef52-AA",
      "name": "Loan Quote",
      "category": "Loan",
      "family": "Loan",
      "super_family": "Lending",
      "more_info_url": "www.example.com",
      "details": "",
      "description": "",
      "meta": {
        "license": {
          "id": "copyright2015",
          "name": "Copyright"
        }
      }
    }
  ]
}
```

Nota: il caricamento dei prodotti puà essere fatto dagli users con entitlment per mezzo della API:
`:API_END_POINT/obp/v3.1.0/sandbox/data-import`