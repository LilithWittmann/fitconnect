# Callback
## Callback registrieren
Beim [anlegen](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations/post) oder [aktualisieren](../reference/subscriber.json/paths/~1{subscriber-id}~1destinations~1{destination-id}/put) einer Destination sollte ein Callback angegeben werden.

```json
{
  "organization": {
    "organization-name": "Gewerbeamt Musterhausen"
  },
  "technical-contact": [
    {
      "first-name": "Werner",
      "last-name": "Mustermann",
      "contact": {
        "telephone": [
          {
            "number": "+49 89 32168-42",
            "mobile": false,
            "type": "work"
          }
        ]
      }
    }
  ],
  "callback": {
    "callback-url": "https://www.example.com/callback"
  }
}
```

## Callback ausführen
Trifft nun ein neuer Antrag ein, so sendet der Zustelldienst einen HTTP-POST-Request an die angegebene Adresse. Im Body des Requests werden die `destination-id` und die `application-id`s der wartenden Anträge (i.d.R. genau eine) aufgelistet.

```json
{
  "destination-id": "821",
  "applications": [
    {
      "application-id": "98472"
    }
  ]
}
```

## Callback nur bei Inaktivität
Nach einem Callback wartet der Zustelldienst eine gewisse Zeit (z.B. 5 Minuten) bis zum nächsten Callback, auch wenn in dieser Zeit neue Anträge eintreffen. Diese Wartezeit wird bei Aktivität der Destination (z.B. Abfrage der Queue oder Abholen von Anträgen) verlängert.
