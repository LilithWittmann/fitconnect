# Erste Schritte zur API Nutzung

<!-- theme: info -->

> ## ① Account registrieren
> Registrieren Sie sich für ein Zugriff, um mit Ihren Client auf die API zuzugreifen. Im Rahmen der Registrierung bekommen Sie für die gewünschte API die Client-ID und Zugriffdaten mitgeteilt. Da zum aktuellen Zeitpunkt keine Sandbox Umgebung bereitstellt, wird empfohlen, sich für beide Seiten zu registieren, um für komplexere Tests mit einem REST Client die API der Gegenseite anzusprechen (Siehe Postman Nutzung in Schritt 2). ➡ [Anwender Registrierung](./4_Authentifizierung_und_Autorisierung.md)

> ## ② API ausprobieren
> In der Navigation auf linken Seite finden Sie die jeweiligen API Referenzen für die Nutzung der APIs unter den Reitern `Application Sender API` und `Application Subscriber API` 
Für einen einfachen Einstieg zum Test der API können Sie die bereitgestellte Postman Collection nutzen und mit dem Postman REST Client die Anfragen an die API durchführen. Hiermit können Sie auch die Gegenseite (Sender oder Empfänger von Anträgen simulieren) (➡ [Testen mit Postman](./Detailinformationen/Postman.md). Nähere Informationen zu Postman siehe https://www.postman.com/) 
Alternativ können Sie die Anfragen auch mittels eigener Anwendungen oder alternativer REST Clients durchführen.

> ## ③ OAuth Token vor der API Nutzung abrufen
> Für jede Anfrage an die API Endpunkte ist ein gültiger JWT-Token mit der Anfrage mitzusenden. Für nähere Informationen zum Abruf eines JWT-Token siehe ➡ [OAuth Details](./Detailinformationen/OAuth.md)

> ## ④ Spezifikation lokal nutzen
> Sofern Sie einen lokalen Zugriff auf die Quellen der Spezifikation im OpenAPI Format (bspw. für Code Generatoren) benötigen, finden Sie diese hier: ➡[FIT-Connect-PoC-v0.6.zip](https://github.com/fiep-poc/assets/raw/master/spec/FIT-Connect-PoC-v0.6.zip)
<!-- Abschließendes Beispiel eines API Abrufs mit Token Abruf und einem Beispiel unter Nutzung des Tokens. -->

## Wie geht es weiter?

<!-- theme: success -->

> ### Service Desk
> Für Fragen, Anregungen und sonstiges Feedback steht Ihnen unser
> [FIT-Connect Service Desk](https://jira.fiep-poc.de/servicedesk/customer/portal/1)
> zur Verfügung.
