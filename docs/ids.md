# IDs

![REST Resourcen](../assets/images/REST_Resourcen.svg)

## Extern vergebene IDs
### source-id
Die `source-id` ist die ID des Accounts, der die Übertragung absendet. Sie wird vom genutzten Identitätssystem vergeben und muss global eindeutig sein.

### subscriber-id
Die `subscriber-id` ist die ID des Accounts, der die Übertragung empfängt. Sie wird vom genutzten Identitätssystem vergeben und muss global eindeutig sein.

## Vom Sender vergebene IDs
### doc-id
Der Sender vergibt für jedes Antragsformular und jede Anlage in einer Übertragung eine `doc-id`. Diese muss für alle Dokumente (Antragsformulare und Anlagen) in der Übertragung eindeutig sein. Es wird empfohlen, die IDs `1`, `2` etc. zu verwenden.

## Vom Zustelldienst vergebene IDs
### application-id
Der Zustelldienst weist jeder Übertragung (Application) eine global eindeutige `application-id` zu.

### destination-id
Für jeden vom Subscriber angelegtes Übertragungsziel vergibt der Zustelldienst eine global eindeutige `destination-id`.

### schema-id
Für jedes einer Destination zugeordnetes Appication Schema vergibt der Zustelldienst eine global eindeutige `schema-id`.
