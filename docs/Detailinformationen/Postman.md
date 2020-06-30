# Testen mit Postman

Für Tests kann auch SoapUI oder jeder andere REST Client mit OAuth 2.0 Unterstützung eingesetzt werden.
Unter diesen beiden Adressen können Sie eine Postman Collection und eine Postman Environment herunterladen:
- [Collection](https://raw.githubusercontent.com/fiep-poc/assets/master/postman/FIT-Connect.postman_collection.json)
- [Environment](https://raw.githubusercontent.com/fiep-poc/assets/master/postman/FIT-Connect.postman_environment.json)

## API Aufruf mit Postman OAuth 2.0 Konfiguration

Mit diesen Angaben können Sie das API z.B. via Postman nutzen. Dazu wählen sie zunächst den Bereich "Authorization" aus. Danach kann der Button "Get New Access Token" genutzt werden.

![Authorization konfigurieren](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/14_authorization.png)

![Token holen](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/15_request_token.png)

![Use Token](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/16_use_token.png)

Mit diesem Token kann das API erfolgreich aufgerufen werden.

![API Aufruf](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/17_api_call.png)

In diesem Beispiel wurde eine neue Destination angelegt.
