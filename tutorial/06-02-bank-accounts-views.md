# 06 - Varie
# 06.02 - Get Views for Account 
controllo visibilità delle viste disponibili sul conto  

`GET` `:API_ENDPOINT/obp/v3.1.0/banks/:BANK_ID/accounts/:ACCOUNT_ID/views`

##### Endpoint:
- `:API_ENDPOINT` per le prove in locale `http://localhost:8080`
- `:API_ENDPOINT` per l'hackathon: `http://hackapire-sandbox.westeurope.azurecontainer.io:8080`

esempio richiesta: 
``` bash 
curl -X "GET" 'http://localhost:8080/obp/v3.1.0/banks/hackapire-bank-1/accounts/conto-44c51a80-4877-4d6b-abc8-2befaa8d3624/views' \
-H 'Authorization: DirectLogin token="eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.n0_0ZnC0q14fRCS1QJiNPAGFswMQlLm_WDP4m3CqqO4", consumer_key="a5v4pkonyuqz5a5f5jcphchym5v3carluotwk24o"' \
-H 'Content-Type: application/json' | jq
```
risposta:
``` json
{
    "views": [
        {
            "alias": "",
            "can_add_comment": true,
            "can_add_corporate_location": true,
            "can_add_counterparty": true,
            "can_add_image": true,
            "can_add_image_url": true,
            "can_add_more_info": true,
            "can_add_open_corporates_url": true,
            "can_add_physical_location": true,
            "can_add_private_alias": true,
            "can_add_public_alias": true,
            "can_add_tag": true,
            "can_add_transaction_request_to_any_account": true,
            "can_add_transaction_request_to_own_account": true,
            "can_add_url": true,
            "can_add_where_tag": true,
            "can_delete_comment": true,
            "can_delete_corporate_location": true,
            "can_delete_image": true,
            "can_delete_physical_location": true,
            "can_delete_tag": true,
            "can_delete_where_tag": true,
            "can_edit_owner_comment": true,
            "can_query_available_funds": true,
            "can_see_bank_account_balance": true,
            "can_see_bank_account_bank_name": true,
            "can_see_bank_account_credit_limit": false,
            "can_see_bank_account_currency": true,
            "can_see_bank_account_iban": true,
            "can_see_bank_account_label": true,
            "can_see_bank_account_national_identifier": true,
            "can_see_bank_account_number": true,
            "can_see_bank_account_owners": true,
            "can_see_bank_account_routing_address": true,
            "can_see_bank_account_routing_scheme": true,
            "can_see_bank_account_swift_bic": true,
            "can_see_bank_account_type": true,
            "can_see_bank_routing_address": true,
            "can_see_bank_routing_scheme": true,
            "can_see_comments": true,
            "can_see_corporate_location": true,
            "can_see_image_url": true,
            "can_see_images": true,
            "can_see_more_info": true,
            "can_see_open_corporates_url": true,
            "can_see_other_account_bank_name": true,
            "can_see_other_account_iban": true,
            "can_see_other_account_kind": true,
            "can_see_other_account_metadata": true,
            "can_see_other_account_national_identifier": true,
            "can_see_other_account_number": true,
            "can_see_other_account_routing_address": true,
            "can_see_other_account_routing_scheme": true,
            "can_see_other_account_swift_bic": true,
            "can_see_other_bank_routing_address": true,
            "can_see_other_bank_routing_scheme": true,
            "can_see_owner_comment": true,
            "can_see_physical_location": true,
            "can_see_private_alias": true,
            "can_see_public_alias": true,
            "can_see_tags": true,
            "can_see_transaction_amount": true,
            "can_see_transaction_balance": true,
            "can_see_transaction_currency": true,
            "can_see_transaction_description": true,
            "can_see_transaction_finish_date": true,
            "can_see_transaction_metadata": true,
            "can_see_transaction_other_bank_account": true,
            "can_see_transaction_start_date": true,
            "can_see_transaction_this_bank_account": true,
            "can_see_transaction_type": true,
            "can_see_url": true,
            "can_see_where_tag": true,
            "description": "Owner View",
            "hide_metadata_if_alias_used": false,
            "id": "owner",
            "is_public": false,
            "metadata_view": "owner",
            "short_name": "Owner"
        }
    ]
}
```

Controllare di ottenere `"can_query_available_funds": true,` per la **view** che si intende usare allo step [di controlo della disponibilità di fondi](./05-01-check-available-funds.md)