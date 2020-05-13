# Version 0.3
## Modelle

### Application Metadata
models/application/metadata-no-id.json
- Property "data/size" ergänzt

### eID
models/common/eID-org-acting-person.json
- Property "artictic-name" in "artistic-name" umbenannt

### Internationale Adresse
models/common/address-international.json 
- Property "lines":
  - Es müssen mindestens zwei Zeilen angegeben werden
  - Maximallänge 35 Zeichen

### Nationale Adresse
models/common/address-national.json 
- Alle Propertys mit weiteren Einschränkungen wir Maximallänge oder Pattern versehen

### eID
models/common/eID-org-acting-person.json
- Property "academic-title" in "doctoral-degrees" umbenannt

### Phone
models/common/phone.json
- Property "number": Formatbeschränkung gelockert
- Property "type" entfernt
- Property "description" hinzugefügt

### Phone Number
models/common/phonenr.json
- Unbenutztes Modell gelöscht
