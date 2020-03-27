# Status- und Fehlercodes

Die XFall APIs liefert in allen Responses die entsprechenden HTTP Response Codes. In der aktuell vorliegenden API Version werden nur HTTP Response Codes verwendet, die im [RFC 7231](https://tools.ietf.org/html/rfc7231) beschrieben sind. 

API Clients sollten aber gemäß RFC 7231 so implementiert, dass auch unbekannte Response Status Codes  (Neue verwendete Standardcodes oder proprietäre Erweiterungen) gemäß ihrer Statusklasse interpretiert werden können:
>    "HTTP status codes are extensible.  HTTP clients are not required to
   understand the meaning of all registered status codes, though such
   understanding is obviously desirable.  However, a client MUST
   understand the class of any status code, as indicated by the first
   digit, and treat an unrecognized status code as being equivalent to
   the x00 status code of that class, with the exception that a
   recipient MUST NOT cache a response with an unrecognized status code."


### Übersicht der verwendeten Response Codes und ihre Bedeutung

Code | Text | Bedeutung
---------|----------|---------
 200 | OK | Der Request war erfolgreich.
 201 | Created | Eine Ressource wurde erfolgreich angelegt.
 202 | Accepted | Daten wurden wurden erfolgreich übertragen und angenommen.
 400 | Bad Request | Der Request war nicht korrekt aufgebaut oder es liegen mehrere Fehler vor, die unterschiedliche Statuscodes der 4xx-Klasse betreffen. 
 401 | Unauthorized | Der Request lieferte keine oder eine ungültige Authentifikation.
 404 | Not Found | Die Ressource kann nicht unter dem angegeben Pfad gefunden werden oder temporär nicht verfügbar.
 406 | Not Acceptable | Request Body entspricht nicht dem vorgebenen Schema.
 410 | Gone | Die Ressource ist unter dem Pfad permanent nicht mehr verfügbar. (bspw. weil die Ressource gelöscht wurde in dieser Repräsentation nicht mehr verfügbar ist)
 413 | Request Entity Too Large | Der übertragene Datensatz ist zu groß.
 415 | Unsupported Media Type | Der Datentyp wird nicht unterstützt.
 500 | Internal Server Error | Es besteht ein Fehler auf Seite des API Providers.

### Detailangaben zu clientseitig verursachten Fehlern

Bei durch den API-Client verursachte Fehler (HTTP Statusklasse 4XX), liefert die API im Response Body eine [Error](../models/error.json) Mitteilung mit detaillierten Angaben, wodurch der Fehler versacht wurde. 

Eine Error Mitteilung enthält dabei folgende Angaben:

    code: Standardisierter Fehlercode

    msg: Textuelle Fehlermeldung

    ref: Referenz auf fehlerhafte Stelle

### Liste der Fehlercodes

**... Noch in der Erstellung ...**