# Direct Login Token 
Gli esempi riportati in questo tutorial sono stati provati in locale e pertanto puntano a  `http://localhost:8080/` ; tale endpoint dovrà essere sostituito con l' `:API_ENDPOINT` dell'hackathon;

La password va definita quando si crea il nuovo utente oppure richiesta al team tecnico si vogliono usare utenti predefiniti. 


## Esempi stacco token per il `Direct Login`

### Stacchiamo il token dello user: `hackapire2`

richiesta:
``` bash 
curl -X "POST" 'http://localhost:8080/my/logins/direct' \
-H 'Authorization: DirectLogin username="hackapire2",  password="************", consumer_key="a5v4pkonyuqz5a5f5jcphchym5v3carluotwk24o"' \
-H 'Content-Type: application/json'
```
risposta:
``` json
{"token":"eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.40i6M0VPnHyEQJmuaP5pra931af-Npd6BsiWR1aQQt0"}
```
### Stacchiamo il token dello user: `hackapire4`
richiesta:
``` json
curl -X "POST" 'http://localhost:8080/my/logins/direct' \
-H 'Authorization: DirectLogin username="hackapire4",  password="************", consumer_key="a5v4pkonyuqz5a5f5jcphchym5v3carluotwk24o"' \
-H 'Content-Type: application/json'
```
risposta:
``` json
{"token":"eyJhbGciOiJIUzI1NiJ9.eyIiOiIifQ.AAqLZhUv3rWkQSFYU3FNMKq0_Rpq-CYYoZYLkhw6GTU"}
```

### messaggio di errore per credenziali non valide
`{"error":"OBP-20004: Invalid login credentials. Check username/password."}`

