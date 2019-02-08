# 03 - Interrogare Saldi e Movimenti di conto 
# 03.02 - Get Transaction For Account ( full )
`GET` `:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID/accounts/:ACCOUNT_ID/:VIEW_ID/transactions`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` dell'hackathon: http://hackapire-sandbox.westeurope.azurecontainer.io:8080
##### Parametri:
- `:BANK_ID` di esempio: `hackapire-bank-1`
- `:ACCOUNT_ID` di sesempio: `conto-44c51a80-4877-4d6b-abc8-2befaa8d3624`
- `:VIEW_ID` di esempio: `owner`   ( vedere 04-01 per avere la lista delle possibili view per account )

esempio richiesta:
``` bash
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/accounts/conto-44c51a80-4877-4d6b-abc8-2befaa8d3624/owner/transactions' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.n0_0ZnC0q14fRCS1QJiNPAGFswMQlLm_WDP4m3CqqO4"' \
-H 'Content-Type: application/json' | jq
```
risposta:
``` json
{
  "transactions": [
    {
      "id": "c63bd928-52c9-47d0-985d-172c8ca9abef",
      "this_account": {
        "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
        "bank_routing": {
          "scheme": "OBP",
          "address": "hackapire-bank-1"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
        "holders": [
          {
            "name": "hackapire2",
            "is_alias": false
          }
        ]
      },
      "other_account": {
        "id": "dgXNPveMloP2VacdX3NJPA-upQsqIoi2wai7H8UwsdE",
        "holder": {
          "name": "hackapire2",
          "is_alias": false
        },
        "bank_routing": {
          "scheme": "hackapire-bank-1",
          "address": "OBP"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
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
          "amount": "50024.00"
        },
        "value": {
          "currency": "EUR",
          "amount": "10.00"
        }
      },
      "metadata": {
        "narrative": null,
        "comments": [],
        "tags": [],
        "images": [],
        "where": null
      }
    },
    {
      "id": "76d23c70-463c-4280-bad4-3bfa2059c109",
      "this_account": {
        "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
        "bank_routing": {
          "scheme": "OBP",
          "address": "hackapire-bank-1"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
        "holders": [
          {
            "name": "hackapire2",
            "is_alias": false
          }
        ]
      },
      "other_account": {
        "id": "dgXNPveMloP2VacdX3NJPA-upQsqIoi2wai7H8UwsdE",
        "holder": {
          "name": "hackapire2",
          "is_alias": false
        },
        "bank_routing": {
          "scheme": "hackapire-bank-1",
          "address": "OBP"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
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
    },
    {
      "id": "13fb4293-5f01-461b-ba91-f6cb9db03a1c",
      "this_account": {
        "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
        "bank_routing": {
          "scheme": "OBP",
          "address": "hackapire-bank-1"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
        "holders": [
          {
            "name": "hackapire2",
            "is_alias": false
          }
        ]
      },
      "other_account": {
        "id": "dgXNPveMloP2VacdX3NJPA-upQsqIoi2wai7H8UwsdE",
        "holder": {
          "name": "hackapire2",
          "is_alias": false
        },
        "bank_routing": {
          "scheme": "hackapire-bank-1",
          "address": "OBP"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
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
        "posted": "2019-01-19T17:19:25Z",
        "completed": "2019-01-19T17:19:25Z",
        "new_balance": {
          "currency": "EUR",
          "amount": "50014.00"
        },
        "value": {
          "currency": "EUR",
          "amount": "10.00"
        }
      },
      "metadata": {
        "narrative": null,
        "comments": [],
        "tags": [],
        "images": [],
        "where": null
      }
    },
    {
      "id": "d2149b49-b468-467d-919a-e305d0d98d71",
      "this_account": {
        "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
        "bank_routing": {
          "scheme": "OBP",
          "address": "hackapire-bank-1"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
        "holders": [
          {
            "name": "hackapire2",
            "is_alias": false
          }
        ]
      },
      "other_account": {
        "id": "dgXNPveMloP2VacdX3NJPA-upQsqIoi2wai7H8UwsdE",
        "holder": {
          "name": "hackapire2",
          "is_alias": false
        },
        "bank_routing": {
          "scheme": "hackapire-bank-1",
          "address": "OBP"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
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
        "posted": "2019-01-19T17:19:25Z",
        "completed": "2019-01-19T17:19:25Z",
        "new_balance": {
          "currency": "EUR",
          "amount": "49994.00"
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
    },
    {
      "id": "56693ab3-9ee9-4200-8ad6-0c694bf3d58e",
      "this_account": {
        "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
        "bank_routing": {
          "scheme": "OBP",
          "address": "hackapire-bank-1"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
        "holders": [
          {
            "name": "hackapire2",
            "is_alias": false
          }
        ]
      },
      "other_account": {
        "id": "dgXNPveMloP2VacdX3NJPA-upQsqIoi2wai7H8UwsdE",
        "holder": {
          "name": "hackapire2",
          "is_alias": false
        },
        "bank_routing": {
          "scheme": "hackapire-bank-1",
          "address": "OBP"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
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
        "type": "SEPA",
        "description": "This is a SEPA Transaction Request for Cassandra Xavier",
        "posted": "2019-01-19T16:59:23Z",
        "completed": "2019-01-19T16:59:23Z",
        "new_balance": {
          "currency": "EUR",
          "amount": "50004.00"
        },
        "value": {
          "currency": "EUR",
          "amount": "2.00"
        }
      },
      "metadata": {
        "narrative": null,
        "comments": [],
        "tags": [],
        "images": [],
        "where": null
      }
    },
    {
      "id": "35832ebf-483d-4ff9-b47c-ab89b5898662",
      "this_account": {
        "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
        "bank_routing": {
          "scheme": "OBP",
          "address": "hackapire-bank-1"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
        "holders": [
          {
            "name": "hackapire2",
            "is_alias": false
          }
        ]
      },
      "other_account": {
        "id": "dgXNPveMloP2VacdX3NJPA-upQsqIoi2wai7H8UwsdE",
        "holder": {
          "name": "hackapire2",
          "is_alias": false
        },
        "bank_routing": {
          "scheme": "hackapire-bank-1",
          "address": "OBP"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
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
        "type": "SEPA",
        "description": "This is a SEPA Transaction Request for Cassandra Xavier",
        "posted": "2019-01-19T16:59:23Z",
        "completed": "2019-01-19T16:59:23Z",
        "new_balance": {
          "currency": "EUR",
          "amount": "50000.00"
        },
        "value": {
          "currency": "EUR",
          "amount": "-2.00"
        }
      },
      "metadata": {
        "narrative": null,
        "comments": [],
        "tags": [],
        "images": [],
        "where": null
      }
    },
    {
      "id": "69b93ba5-e651-4a01-aaf1-371d8142e826",
      "this_account": {
        "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
        "bank_routing": {
          "scheme": "OBP",
          "address": "hackapire-bank-1"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
        "holders": [
          {
            "name": "hackapire2",
            "is_alias": false
          }
        ]
      },
      "other_account": {
        "id": "dgXNPveMloP2VacdX3NJPA-upQsqIoi2wai7H8UwsdE",
        "holder": {
          "name": "hackapire2",
          "is_alias": false
        },
        "bank_routing": {
          "scheme": "hackapire-bank-1",
          "address": "OBP"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
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
        "type": "SEPA",
        "description": "This is a SEPA Transaction Request for Cassandra Xavier",
        "posted": "2019-01-18T16:32:48Z",
        "completed": "2019-01-18T16:32:48Z",
        "new_balance": {
          "currency": "EUR",
          "amount": "50002.00"
        },
        "value": {
          "currency": "EUR",
          "amount": "2.00"
        }
      },
      "metadata": {
        "narrative": null,
        "comments": [],
        "tags": [],
        "images": [],
        "where": null
      }
    },
    {
      "id": "b587e0f0-8fb8-432a-8482-b3080f9f0e00",
      "this_account": {
        "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
        "bank_routing": {
          "scheme": "OBP",
          "address": "hackapire-bank-1"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
        "holders": [
          {
            "name": "hackapire2",
            "is_alias": false
          }
        ]
      },
      "other_account": {
        "id": "dgXNPveMloP2VacdX3NJPA-upQsqIoi2wai7H8UwsdE",
        "holder": {
          "name": "hackapire2",
          "is_alias": false
        },
        "bank_routing": {
          "scheme": "hackapire-bank-1",
          "address": "OBP"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
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
        "type": "SEPA",
        "description": "This is a SEPA Transaction Request for Cassandra Xavier",
        "posted": "2019-01-18T16:32:48Z",
        "completed": "2019-01-18T16:32:48Z",
        "new_balance": {
          "currency": "EUR",
          "amount": "49998.00"
        },
        "value": {
          "currency": "EUR",
          "amount": "-2.00"
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
  ]
}}
```

```
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/accounts/conto-di-iron-man/owner/transactions' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.n0_0ZnC0q14fRCS1QJiNPAGFswMQlLm_WDP4m3CqqO4"' \
-H 'Content-Type: application/json' | jq
```
``` json 
{
  "error": "OBP-50200: Connector cannot return the data we requested. <- OBP-20017: Current user does not have access to the view. Please specify a valid value for VIEW_ID. Current VIEW_ID (owner)"
}
```

```
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/accounts/conto-di-iron-man/owner/transactions' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.AAqLZhUv3rWkQSFYU3FNMKq0_Rpq-CYYoZYLkhw6GTU"' \
-H 'Content-Type: application/json' | jq
```
```
{
  "transactions": []
}
```

...dopo aver effettuato una transazione verso questo contoo avremo una risposta del tipo: 
``` json 
{
  "transactions": [
    {
      "id": "7c66dc6a-3d11-4a69-8a07-0ebe3808ea15",
      "this_account": {
        "id": "conto-di-iron-man",
        "bank_routing": {
          "scheme": "OBP",
          "address": "hackapire-bank-1"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "IT123456"
          }
        ],
        "holders": [
          {
            "name": "hackapire4",
            "is_alias": false
          }
        ]
      },
      "other_account": {
        "id": "gTG335R38OQ9XZHybVpMq3NTksAb-SaqFRApQigxeqQ",
        "holder": {
          "name": "hackapire2",
          "is_alias": false
        },
        "bank_routing": {
          "scheme": "hackapire-bank-1",
          "address": "OBP"
        },
        "account_routings": [
          {
            "scheme": "OBP",
            "address": "UK123456"
          }
        ],
        "metadata": {
          "public_alias": "ALIAS_5D98E3",
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
        "description": "IronMan for president",
        "posted": "2019-01-28T18:33:49Z",
        "completed": "2019-01-28T18:33:49Z",
        "new_balance": {
          "currency": "EUR",
          "amount": "170.00"
        },
        "value": {
          "currency": "EUR",
          "amount": "170.00"
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
  ]
}
```



<!-- NOTA: 
le TRX si trovan nella tabella PUBLIC.MAPPEDTRANSACTIONREQUEST 
-->