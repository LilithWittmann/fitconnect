# Registrierung und Client-Verwaltung

Die Anmeldung erfolgt per Mail.

Die Mail muss an registrierung@fiep-poc.de gesendet werden.

Folgende Angaben müssen in der Mail enthalten sein:
- Name der Anwendung		(z.B. FitConnectShowCase)
- Angaben zur Firma/Behörde
  - Name 				(z.B. Dataport)
  - Adresse			(z.B. Hannover)
  - Webseite			(z.B. https://www.dataport.de)
- AnwenderID				(z.B. 41754caf-c9b2-4f09-b8ac-f3df0d46c318)
- Gewünschter API Bereich 		(entweder Sender oder Subscriber)

Die AnwenderID kann frei gewählt werden.

**Beipiel:**

> **Betreff:** FIT-Connect Registrierung
> 
> **Mailinhalt:**
> 
> Wir bitten um die Registrierung einer Anwendung für FIT-Connect Beta 6
> 
> <pre>Name der Anwendung:         TestAnwendung
> Angaben zur Firma/Behörde:
>     Name Land               Sachsen
>     Adresse                 Dresden
>     Webseite                https://www.sachsen.de
> AnwenderID                  41754caf-c9b2-4f09-b8ac-f3df0d46c318
> Gewünschter API Bereich     Subscriber
> </pre>

## Hinweise zum Aufruf der API mit OAuth2

Um das von ihnen gewünschte API im Rahmen ihrer Anwendung aufzurufen, Gehen sie wie folgt vor:

![API Zugriff](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/13_api_zugriff.png)

Verfahrensschritte:

1) Die Clientanwendung sendet die Authentifizierungsanforderung an den Autorisierungsserver, um ein Zugriffstoken zu erhalten.

2) Der Autorisierungsserver überprüft die Anforderung und generiert ein Zugriffstoken für den Client.

3) Der Client verwendet dieses Zugriffstoken, um HTTP-Anforderungen an das API-Gateway zu senden.

4) Das API-Gateway führt dann folgendes aus:
    - Identifiziert die Anwendung anhand der client_Id.
    - Überprüft das Token lokal oder remote, wenn es lokal nicht möglich ist.
    - Überprüft, ob die angeforderte Ressource Teil des Bereichs im Token ist.

Wurden alle Prüfschritte erfolgreich absolviert, wird die Anfrage an den Zustelldienst übergeben.

Nach Bearbeitung der Anfrage im Zustelldienst wird die Antwort des Zustelldienstes an den Client zurückgesendet.


