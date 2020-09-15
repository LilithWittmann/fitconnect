# Registrierung und Client-Verwaltung

Für die aktuelle Registrierung neuer Clients von Entwicklern haben wir ein neues Verfahren eingeführt. Es wird daher in Kürze hier eine neue Dokumentation zum Registierungsverfahren bereitgestellt.

Bis dahin übersenden Sie die Registrierung neuer Clients zur Nutzung der API an den
[FIT-Connect Service Desk](https://jira.fiep-poc.de/servicedesk/customer/portal/1). Wir werden Ihnen hierüber Ihre Clients und Ihnen die notwendigen Informationen bereitstellen.

## Hinweise zum Aufruf der API mit OAuth2

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