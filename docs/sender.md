# Application Sender API
## Transfer Operationen
Es werden folgende Parameter in der URL verwendet:
- `source-id`: Wird mit dem SourceAccount zugewiesen.
- `destination-id`: Über externes System (Zuständigkeitsfinder) dem Onlineantragsdienst bekannt.
- `application-id`: Vom Zustelldienst vergebene ID für die Übertragung.



### [Create Transfer](../reference/sender.json/paths/~1{source-id}~1{destination-id}/post)
Legt eine neue Übertragung an.

#### Request
- Body: [Application Metadata ohne ID](../models/application/metadata-no-id.json)

#### Response
- Body: `application-id`



### [Add Application Data](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}~1data/put)
Fügt dem Antrag strukturierte Daten hinzu.

#### Request application/json
- Body: Strukturierte JSON-Daten, die dem in der Application angegebenen ApplicationSchema entsprechen.

#### Request application/xml
- Body: Strukturierte XML-Daten, die dem in der Application angegebenen ApplicationSchema entsprechen.

#### Response
- Body: (leer)

#### Falls Transfer-ID ungültig/Transfer-Timeout
- HTTP 410 Gone
- Body: [Error](../models/error.json)

#### Falls Kein Schema zugeordnet
- HTTP 406 Not Acceptable
- Body: [Error](../models/error.json)

#### Falls Übertragung zu groß
- HTTP 413 Request Entity Too Large 
- Body: [Error](../models/error.json)

#### Falls Schemafehler
- HTTP 406 Not Acceptable 
- Body: [Error](../models/error.json)



### [Add Application Document](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}~1docs~1{doc-id}/put)
Übermittelt ein Antragsformular oder eine Anlage.

#### Request
- Body: FIXME

#### Response
- Body: (leer)

#### Falls Transfer-ID ungültig/Transfer-Timeout
- HTTP 410 Gone
- Body: [Error](../models/error.json)

#### Falls der Body bzw. das Dokument kein PDF ist
- HTTP 415 Unsupported Media Type
- Body: [Error](../models/error.json)

#### Falls Signaturprüfung nicht erfolgreich - Signatur passt nicht zum Dokument
- HTTP 400 Bad Request
- Body: [Error](../models/error.json)



### [Commit Transfer](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}/post)
Beendet die Übertragung des Antrags und löst seinen Versand aus.

#### Request
- Body: 

#### Response
- Body: 

#### Falls 
- HTTP
- Body: [Error](../models/error.json)



### [Get Application Metadata](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}/get)

FIXME

### [Get Application Upload Status](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}~1upload-status/get)

FIXME
