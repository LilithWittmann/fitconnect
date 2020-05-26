# Status- und Fehlercodes

Die XFall RESTful API liefert in allen Responses HTTP Response Codes. In der aktuell vorliegenden API Version werden nur HTTP Response Codes verwendet, die im [RFC 7231](https://tools.ietf.org/html/rfc7231) beschrieben sind. 

API Clients sollten aber gemäß RFC 7231 so implementiert, dass auch unbekannte Response Status Codes (Neue Standardcodes oder proprietäre Erweiterungen) gemäß ihrer Statusklasse interpretiert werden können:
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
 403 | Forbidden | Die mit dem Request gelieferte Authentifikation ist für diese Resource nicht zugriffsberechtigt.
 404 | Not Found | Die Ressource kann nicht unter dem angegeben Pfad gefunden werden oder temporär nicht verfügbar.
 410 | Gone | Die Ressource ist unter dem Pfad permanent nicht mehr verfügbar. (bspw. weil die Ressource gelöscht wurde in dieser Repräsentation nicht mehr verfügbar ist)
 413 | Request Entity Too Large | Der übertragene Datensatz ist zu groß.
 415 | Unsupported Media Type | Der Datentyp wird nicht unterstützt.
 500 | Internal Server Error | Es besteht ein Fehler auf Seite des API Providers.

### Detailangaben zu clientseitig verursachten Fehlern

Bei durch den API-Client verursachte Fehler (HTTP Statusklasse 4XX), liefert die API im Response Body eine [Error Body](../models/error-body.json) Mitteilung mit detaillierten Angaben, wodurch der Fehler versacht wurde. 

Eine Error Mitteilung enthält folgende Angaben:

- `code`: Standardisierter Fehlercode
- `msg`: Textuelle Fehlermeldung
- `ref`: Referenz auf fehlerhafte Stelle

### Liste der Fehlercodes

<!-- theme: warning -->
> **Hinweis:**
> Die im Folgenden beschriebenen Prüfungen und Fehlerfälle sind noch nicht implementiert und stellen aktuell eine Planung dar.

#### Allgemeine Fehler

**... Noch in der Erstellung ...**

#### Application Transfer

| HTTP Code                    | Code | Message                                                                                             | Referenz         | Tritt auf, wenn…                                                                                                                                       |
|:---------------------------- |:----:|:--------------------------------------------------------------------------------------------------- |:---------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 404 Not Found                | 101  | Die Destination wurde nicht gefunden.                                                               | (keine)          | keine Destination mit der Destination-ID existiert                                                                                                     |
| 413 Request Entity Too Large | 102  | Die Übertragung ist zu groß.                                                                        | (keine)          | die Gesamtgröße über der Maximalgröße der Destination liegt                                                                                            |
| 413 Request Entity Too Large | 103  | Die Fachdaten sind zu groß.                                                                         | (keine)          | die Größe der Fachdaten (/contentStructure/data/size) über der Maximalgröße der Destination liegt                                                      |
| 400 Bad Request              | 104  | Das Fachdatenschema des Antrags entspricht nicht den vorgebenen Schemata der Destination.           | (keine)          | ein Schema angegeben wird, das in der Destination nicht definiert wurde                                                                                |
| 400 Bad Request              | 105  | Es darf keine Schema-ID angegeben werden.                                                           | (keine)          | die Schema-Quelle "none" und eine Schema-ID angegeben wurde                                                                                            |
| 400 Bad Request              | 106  | Die Schema-ID fehlt.                                                                                | (keine)          | die Schema-Quelle "fim" und keine Schema-ID angegeben wurde                                                                                            |
| 400 Bad Request              | 107  | Die Schema-ID referenziert kein FIM Stammdatenschema.                                               | (keine)          | die Schema-Quelle "fim" angegeben wurde, die Schema-ID aber nicht der Regex "^S\d{8}V\d+\.\d+$" entspricht                                             |
| 413 Request Entity Too Large | 108  | Die Maximalzahl von Dokumenten wurde überschritten.                                                 | (keine)          | die Anzahl der Dokumente über der maximalen Anzahl der Destination liegt                                                                               |
| 400 Bad Request              | 109  | Die Dokument-ID "{docId}" ist nicht eindeutig.                                                      | (keine)          | eine Doc-ID doppelt vorkommt                                                                                                                           |
| 413 Request Entity Too Large | 110  | Das Dokument "{docId}" ist zu groß. Es sind nur {Maximalgröße} Bytes erlaubt.                       | (keine)          | die Größe des Dokuments (/contentStructure/docs[docId='{docId}']/size) über der Maximalgröße der Destination liegt                                     |
| 400 Bad Request              | 111  | Der Content-Type des Dokuments "{docId}" ist ungültig.                                              | (keine)          | der MIME-Type (/contentStructure/docs[docId='{docId}']/mimeType) nicht RFC 2045 entspricht                                                             |
| 404 Not Found                | 112  | Die Application wurde nicht gefunden.                                                               | (keine)          | keine Application mit der Application-ID existiert                                                                                                     |
| 404 Not Found                | 113  | Die Application wurde nicht gefunden.                                                               | (keine)          | die Application-ID nicht zur Source-ID passt                                                                                                           |
| 404 Not Found                | 114  | Die Application wurde nicht gefunden.                                                               | (keine)          | die Application-ID nicht zur Destination-ID passt                                                                                                      |
| 400 Bad Request              | 115  | Fachdaten können nicht übermittelt werden. Es wurde kein "data" Element in den Metadaten angegeben. | (keine)          | in den Metadaten kein /contentStructure/data Element enthalten ist                                                                                     |
| 400 Bad Request              | 116  | Die Größe der übermittelten Fachdaten entspricht nicht dem Eintrag in den Metadaten.                | (keine)          | die Größe des Bodys nicht mit /contentStructure/data/size in den Metadaten übereinstimmt                                                               |
| 415 Unsupported Media Type   | 117  | Der Typ (Content-Type) der Fachdaten ist falsch.                                                    | (keine)          | der MIME-Type nicht mit /data/schema/mimeType übereinstimmt                                                                                            |
| 400 Bad Request              | 118  | Die Fachdaten entsprechen nicht dem geforderten Format.                                             | (keine)          | die Fachdaten nicht dem Format (JSON bzw. XML) entsprechen                                                                                             |
| 400 Bad Request              | 119  | Die Fachdaten entsprechen nicht dem geforderten Schema.                                             | (keine)          | ein Schema referenziert wurde (Schema-Source ≠ "none" und gültige Schema-ID) und die Fachdaten nicht dem Schema entsprechen                            |
| 404 Not Found                | 120  | Die Application wurde nicht gefunden.                                                               | (keine)          | keine Application mit der Application-ID existiert                                                                                                     |
| 404 Not Found                | 121  | Die Application wurde nicht gefunden.                                                               | (keine)          | die Application-ID nicht zur Source-ID passt                                                                                                           |
| 404 Not Found                | 122  | Die Application wurde nicht gefunden.                                                               | (keine)          | die Application-ID nicht zur Destination-ID passt                                                                                                      |
| 404 Not Found                | 123  | Das Dokument wurde nicht gefunden.                                                                  | (keine)          | die Doc-ID nicht zur Application-ID passt                                                                                                              |
| 400 Bad Request              | 124  | Die Prüfsumme (Hash) des Dokuments "{docId}" stimmt nicht mit der in den Metadaten überein.         | (keine)          | der Hash in den Metadaten nicht zu dem hochgeladenen Dokument passt                                                                                    |
| 400 Bad Request              | 125  | Die Signatur des Dokuments "{docId}" passt nicht zum Dokument.                                      | (keine)          | die Signatur in den Metadaten nicht zu dem hochgeladenen Dokument passt                                                                                |
| 404 Not Found                | 126  | Die Application wurde nicht gefunden.                                                               | (keine)          | keine Application mit der Application-ID existiert                                                                                                     |
| 404 Not Found                | 127  | Die Application wurde nicht gefunden.                                                               | (keine)          | die Application-ID nicht zur Source-ID passt                                                                                                           |
| 404 Not Found                | 128  | Die Application wurde nicht gefunden.                                                               | (keine)          | die Application-ID nicht zur Destination-ID passt                                                                                                      |
| 400 Bad Request              | 129  | Die Fachdaten fehlen noch.                                                                          | (keine)          | Fachdaten in den Metadaten angegeben wurden (/contentStructure/data), aber keine Fachdaten hochgeladen wurden                                          |
| 400 Bad Request              | 130  | Die Fachdaten sind unvollständig.                                                                   | (keine)          | die hochgeladenen Fachdaten unvollständig sind, also die übermittelten Bytes kleiner sind als in den Metadaten angegeben (/contentStructure/data/size) |
| 400 Bad Request              | 131  | Die Fachdaten sind ungültig: {Fehler vom Upload}                                                    | (keine)          | die Fachdaten nicht korrekt ist, also eine der Prüfungen (z.B. MIME-Type oder Schema) beim Upload nicht korrekt war                                    |
| 400 Bad Request              | 132  | Das Dokument '{docId}' fehlt noch.                                                                  | (keine)          | nicht alle in den Metadaten angegebenen (/contentStructure/docs) Dokumente hochgeladen wurden                                                          |
| 400 Bad Request              | 133  | Das Dokument '{docId}' wurde nicht vollständig hochgeladen.                                         | (keine)          | Das Dokument '{docId}' wurde nicht vollständig hochgeladen.                                                                                            |
| 400 Bad Request              | 134  | Das Dokument '{docId}' ist ungültig: {Fehler vom Upload}                                            | {ref vom Upload} | Das Dokument '{docId}' ist ungültig: {Fehler vom Upload}                                                                                               |

#### Status & Transfer Related Information

| HTTP Code     | Code | Message                                                          | Referenz | Tritt auf, wenn…                                               |
|:------------- |:----:|:---------------------------------------------------------------- |:-------- |:-------------------------------------------------------------- |
| 404 Not Found | 201  | Es wurde keine Statusinformation für diese Application gefunden. | (keine)  | kein Status/keine Application mit der Application-ID existiert |
| 404 Not Found | 202  | Es wurde keine Statusinformation für diese Application gefunden. | (keine)  | die Application-ID nicht zur Source-ID passt                   |
| 404 Not Found | 203  | Die Application wurde nicht gefunden.                            | (keine)  | keine Application mit der Application-ID existiert             |
| 404 Not Found | 204  | Die Application wurde nicht gefunden.                            | (keine)  | die Application-ID nicht zur Source-ID passt                   |
| 404 Not Found | 205  | Die Application wurde nicht gefunden.                            | (keine)  | die Application-ID nicht zur Destination-ID passt              |
| 404 Not Found | 206  | Die Destination wurde nicht gefunden.                            | (keine)  | keine Destination mit der Destination-ID existiert             |


#### Destination Management

| HTTP Code | Code | Message | Referenz | Tritt auf, wenn… |
|:--------- |:----:|:------- |:-------- |:---------------- |
| 404 Not Found | 301 | Der Subscriber wurde nicht gefunden. | (keine) | kein Subscriber mit der Subscriber-ID existiert |
| 404 Not Found | 302 | Die Destination wurde nicht gefunden. | (keine) | keine Destination mit der Destination-ID existiert |
| 404 Not Found | 303 | Die Destination wurde nicht gefunden. | (keine) | die Destination-ID nicht zur Subscriber-ID passt |
| 404 Not Found | 304 | Die Destination wurde nicht gefunden. | (keine) | keine Destination mit der Destination-ID existiert |
| 404 Not Found | 305 | Die Destination wurde nicht gefunden. | (keine) | die Destination-ID nicht zur Subscriber-ID passt |
| 400 Bad Request | 306 | Die Destination-ID darf nicht geändert werden. | /destinationId | die Destination-ID in URL und Body nicht übereinstimmen |
| 404 Not Found | 307 | Die Destination wurde nicht gefunden. | (keine) | keine Destination mit der Destination-ID existiert |
| 404 Not Found | 308 | Die Destination wurde nicht gefunden. | (keine) | die Destination-ID nicht zur Subscriber-ID passt |

#### Application Retrieval


| HTTP Code     | Code | Message                                                     | Referenz | Tritt auf, wenn…                                           |
|:------------- |:----:|:----------------------------------------------------------- |:-------- |:---------------------------------------------------------- |
| 404 Not Found | 401  | Die Destination wurde nicht gefunden.                       | (keine)  | keine Destination mit der Destination-ID existiert         |
| 404 Not Found | 402  | Die Destination wurde nicht gefunden.                       | (keine)  | die Destination-ID nicht zur Subscriber-ID passt           |
| 404 Not Found | 403  | Die Application wurde nicht gefunden.                       | (keine)  | keine Application mit der Application-ID existiert         |
| 404 Not Found | 404  | Die Application wurde nicht gefunden.                       | (keine)  | die Application-ID nicht zur Destination-ID passt          |
| 404 Not Found | 405  | Die Application wurde nicht gefunden.                       | (keine)  | der Status 'incomplete' ist                                |
| 404 Not Found | 406  | Im aktuellen Status ist nur das finale Acknowledge möglich. | (keine)  | der Status 'forwarded' ist und 'finalDelivery' 'false' ist |
| 404 Not Found | 407  | Im aktuellen Status ist kein Acknowledge möglich.           | (keine)  | der Status 'delivered' ist                                 |
| 404 Not Found | 408  | Die Destination wurde nicht gefunden.                       | (keine)  | keine Destination mit der Destination-ID existiert         |
| 404 Not Found | 409  | Die Destination wurde nicht gefunden.                       | (keine)  | die Destination-ID nicht zur Subscriber-ID passt           |
| 404 Not Found | 410  | Die Application wurde nicht gefunden.                       | (keine)  | keine Application mit der Application-ID existiert         |
| 404 Not Found | 411  | Die Application wurde nicht gefunden.                       | (keine)  | die Application-ID nicht zur Destination-ID passt          |
| 404 Not Found | 412  | Die Application wurde nicht gefunden.                       | (keine)  | der Status 'incomplete' ist                                |
| 404 Not Found | 413  | Die Application wurde nicht gefunden.                       | (keine)  | der Status nicht 'queued' ist                              |
| 404 Not Found | 414  | Es wurden keine Fachdaten gefunden.                         | (keine)  | keine Fachdaten vorliegen                                  |
| 404 Not Found | 415  | Die Destination wurde nicht gefunden.                       | (keine)  | keine Destination mit der Destination-ID existiert         |
| 404 Not Found | 416  | Die Destination wurde nicht gefunden.                       | (keine)  | die Destination-ID nicht zur Subscriber-ID passt           |
| 404 Not Found | 417  | Die Application wurde nicht gefunden.                       | (keine)  | keine Application mit der Application-ID existiert         |
| 404 Not Found | 418  | Die Application wurde nicht gefunden.                       | (keine)  | die Application-ID nicht zur Destination-ID passt          |
| 404 Not Found | 419  | Die Application wurde nicht gefunden.                       | (keine)  | der Status 'incomplete' ist                                |
| 404 Not Found | 420  | Die Application wurde nicht gefunden.                       | (keine)  | der Status nicht 'queued' ist                              |
| 404 Not Found | 421  | Das Dokument wurde nicht gefunden.                          | (keine)  | die Doc-ID nicht zur Application-ID passt                  |
| 404 Not Found | 408  | Die Destination wurde nicht gefunden.                       | (keine)  | keine Destination mit der Destination-ID existiert         |
| 404 Not Found | 409  | Die Destination wurde nicht gefunden.                       | (keine)  | die Destination-ID nicht zur Subscriber-ID passt           |
| 404 Not Found | 410  | Die Application wurde nicht gefunden.                       | (keine)  | keine Application mit der Application-ID existiert         |
| 404 Not Found | 411  | Die Application wurde nicht gefunden.                       | (keine)  | die Application-ID nicht zur Destination-ID passt          |
| 404 Not Found | 412  | Die Application wurde nicht gefunden.                       | (keine)  | der Status 'incomplete' ist                                |
| 404 Not Found | 413  | Die Application wurde nicht gefunden.                       | (keine)  | der Status nicht 'queued' ist                              |
| 404 Not Found | 408  | Die Destination wurde nicht gefunden.                       | (keine)  | keine Destination mit der Destination-ID existiert         |
| 404 Not Found | 409  | Die Destination wurde nicht gefunden.                       | (keine)  | die Destination-ID nicht zur Subscriber-ID passt           |
