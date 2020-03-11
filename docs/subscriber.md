# Application Subscriber API
## Subscriber Operationen
Mit diesem Satz von Operationen werden die Abonnements (Subscriptions bzw. Destinations) des Backends/Subscribers verwaltet.



### [Create Destination](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations/post)
Legt ein neues Übertragungsziel (Destination) an.

#### Request
- Body: [Destination](../models/destination.json)

#### Response
- Body: destination-id

Beispiel:
```json
{ "destination-id": "123e4567-e89b-12d3-a456-426655440000" }
```
**Hinweis:** Die `destination-id` kann, muss aber keine UUID sein. Der Subscriber hat sie als einen beliebigen String zu behandeln.



### [List Destinations](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations/get)
Listet alle Übertragungsziele (Destinations) eines Subscribers auf.



### [Get Destination](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}/get)
Ruf die Daten eines Übertragungsziels (Destination) ab.



### [Update Destination](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}/put)
Aktualisiert ein Übertragungsziel (Destination).



### [Delete Destination](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}/delete)
Löscht ein Übertragungsziel (Destination).



## Application Operationen
Mit diesem Satz von Operationen wird nach wartenden Transfers/Applications gesucht und diese abgeholt.



### [List Applications](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications/get)
Ruft die Liste der wartenden Übertragungen (Applications) ab.



### [Get Application](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications~1{application-id}/get)
Ruft eine wartende Übertragung (Application) ab.



### [Get Application Data](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications~1{application-id}~1application-data/get)
Ruft die Fachdaten einer Übertragung (Application Data) ab.

Beispiele:
#### JSON
```json
{
    "F99000001": "Eins",
    "G99000001": {
        "F99000002": "Zwei",
        "F99000003": "Drei"
    }
}
```

#### XML
```xml
<S99000001>
  <F99000001>Eins</F99000001>
  <G99000001>
    <F99000002>Zwei</F99000002>
    <F99000003>Drei</F99000003>
  </G99000001>
</S99000001>
```



### [Get Application Form](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications~1{application-id}~1application-forms~1{form-id}/get)
Ruft ein Antragsformular einer Übertragung (Application Form) ab.



### [Get Attachment](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications~1{application-id}~1attachments~1{attachment-id}/get)
Ruft eine Anlage einer Übertragung (Attachment) ab.



### [Commit Application](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}~1applications~1{application-id}/post)
Quittiert die Abholung der Übertragung.


