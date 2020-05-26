# Version 0.2
Veröffentlicht 2020-03-31

## Modelle
### Antragsteller - Organisation
models/application/applicant-organization.json
- Property "role" entfernt
- Property "org-validation/validated" entfernt
- Property "legal-representatives" ist jetzt eine $ref auf models/common/individual.json

### Antragsteller - Natürliche Person
models/application/applicant-person.json
- Property "role" entfernt

### Application Schema
Das Schema wurde umgebaut und enthält jetzt drei Angaben:
- mime-type: ist entweder "json" oder "xml"
- schema-source: Quelle für das Schema. Kann "fim" oder "none" sein. Bei "none" dürfen beliebige Datenstrukturen übertragen werden.
- schema-id: ID des Schemas, ist von der Schema Quelle (schema-source) abhängig.

### Person
Die Person (Verzeichnis models/person/) wurde weitestgehend entfernt. Es gibt nur noch das Modell models/common/individual.json für eine natürliche Person.

### Phone
models/common/phone.json
- Properties "number" und "type" sind jetzt verpflichtend

### Destination
Die Destination wurde in mehrere Modelle zerlegt, um dem Sender einen anderen Umfang zu zeigen als dem Subscriber.

### Statusübersicht
models/status-overview.json
- Umbenannt: models/status.json → models/status-overview.json
- Enum Wert "sending" entfernt
- Property "since" in "timestamp" umbenannt
- Property "number" ergänzt

### Error Body
models/error-body.json
- Umbenannt: models/error.json → models/error-body.json
- Enthält jetzt ein Array von Fehlern, statt nur einem.

### Neue Modelle
- base64: models/common/base64.json
- JSON Web Encryption (JWE): models/common/jwe.json
- JSON Web Key (JWK): models/common/jwk.json

## Application Sender API
reference/sender.json
- Vorkommen von "Transfer" in "Application" umbenannt
  - Dadurch sind auch  Operation-IDs geändert worden (siehe unten)
- OAuth2 Scopes ergänzt
- Operation "Get Status Entry" (get-application-status-entry) entfernt
- Operation "Get Application Upload Status"
  - Property "docs/doc-id" ergänzt
- Operation "Create Application": ID in create-application geändert
- Operation "Send Application" (früher "Commit Application"): ID in commit-application geändert

## Application Subscriber API
- OAuth2 Scopes ergänzt
- Operation "Acknowledge Application" (früher "Commit Application"): ID in ack-application geändert

## Dokumentation
Die Dokumentation im Verzeichnis "docs" wurde erstellt.
