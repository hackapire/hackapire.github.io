# intro alle API disponibili per hackapire
<!-- 
- Read the documentation
- Play with the sandbox
- Write some test code 
- Get some breat idea
-->
## 01. API *"esplorative"*, ...non necessitano di autenticazione
- [01.01 - **Get Banks** - elenca le `banks` presenti nella *sandbox*](./tutorial/01-01-get-banks.md)
- [01.02 - **Get Bank**  - verifica presenza di una specifica `bank`](./tutorial/01-02-get-bank.md)
- [01.03 - **Get Bank Products** - elenca i `products` della `bank` specificata](./tutorial/01-03-get-bank-products.md)
- [01.04 - **Get Supported Transaction Request Types** - elenca i tipi di richiesta di transazione supportati](./tutorial/01-04-get-supported-tr-req-types.md)

## 02. Ottenere una lista dei conti correnti 
- [02.01 - **Get Accounts at Bank (Minimal)** - elenca gli `accounts` di una `bank`](./tutorial/02-01-get-acconts-at-bank-minimal.md)

## 03. Interrogare saldi/movimenti di conto 
- [03.01 - **Get Account by Id ( core )**](./tutorial/03-01-get-acconts-by-id.md)
- [03.02 - **Get Transaction For Account ( full )**](./tutorial/03-02-get-trx-for-account-full.md)
- [03.03 - **Get Transaction By Id**](./tutorial/03-03-get-trx-by-id.md)

## 04. Effettuare una transazione
- [04.01 - **Create Transaction Request** (bonifico interno)](./tutorial/04-01-create-transaction-request-bo-interno.md)
- [04.02 - **Create Transaction Request** (SEPA)](./tutorial/04-02-create-transaction-request-sepa.md)

## 05. Verificare la disponibilità fondi di un conto corrente
- [05.01 - **Check Available Funds** -  controllo visibilità delle viste disponibili sul conto](./tutorial/05-01-check-available-funds.md)

## 06. Varie
- [06.01 - **Create Account** - creazione di un nuovo conto](./tutorial/06-01-create-account.md)
- [06.02 - **Get Views for Account** - controllo visibilità delle viste disponibili sul conto](./tutorial/06-02-bank-accounts-views.md)


## Supporto
Serve aiuto ? 
  - chiedi come fare aprendo una nuova [issue da qui](https://github.com/hackapire/hackapire.github.io/issues/new)
  - vedi la [lista completa delle issues](https://github.com/hackapire/hackapire.github.io/issues?utf8=✓&q=)

## Contributi 
Vuoi dare il tuo contributo ?
  - vedi come [creare una pull request](https://help.github.com/articles/creating-a-pull-request/)

## Mock
Vuoi provare con un mock ?
Se la sandbox è troppo complicata da usare
Possiamo pubblicare mock per richieste in `GET` su specifiche **branches**  
### Esempio di mock pubblicato nella branch: [mock-001](https://github.com/hackapire/hackapire.github.io/tree/mock-001)
``` bash
$ curl https://raw.githubusercontent.com/hackapire/hackapire.github.io/mock-001/obp/v3.1.0/my/banks/BANK_ID/accounts/ACCOUNT_ID/account/mocked-response.json
{
    "id": "conto-44c51a80-4877-4d6b-abc8-2befaa8d3624",
    "bank_id": "hackapire-bank-1",
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

