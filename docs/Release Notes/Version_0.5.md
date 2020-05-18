# Nächste Version (0.5)

## Übergreifende Änderungen

### Basis-URLs
Die Basis-URLs werden ab sofort mit jeder neuen Version geändert, damit ein paralleler Betrieb mehrerer API-Versionen möglich ist.
Die Basis-URLs für diese Version sind:
- https://sender.fiep-poc.de/beta5/
- https://subscriber.fiep-poc.de/beta5/

### CR-1: Diversen Modellen den Discriminator "type" hinzugefügt:
- models/application/applicant-contact-info.json
- models/application/applicant-contact-info.json
- models/application/applicant-person.json
- models/application/applicant.json
- models/common/address-international.json
- models/common/address-national.json
- models/common/address-postbox.json
- models/common/individual.json
- models/destination-no-id.json

### CR-3: Source in Sender ändern
In der Dokumentation werden die Begriffe "Source" und "Sender" synonym verwendet. Um die Dokumentation klarer zu machen, wurden alle Vorkommen von "Source" in "Sender" geändert.

<!-- theme: warning -->
> **Hinweis:** Dies wirkt sich auch auf die OAuth-Scopes aus. Der Scope `{senderId}:source:manage` wurde in `{senderId}:sender:manage` geändert.

### CR-5: Zusätzliche Properties verbieten
Wo möglich wurde `"additionalProperties": false` gesetzt um weitere Properties zu verbieten.

## Dokumentation
- Release Notes mit aufgenommen
- Dokumentation zu OAuth integriert
- Token URL eingetragen
- Postman Collection & Environment integriert

## Modelle

### Destination
models/destination-no-id.json

### Postfachadresse
models/common/address-national.json
models/common/address-postbox.json
- Um ein doppeltes `oneOf` zu vermeiden wurde die Postfach Adresse aus der nationalen Adresse herausgelöst.

## Application Sender API

### Application Document
models/application/document.json
- Regex Pattern für SHA-256/512 Hash präzisiert: "`[0-9A-F]{64,128}`" -> "`^[A-Fa-f0-9]{64}([A-Fa-f0-9]{64})?$`"

## Application Subscriber API

### Acknowledge Application
- Bugfix: Property `final-delivery` auf Camelcase umgestellt.
- Bugfix: Angaben von `finalDelivery` in Acknowledge Application ist verpflichtend.
