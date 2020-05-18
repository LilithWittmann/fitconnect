# Nächste Version (0.5)

## Dokumentation
- Release Notes mit aufgenommen
- Dokumentation zu OAuth integriert
- Token URL eingetragen
- Postman Collection & Environment integriert

## Modelle
- CR-1: Diversen Modellen den Discriminator "type" hinzugefügt:
  - models/application/applicant-contact-info.json
  - models/application/applicant-contact-info.json
  - models/application/applicant-person.json
  - models/application/applicant.json
  - models/common/address-international.json
  - models/common/address-national.json
  - models/common/address-postbox.json
  - models/common/individual.json
  - models/destination-no-id.json

### Destination
models/destination-no-id.json

### Postfachadresse
models/common/address-national.json
models/common/address-postbox.json
- Um ein doppeltes `oneOf` zu vermeiden wurde die Postfach Adresse aus der nationalen Adresse herausgelöst.

## Application Sender API

### Application Document
models/application/document.json
- Regex Pattern für SHA-256/512 Hash präzisiert: "[0-9A-F]{64,128}" -> "^[A-Fa-f0-9]{64}([A-Fa-f0-9]{64})?$"

## Application Subscriber API

### Acknowledge Application
- Bugfix: Property `final-delivery` auf Camelcase umgestellt.
- Bugfix: Angaben von `finalDelivery` in Acknowledge Application ist verpflichtend.

# Geplant
- Pfad der APIs um Versionsnummer erweitert:
  - https://sender.fiep-poc.de/v0.5/
  - https://subscriber.fiep-poc.de/v0.5/
