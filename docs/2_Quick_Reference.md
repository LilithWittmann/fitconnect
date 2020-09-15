# API-Kurzreferenz

## Der XFall Antrag

![application_structure](https://raw.githubusercontent.com/fiep-poc/assets/master/images/quick_reference/application_structure.png "Struktur des XFall Antrags")

Der XFall Antrag (`application`) ist das zentrale Geschäftsobjekt in der XFall API. Der XFall Antrag besteht aus den Fachdaten (`data`) sowie den beigefügten Anhängen (`document`) und wird über die Metadaten ([application metadata](../models/application/metadata.json)) beschrieben.

Die Metadaten des Antrags entsprechen dem früheren XFall-Container und enthalten übergreifenden Informationen über den Antrag sowie Strukturinformationen zu den enthaltenen Fachdaten und Anhängen.

Fachdaten bezeichnen in XFall Antrag im einen strukturieren Datensatz in XML oder JSON und können über ein externes Schema (bspw. aus FIM) beschrieben werden. 

Anhänge können entweder klassische Anhänge (bspw. Nachweise) oder oder eine PDF-Repräsentation der Fachdaten des Antrags, falls eine solche alternative Repräsentation aus rechtlichen, technischen oder organisatorischen Gründen notwendig ist.

## Identifikatoren der XFall Ressourcen

Um Ressourcen eindeutig zu identifizieren, werden in den URLs der REST Endpunkte eine oder mehrere Identifikatoren (IDs) benutzt. 

### Von der API bereitgestellte IDs
#### applicationId
Der Zustelldienst weist jedem übertragenen Antrag (`application`) eine global eindeutige `applicationId` zu, die diesen Antrag dauerhaft über den gesamten Bearbeitungsverlauf eindeutig identifiziert.

#### destinationId
Die `destinationId` ist eine vom Zustelldienst vergebene ID für einen durch den Subscriber angelegten Zustellpunkt (`destination`). Diese ID wird dem Sender über externe Systeme (bspw. Zuständigkeitsfinder) oder bilaterale Absprachen zwischen beiden Seiten mitgeteilt.

### Vom Sender vergebene Identifikatoren
#### docId
Der Sender vergibt für jedes Antragsformular und jede Anlage in einer Übertragung eine `docId`. Diese muss für alle Dokumente (PDF-Antragsformulare und beliebige Anlagen) in der Übertragung eindeutig sein. Es wird empfohlen, die IDs `1`, `2` etc. zu verwenden.

## Operation der Application Sender API

Mit folgenden Operationen kann der Sender eine Application übertragen und die Übertragung verwalten:

- [Create Application](../reference/sender.json/paths/~1destinations~1{destinationId}~1applications/post) - Legt eine neue Übertragung durch Übermittlung der Metadaten an.
- [Add Application Data](../reference/sender.json/paths/~1destinations~1{destinationId}~1applications~1{applicationId}~1data/put) - Fügt dem Antrag strukturierte Daten (Fachdaten) hinzu.
- [Add Application Document](../reference/sender.json/paths/~1destinations~1{destinationId}~1applications~1{applicationId}~1docs~1{docId}/put) - Übermittelt ein Antragsformular oder eine Anlage.
- [Send Application](../reference/sender.json/paths/~1destinations~1{destinationId}~1applications~1{applicationId}/post) - Beendet die Übertragung des Antrags und löst seinen Versand aus.
- [Get Application Upload Status](../reference/sender.json/paths/~1destinations~1{destinationId}~1applications~1{applicationId}~1upload-status/get) - Ruft den Status der Uploads der Teile der Übertragung ab. Für die Fachdaten und Dokumente wird jeweils der Status und die auf dem Server vorliegende Länge in Bytes zurückgegegben.

Darüber hinaus stehen dem Sender folgende weitere Operationen zur Verfügung:

- [Get Destination Info](../reference/sender.json/paths/~1destinations~1{destinationId}/get) - Ruft übertragungsrelevante Informationen über den Zustellpunkt (bspw. zulässige Schemata oder Datentypen) ab.
- [Get Status](../reference/sender.json/paths/~1destinations~1{destinationId}~1applications~1{applicationId}~1status/get) - Ruft den Status sowie die Statushistorie der Zustellung des Antrags ab.

## Operation der Application Subscriber API

Mit diesen Operationen kann der Subscriber eine oder mehrere Zustellpunkte (`Destinations`) verwalten:
- [Create Destination](../reference/subscriber.json/paths/~1destinations/post) - Legt ein neues Übertragungsziel (Destination) an.
- [List Destinations](../reference/subscriber.json/paths/~1destinations/get) - Listet alle Übertragungsziele (Destinations) eines Subscribers auf.
- [Get Destination](../reference/subscriber.json/paths/~1destinations~1{destinationId}/get) - Ruf die Daten eines Übertragungsziels (Destination) ab.
- [Update Destination](../reference/subscriber.json/paths/~1destinations~1{destinationId}/put) - Aktualisiert ein Übertragungsziel (Destination).
- [Delete Destination](../reference/subscriber.json/paths/~1destinations~1{destinationId}/delete) - Löscht ein Übertragungsziel (Destination).

Mit diesen Operationen wird nach wartenden Applications gesucht und diese abgeholt:
- [List Applications](../reference/subscriber.json/paths/~1destinations~1{destinationId}~1applications/get) - Ruft die Liste der wartenden Übertragungen (Applications) ab.
- [Get Application Metadata](../reference/subscriber.json/paths/~1destinations~1{destinationId}~1applications~1{applicationId}/get) - Ruft eine wartende Übertragung (Application) ab.
- [Get Application Data](../reference/subscriber.json/paths/~1destinations~1{destinationId}~1applications~1{applicationId}~1data/get) - Ruft die Fachdaten einer Übertragung (Application Data) ab.
- [Get Application Document](../reference/subscriber.json/paths/~1destinations~1{destinationId}~1applications~1{applicationId}~1docs~1{docId}/get) - Ruf ein Dokument (Formular oder Anlage) der Application ab.
- [Acknowledge Application](../reference/subscriber.json/paths/~1destinations~1{destinationId}~1applications~1{applicationId}/post) - Quittiert die Abholung der Übertragung.
