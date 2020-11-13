# Registrierung und Client-Verwaltung

Für die Version Beta 6 ist keine Anmeldung über das FIT-Connect API Portal erforderlich.
Die Anmeldung erfolgt einstufig durch per Mail mit der Anfrage zur Registrierung eines Client (Anwendung).

Die Mail muss an [registrierung@fiep-poc.de](mailto:registrierung@fiep-poc.de) gesendet werden.

Folgende Angaben müssen in der Mail enthalten sein:
- Name der Anwendung		(z.B. FitConnectShowCase)
- Angaben zur Firma/Behörde
  - Name (z.B. Dataport)
  - Adresse (z.B. Hannover)
  - Webseite (z.B. https://www.dataport.de)
- Kontaktadresse
  - E-Mail (z.B. Harald.Mustermann@dataport.de)
  - Telefonnummer	(z.B. +49 431 4712-4711)
- AnwenderID (z.B. 41754caf-c9b2-4f09-b8ac-f3df0d46c318)
- Gewünschter API Bereich (entweder Sender oder Subscriber)

Die AnwenderID kann frei gewählt werden. Sie wird automatisch vergeben, wenn sie nicht angegeben wurde.

**Beipiel:**

> **Betreff:** FIT-Connect Registrierung
> 
> **Mailinhalt:**
> 
> Wir bitten um die Registrierung einer Anwendung für FIT-Connect Beta 6
> 
> <pre>Name der Anwendung:         TestAnwendung
> Angaben zur Firma/Behörde:
>     Name Land           Sachsen
>     Adresse             Dresden
>     Webseite            https://www.sachsen.de
>     E-Mail              Harald.Mustermann@dataport.de
>     Telefon             +49 431 4712-4711
> AnwenderID              41754caf-c9b2-4f09-b8ac-f3df0d46c318
> Gewünschter API Bereich Subscriber
> </pre>

Sie bekommen im Anschluss eine Rückantwort per E-Mail wie diese:

> Willkommen xxx,
> 
> Ihre Anwendung wurde registriert.
> 
> Client ID:          f7d44674-05c2-4eab-xxx
> 
> Client Secret:   754b0b41-d891-4f63-xxx
> 
> AnwenderID:    2a9d33c9-a70d-446d-xxx
> 
> Als Scope kann für das SubscriberAPI „destination:manage“ und /oder „detsination:subscribe“ und für das SenderAPI „destination:send“ verwendet werden.
Client ID und Client Secret benötigen Sie zur Ermittlung eines Token. Die AnwenderID wird anhand des Token automatisch ermittelt und an den Zustelldient weitergeleitet.
> 
> Die Url zur Token Generierung lautet: https://fitko.cidaas.de/token-srv/token

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

FÜr nähere Details und Beispiele siehe:
➡ [OAuth](./Detailinformationen/OAuth.md)
