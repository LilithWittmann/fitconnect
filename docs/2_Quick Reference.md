# API-Kurzreferenz

## Der XFall Antrag

![application_structure](https://raw.githubusercontent.com/fiep-poc/fiep-poc/documentation/assets/images/quick_reference/application_structure.png?token=AOHBJROKKDX4MECV4WW6IKC6Q4ZYS "Struktur des XFall Antrags")

Der XFall Antrag (`application`) ist das zentrale Geschäftsobjekt in der XFall API. Dieser besteht aus den Fachdaten (`data`) und den beigefügten Anhängen (`document`) und wird über Metadaten beschrieben.

Die Metadaten des Antrags ([Application Metadata](../models/application/metadata.json)) entsprechen dem früheren XFall-Container und enthalten allgemeine Informationen über den Antrag, die enthaltenen Fachdaten und die enthaltenen Anhänge:

- Die `application-id` zur eindeutigen Identifizierung des Antrags (diese wird erst nach initialer Anlage der Antragsressource von der API vergeben)
- Fachliche Informationen über den Antrag (zusätzliche Prozessinfromationen, Antragssteller oder Bezahlinformationen)
- Angaben zu, verwendeten Schema in den Fachdaten
- Anzahl und Strukturinformationen zu den enthaltenen Anhängen

Fachdaten bezeichnen in XFall im einen strukturieren Datensatz in XML oder JSON und können über ein externes Schema (bspw. aus FIM) beschrieben werden. Anhänge können entweder klassische Anhänge (bspw. Nachweise) sein oder oder eine PDF Representation des Fachantrags, falls dies aus rechtlichen oder technischen Gründen notwendig ist.

## Identifikatoren der XFall Ressourcen

Um Ressourcen eindeutig zu identifizieren, werden in den URLs der REST Endpunkt eine oder mehrere Identifikatoren (IDs) benutzt. 

### Von der API bereitgestellte IDs
#### application-id
Der Zustelldienst weist jedem übertragenen Antrag (`Application`) eine global eindeutige `application-id` zu, die diesen Antrag dauerhaft über den gesamten Bearbeitungsverlauf eindeutig identifiziert.

#### destination-id
Die `destination-id` ist eine vom Zustelldienst vergebene ID für einen durch den Subscriber angelegten Zustellpunkt (`destination`). Diese ID wird dem Sender über externe Systeme (bspw. Zuständigkeitsfinder) oder bilaterale Absprachen zwischen beiden Seiten mitgeteilt.

### Vom API-Portal bereitgestellte IDs
#### source-id
Die `source-id` ist die ID des Accounts, der die Übertragung absendet. Sie wird vom genutzten Identitätssystem vergeben und muss global eindeutig sein.

#### subscriber-id
Die `subscriber-id` ist die ID des Accounts, der die Übertragung empfängt. Sie wird vom genutzten Identitätssystem vergeben und muss global eindeutig sein.

### Vom Sender vergebene Identifikatoren
#### doc-id
Der Sender vergibt für jedes Antragsformular und jede Anlage in einer Übertragung eine `doc-id`. Diese muss für alle Dokumente (PDF-Antragsformulare und beliebige Anlagen) in der Übertragung eindeutig sein. Es wird empfohlen, die IDs `1`, `2` etc. zu verwenden.

## Operation der Application Sender API

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

- [Get Destination](../reference/sender.json/paths/~1{source-id}~1{destination-id}/get): Ruft übertIagungsrelevante nformationen über den Zustellpunkt (bspw. zulässige Schemata oder Datentypen) ab.
- [Get Status](../reference/sender.json/paths/~1{source-id}~1{application-id}~1status/get): Ruft den Status sowie die Statushistorie der Zustellung des Antrags ab.

## Operation derApplication Subscriber API

Mit diesen Operationen kann der Subscriber Zustellpunkte (`Destinations`) verwalten:
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
