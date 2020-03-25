# Application Subscriber API
## Subscriber Operationen
### Destination Operationen
Mit diesem Satz von Operationen werden die Abonnements (Subscriptions bzw. Destinations) des Backends/Subscribers verwaltet.
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

### Application Operationen
Mit diesem Satz von Operationen wird nach wartenden Transfers/Applications gesucht und diese abgeholt.
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
