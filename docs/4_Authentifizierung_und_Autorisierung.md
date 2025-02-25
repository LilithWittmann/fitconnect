# Registrierung und Client-Verwaltung

## Anwender Registrierung

Das FIT-Connect API Portal ist unter der folgenden URL erreichbar:

https://portal.fiep-poc.de

Eine Behörde, die ein Verfahren anbieten möchte, registriert sich zunächst am Portal mit dem Button "Registrieren". Diese Funktion steht auch rechts oben unter "Mein Konto" zur Verfügung.

![API-Portal](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/01_portal.png)

![Registrierung](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/02_register.png)

![Registrierung abgesendet](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/03_registered.png)

Im Anschluss erhalten Sie zwei verschiedene E-Mails.
Die zweite E-Mail kommt mit einer zeitlichen Verzögerung von bis zu 30 Minuten.

In der ersten Email wird ihre Registrierungsanfrage bestätigt:

> Hallo Werner Mustermann, 
> 
> ihre Anfrage zur Registrierung ist aufgenommen worden. Sie erhalten noch zwei weitere Bestätigungsmails. 
> 
> Mit besten Grüßen,
> Ihr FIT-Connect API Portal Team
> 
> *** Diese Benachrichtigung wurde automatisch erstellt. Antworten Sie nicht auf diese Email.***

In der zweiten Email wird ihnen noch die Anwender-ID mitgeteilt.

Diese Anwender-ID ist essenziell für die weitere Arbeit mit den APIs.
Sie ist Bestandteil sowohl der Aufruf URLs als auch Bestandteil der Scopes für die OAuth 2.0. Authorization / Authentication.

**Erst nach Erhalt der Email können sie sich anmelden!**

Hier ein Beispiel einer solchen Email:

> Sehr geehrter Herr Mustermann,
> 
> wir freuen uns über ihre Teilnahme an dem POC Fit-Connect. 
> 
> Ihre Anwender-ID lautet: c94ae37e-dcc5-345e-a530-8651bdfa5f2c
> 
> Mit freundlichem Gruß
> Ihr FIT-Connect Team.

## Client Registrierung

<!-- theme: warning -->
> **Hinweis:** Im Zuge der ersten Anmeldung empfehlen wir die Umstellung der Sprache auf Deutsch.

![Einstellungen aufrufen](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/04_settings.png)

![Sprache auswählen](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/05_language.png)

Im zweiten Schritt wird die von ihrer Behörde angebotene Anwendung (auch Client genannt) registriert.

Dies erfolgt durch Aufruf der Details des für die Anwendung gewünschten API

Dazu klicken sie in der Titelleiste auf "APIs":

![APIs aufrufen](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/06_apis.png)

In der nun angezeigten Liste klicken Sie beim API "SubscriberAPI" auf den Button "Details anzeigen >>"

![API Details aufrufen](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/07_select_api.png)

In der Detailanzeige klicken sie rechts oben unter "Was als Nächstes?" auf "Client anmelden und Zugriffs-Token auswählen".

![Client anmelden](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/08_register_client.png)

Nun erscheint der folgende Dialog:

![Token anfordern](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/09_request_token.png)

Hier vergeben Sie einen Anwendungsnamen und eine Beschreibung. Die Angabe einer Umleitungs-URI ist optional.
Haken Sie beiden APIs ("Source/Sender" und "Subscriber") an.

<!-- theme: warning -->
> **Achtung:** Zum Testen benötigen Sie Zugriff auf beide APIs. Achten Sie bitte darauf, im unteren Teil beide Haken zu setzen.

Mit dem Button "Token anfordern" lösen Sie die Erstellung der Anwendung (Client) und der für Sie gültigen Subscriber-ID (subscriber-id) und/oder Source/Sender-ID (source-id) aus. Diese Subscriber-ID wird für alle weiteren API Aufrufe benötigt.

Im Hintergrund wird nun automatisch eine nur für ihre Behörde und diese Anwendung gültige Scope Konfiguration erstellt. Dies Konfiguration kann über den Menüpunkt "Applications" eingesehen werden.

![Anwendungen aufrufen](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/10_goto_applications.png)

![Anwendungen](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/11_applications.png)

Aus dieser Liste heraus können sie die Details der Anwendung durch Klick auf den Namen der Anwendung ansehen.

![Anwendungsdetails](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/12_application_details.png)

Für die Nutzung des API sind die Angaben unter "OAuth2-Anmeldeinformationen" wichtig.

Der für Sie und Ihre Anwendung gültige OAuth2 Scope wird ihnen in einer E-Mail mitgeteilt.

Hier ein Beispiel einer solchen E-Mail:

> Sehr geehrter Herr Mustermann,
> 
> Für ihren Client (Application) steht ihnen folgender Scope zur Verfügung 
> 
> Scope:  subscriber-c1785a90-b3e7-3022-9c70-e1714cb8e8c6:manage
> 
> Zusammen mit der „client_id“ und dem für uns nicht sichtbaren „client_secret“ können Sie in der Folge einen „access token“ für das API „SubscriberAPI“ abholen.
> 
> Die URL dafür lautet: 
> https://oauth.fiep-poc.de/invoke/pub.apigateway.oauth2/authorize
> 
> Die weiteren Details zur entnehmen Sie bitte der FIT-Connect Anwenderdokumentation“.
> 
> Mit freundlichem Gruß
> Ihr FIT-Connect Team.

## Hinweise zum Aufruf des API mit OAuth2

Um das von ihnen gewünschte API im Rahmen ihrer Anwendung aufzurufen, Gehen sie wie folgt vor:

![API Zugriff](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/13_api_zugriff.png)

Verfahrensschritte:

1) Der Endbenutzer meldet sich an, die Clientanwendung sendet die Authentifizierungsanforderung an den Autorisierungsserver, um ein Zugriffstoken zu erhalten.

2) Der Autorisierungsserver überprüft die Anforderung und generiert ein Zugriffstoken für den Client.

3) Der Client verwendet dieses Zugriffstoken, um HTTP-Anforderungen an das API-Gateway zu senden.

4) Das API-Gateway führt dann folgendes aus:
    - Identifiziert die Anwendung anhand der client_Id.
    - Überprüft das Token lokal oder remote, wenn es lokal nicht möglich ist.
    - Überprüft, ob die angeforderte Ressource Teil des Bereichs im Token ist.

Wurden alle Prüfschritte erfolgreich absolviert, wird die Anfrage an den Zustelldienst übergeben.

Nach Bearbeitung der Anfrage im Zustelldienst wird die Antwort des Zustelldienstes an den Client zurückgesendet.
