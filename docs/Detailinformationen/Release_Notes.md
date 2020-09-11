# Release Notes

## Version 0.6

### Dokumentation
- [Fehlercodes](../5_Status-_und_Fehlercodes.md) dokumentiert
- [Erste Schritte](../1_Getting_Started.md) überarbeitet

### Umgesetzte Change Requests
#### #3 Sematic error of the OAS in editor.swagger.io
Das Security Schema darf keine Leerzeichen enthalten und wurde deswegen von "OAuth 2.0" in "OAuth20" umbenannt.

#### #4 academicTitle -> doctoralDegrees
Alle Vorkommen von "academicTitle" wurden durch "doctoralDegrees" ersetzt.

#### #5 telephone -> telephones
Da Arrays mit einem Plural bezeichnet werden sollen wurde "telephone" durch "telephones" ersetzt.

#### #7 Regex für Hausnummernzusatz ist falsch
Das Pattern für den Hasnummernzusatz `^[\\p{L}0-9. ]*$` war inkorrekt da die Zeichenklassen `\p{L}` nicht zulässig ist. Es wurde daher zu `^[A-Za-z0-9. ]*$` korrigiert.

#### #10 API Specification: senderId and subscriberId in URIs
Die Sender- und Subscriber-ID muss nicht mehr über den Pfad mitgegeben werden sondern wird automatisch über das Token ermittelt. Damit entfallen die IDs als Pfadangabe.

#### #11 API Specification: Missing nouns in Sender API URIs endpoints
Die Pfade auf in der Sender API enthielten vor den IDs kein beschreibendes Nomen. Dies wurde korrigiert. Zum Beispiel:
- vorher: `/{destinationId}/{applicationId}/data`
- nachher: `/destinations/{destinationId}/applications/{applicationId}/data`

#### #12 API Specification: Missing destinationId in Get Status endpoint of Sender 
Die Operation "Get Status" wies im Gegensatz zu den anderen Operationen keine vorangestellte Destination-ID auf.
- vorher: `/{applicationId}/status`
- nachher: `/destinations/{destinationId}/applications/{applicationId}/status`

#### #16 Fachdaten optional
Das Element "data" in der "contentStructure" war verpflichtend. Damit mussten Fachdaten übertragen werden. Das Element ist jetzt optional.



## Version 0.5

### Übergreifende Änderungen

#### Basis-URLs
Die Basis-URLs werden ab sofort mit jeder neuen Version geändert, damit ein paralleler Betrieb mehrerer API-Versionen möglich ist.
Die Basis-URLs für diese Version sind:
- https://sender.fiep-poc.de/beta5/
- https://subscriber.fiep-poc.de/beta5/

#### CR-1: Diversen Modellen den Discriminator "type" hinzugefügt:
- models/application/applicant-contact-info.json
- models/application/applicant-contact-info.json
- models/application/applicant-person.json
- models/application/applicant.json
- models/common/address-international.json
- models/common/address-national.json
- models/common/address-postbox.json
- models/common/individual.json
- models/destination-no-id.json

#### CR-3: Source in Sender ändern
In der Dokumentation werden die Begriffe "Source" und "Sender" synonym verwendet. Um die Dokumentation klarer zu machen, wurden alle Vorkommen von "Source" in "Sender" geändert.

<!-- theme: warning -->
> **Hinweis:** Dies wirkt sich auch auf die OAuth-Scopes aus. Der Scope `{senderId}:source:manage` wurde in `{senderId}:sender:manage` geändert.

#### CR-5: Zusätzliche Properties verbieten
- Wo möglich wurde `"additionalProperties": false` gesetzt um weitere Properties zu verbieten.
- Bei den Metadaten und der Destination ohne ID musste `"additionalProperties": false` wieder entfernt werden da sonst keine Ableitung mit `allOf` möglich ist.

### Dokumentation
- Release Notes mit aufgenommen
- Dokumentation zu OAuth integriert
- Token-URL eingetragen
- Postman Collection & Environment integriert

### Modelle

#### Destination
models/destination-no-id.json

#### eID
- eID-org-acting-person.json aufgelöst und in eID-natural-person.json integriert.

#### Postfachadresse
models/common/address-national.json
models/common/address-postbox.json
- Um ein doppeltes `oneOf` zu vermeiden wurde die Postfach Adresse aus der nationalen Adresse herausgelöst.

#### Application Document
models/application/document.json
- Regex Pattern für SHA-256/512 Hash präzisiert: "`[0-9A-F]{64,128}`" -> "`^[A-Fa-f0-9]{64}([A-Fa-f0-9]{64})?$`"

### Application Sender API

#### Add Application Data
- Im Erfolgsfall enthält der Body `{"result":"success"}`

#### Add Application Document
- Im Erfolgsfall enthält der Body `{"result":"success"}`

### Application Subscriber API

#### Update Destination
- Im Erfolgsfall enthält der Body `{"result":"success"}`

#### Delete Destination
- Im Erfolgsfall enthält der Body `{"result":"success"}`

#### Acknowledge Application
- Bugfix: Property `final-delivery` auf Camelcase umgestellt.
- Bugfix: Angaben von `finalDelivery` in Acknowledge Application ist verpflichtend.



## Version 0.4
### Modelle
- Alle Bezeichner auf CamelCase umgestellt.
- Beispiele angepasst.

#### Application Metadata
models/application/metadata-no-id.json
- data/mimeType entfernt, da redundant zu data/schema/mimeType

### Application Sender API
- Alle Bezeichner auf CamelCase umgestellt.
- Beispiele angepasst.

### Application Subscriber API
- Alle Bezeichner auf CamelCase umgestellt.
- Beispiele angepasst.



## Version 0.3
### Modelle

#### Application Metadata
models/application/metadata-no-id.json
- Property "data/size" ergänzt

#### eID
models/common/eID-org-acting-person.json
- Property "artictic-name" in "artistic-name" umbenannt

#### Internationale Adresse
models/common/address-international.json 
- Property "lines":
  - Es müssen mindestens zwei Zeilen angegeben werden
  - Maximallänge 35 Zeichen

#### Nationale Adresse
models/common/address-national.json 
- Alle Propertys mit weiteren Einschränkungen wir Maximallänge oder Pattern versehen

#### eID
models/common/eID-org-acting-person.json
- Property "academic-title" in "doctoral-degrees" umbenannt

#### Phone
models/common/phone.json
- Property "number": Formatbeschränkung gelockert
- Property "type" entfernt
- Property "description" hinzugefügt

#### Phone Number
models/common/phonenr.json
- Unbenutztes Modell gelöscht



## Version 0.2
Veröffentlicht 2020-03-31

### Modelle
#### Antragsteller - Organisation
models/application/applicant-organization.json
- Property "role" entfernt
- Property "org-validation/validated" entfernt
- Property "legal-representatives" ist jetzt eine $ref auf models/common/individual.json

#### Antragsteller - Natürliche Person
models/application/applicant-person.json
- Property "role" entfernt

#### Application Schema
Das Schema wurde umgebaut und enthält jetzt drei Angaben:
- mime-type: ist entweder "json" oder "xml"
- schema-source: Quelle für das Schema. Kann "fim" oder "none" sein. Bei "none" dürfen beliebige Datenstrukturen übertragen werden.
- schema-id: ID des Schemas, ist von der Schema Quelle (schema-source) abhängig.

#### Person
Die Person (Verzeichnis models/person/) wurde weitestgehend entfernt. Es gibt nur noch das Modell models/common/individual.json für eine natürliche Person.

#### Phone
models/common/phone.json
- Properties "number" und "type" sind jetzt verpflichtend

#### Destination
Die Destination wurde in mehrere Modelle zerlegt, um dem Sender einen anderen Umfang zu zeigen als dem Subscriber.

#### Statusübersicht
models/status-overview.json
- Umbenannt: models/status.json → models/status-overview.json
- Enum Wert "sending" entfernt
- Property "since" in "timestamp" umbenannt
- Property "number" ergänzt

#### Error Body
models/error-body.json
- Umbenannt: models/error.json → models/error-body.json
- Enthält jetzt ein Array von Fehlern, statt nur einem.

#### Neue Modelle
- base64: models/common/base64.json
- JSON Web Encryption (JWE): models/common/jwe.json
- JSON Web Key (JWK): models/common/jwk.json

### Application Sender API
reference/sender.json
- Vorkommen von "Transfer" in "Application" umbenannt
  - Dadurch sind auch  Operation-IDs geändert worden (siehe unten)
- OAuth2 Scopes ergänzt
- Operation "Get Status Entry" (get-application-status-entry) entfernt
- Operation "Get Application Upload Status"
  - Property "docs/doc-id" ergänzt
- Operation "Create Application": ID in create-application geändert
- Operation "Send Application" (früher "Commit Application"): ID in commit-application geändert

### Application Subscriber API
- OAuth2 Scopes ergänzt
- Operation "Acknowledge Application" (früher "Commit Application"): ID in ack-application geändert

### Dokumentation
Die Dokumentation im Verzeichnis "docs" wurde erstellt.
