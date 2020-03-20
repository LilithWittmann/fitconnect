# Application Sender API
## Transfer Operationen
### IDs
Es werden folgende Parameter in der URL verwendet:
- `source-id`: Wird mit dem Source Account zugewiesen.
- `destination-id`: Über externes System (Zuständigkeitsfinder) dem Onlineantragsdienst bekannt.
- `application-id`: Vom Zustelldienst vergebene ID für die Übertragung.

### Operationen
- [Create Application](../reference/sender.json/paths/~1{source-id}~1{destination-id}/post)
Legt eine neue Übertragung an.
- [Add Application Data](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}~1data/put)
Fügt dem Antrag strukturierte Daten hinzu.
- [Add Application Document](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}~1docs~1{doc-id}/put)
Übermittelt ein Antragsformular oder eine Anlage.
- [Send Application](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}/post)
Beendet die Übertragung des Antrags und löst seinen Versand aus.
- [Get Application Upload Status](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}~1upload-status/get)
Ruft den Status der Uploads der Teile der Übertragung ab. Für die Fachdaten und Dokumente wird jeweils der Status und die auf dem Server vorliegende Länge in Bytes zurückgegegben. Der Status kann folgende Werte haben:
  - `missing`: Es wurden noch keine Daten hochgeladen (`length` = 0).
  - `partial`: Es wurden bereits Daten hochgeladen, jedoch weniger als in den Metadaten angegeben (0 < `length` < `size` aus Metadaten).
  - `complete`: Die Übertragung ist vollständig (`length` = `size` aus Metadaten).
