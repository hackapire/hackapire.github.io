# hackapire.github.io
... stiamo preparando il prossimo evento.
## Supporto
Serve aiuto ? 
- apri una nuova [issue da qui](https://github.com/hackapire/hackapire.github.io/issues/new)
- vedi la lista delle issue

## Contributi 
Vuoi dare il tuo contributo ?
 vedi come [creare una pull request](https://help.github.com/articles/creating-a-pull-request/)

## Mock
Vuoi provare con un mock ?
Se la sandbox è troppo complicata da usare
Possiamo pubblicare mock per richieste in `GET` su specifiche **branches**  
### Esempio di mock pubblicato nella brench: `mock-001`
``` bash
$ curl https://raw.githubusercontent.com/hackapire/hackapire.github.io/mock-001/obp/v3.1.0/my/banks/BANK_ID/accounts/ACCOUNT_ID/account/mocked-response.json
{
    "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
    "bank_id": "hackaton-bank-1",
    "label": "Label",
    "number": "3047035405",
    "owners": [
        {
            "id": "hackapire2",
            "provider": "http://127.0.0.1:8080",
            "display_name": "hackapire2"
        }
    ],
    "type": "CURRENT",
    "balance": {
        "currency": "EUR",
        "amount": "50024.00"
    },
    "account_routings": [
        {
            "scheme": "OBP",
            "address": "UK123456"
        }
    ],
    "account_rules": []
}
```

vedi **Supporto** e **Contributi** per proporre i tuoi mock

