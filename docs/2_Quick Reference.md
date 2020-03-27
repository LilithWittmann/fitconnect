# API-Kurzreferenz

## IDs in den XFall Endpunkten

Um Ressourcen eindeutig zu identifizieren, werden in den URLs der REST Endpunkt eine oder mehrere Identifikatoren benutzt. 

### Durch die API bereitgestellte IDs
#### application-id
Der Zustelldienst weist jeder Übertragung (Application) eine global eindeutige `application-id` zu.

#### destination-id
Für jeden vom Subscriber angelegtes Übertragungsziel vergibt der Zustelldienst eine global eindeutige `destination-id`.

### Extern vergebene IDs
#### source-id
Die `source-id` ist die ID des Accounts, der die Übertragung absendet. Sie wird vom genutzten Identitätssystem vergeben und muss global eindeutig sein.

#### subscriber-id
Die `subscriber-id` ist die ID des Accounts, der die Übertragung empfängt. Sie wird vom genutzten Identitätssystem vergeben und muss global eindeutig sein.

### Vom Sender vergebene IDs
#### doc-id
Der Sender vergibt für jedes Antragsformular und jede Anlage in einer Übertragung eine `doc-id`. Diese muss für alle Dokumente (Antragsformulare und Anlagen) in der Übertragung eindeutig sein. Es wird empfohlen, die IDs `1`, `2` etc. zu verwenden.

## Application Sender API
### Verwendete IDs
Es werden folgende Pfadparameter in der URL verwendet:
- `source-id`: Wird mit dem Source Account zugewiesen.
- `destination-id`: Über externes System (Zuständigkeitsfinder) dem Onlineantragsdienst bekannt.
- `application-id`: Vom Zustelldienst vergebene ID für die Übertragung.

### Operationen
Mit folgenden Operationen kann der Sender eine Application übertragen und die Übertragung verwalten:

- [Create Application](../reference/sender.json/paths/~1{source-id}~1{destination-id}/post)
Legt eine neue Übertragung an.
- [Add Application Data](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}~1data/put)
Fügt dem Antrag strukturierte Daten hinzu.
- [Add Application Document](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}~1docs~1{doc-id}/put)
Übermittelt ein Antragsformular oder eine Anlage.
- [Send Application](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}/post)
Beendet die Übertragung des Antrags und löst seinen Versand aus.
- [Get Application Upload Status](../reference/sender.json/paths/~1{source-id}~1{destination-id}~1{application-id}~1upload-status/get)
Ruft den Status der Uploads der Teile der Übertragung ab. Für die Fachdaten und Dokumente wird jeweils der Status und die auf dem Server vorliegende Länge in Bytes zurückgegegben.

Darüber hinaus stehen dem Sender folgende weitere Operationen zur Verfügung:

- 

## Application Subscriber API

### Verwendete IDs

...

**Noch in Arbeit**

...

### Operationen

Mit diesen Operationen werden die Abonnements (im Sinne von Destinations) des Backends/Subscribers verwaltet:
- [Create Destination](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations/post)
Legt ein neues Übertragungsziel (Destination) an.
- [List Destinations](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations/get)
Listet alle Übertragungsziele (Destinations) eines Subscribers auf.
- [Get Destination](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}/get)
Ruf die Daten eines Übertragungsziels (Destination) ab.
- [Update Destination](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}/put)
Aktualisiert ein Übertragungsziel (Destination).
- [Delete Destination](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}/delete)
Löscht ein Übertragungsziel (Destination).

Mit diesen Operationen wird nach wartenden Applications gesucht und diese abgeholt:
- [List Applications](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications/get)
Ruft die Liste der wartenden Übertragungen (Applications) ab.
- [Get Application](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications~1{application-id}/get)
Ruft eine wartende Übertragung (Application) ab.
- [Get Application Data](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications~1{application-id}~1application-data/get)
Ruft die Fachdaten einer Übertragung (Application Data) ab.
- [Get Application Document](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications~1{application-id}~1docs~1{doc-id}/get)
Ruf ein Dokument (Formular oder Anlage) der Application ab.
- [Acknowledge Application](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications~1{application-id}/post)
Quittiert die Abholung der Übertragung.
