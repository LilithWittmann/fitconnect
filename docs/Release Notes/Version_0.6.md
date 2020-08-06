# Version (0.6)

## Dokumentation
- [Fehlercodes](../5_Status-_und_Fehlercodes.md) dokumentiert
- [Erste Schritte](../1_Getting_Started.md) überarbeitet

## Umgesetzte Change Requests
### #3 Sematic error of the OAS in editor.swagger.io
Das Security Schema darf keine Leerzeichen enthalten und wurde deswegen von "OAuth 2.0" in "OAuth20" umbenannt.

### #4 academicTitle -> doctoralDegrees
Alle Vorkommen von "academicTitle" wurden durch "doctoralDegrees" ersetzt.

### #5 telephone -> telephones
Da Arrays mit einem Plural bezeichnet werden sollen wurde "telephone" durch "telephones" ersetzt.

### #7 Regex für Hausnummernzusatz ist falsch
Das Pattern für den Hasnummernzusatz `^[\\p{L}0-9. ]*$` war inkorrekt da die Zeichenklassen `\p{L}` nicht zulässig ist. Es wurde daher zu `^[A-Za-z0-9. ]*$` korrigiert.

### #10 API Specification: senderId and subscriberId in URIs
Die Sender- und Subscriber-ID muss nicht mehr über den Pfad mitgegeben werden sondern wird automatisch über das Token ermittelt. Damit entfallen die IDs als Pfadangabe.

### #11 API Specification: Missing nouns in Sender API URIs endpoints
Die Pfade auf in der Sender API enthielten vor den IDs kein beschreibendes Nomen. Dies wurde korrigiert. Zum Beispiel:
- vorher: `/{destinationId}/{applicationId}/data`
- nachher: `/destinations/{destinationId}/applications/{applicationId}/data`

### #12 API Specification: Missing destinationId in Get Status endpoint of Sender 
Die Operation "Get Status" wies im Gegensatz zu den anderen Operationen keine vorangestellte Destination-ID auf.
- vorher: `/{applicationId}/status`
- nachher: `/destinations/{destinationId}/applications/{applicationId}/status`

### #16 Fachdaten optional
Das Element "data" in der "contentStructure" war verpflichtend. Damit mussten Fachdaten übertragen werden. Das Element ist jetzt optional.
