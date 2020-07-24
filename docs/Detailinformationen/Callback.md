# Callback Benachrichtigungen

Callbacks sind einfache Webhooks und dienen dazu, API Nutzer über relevante Ereignisse aktiv zu informieren, anstatt das der Client über konstante Abfragen an der API potentielle Änderungen oder Eigenisse abzufragen muss. 

Aktuell wird den Subscribern eine Callback Funktion angeboten, um diese über abrufbereite Anträge in ihren Destinations zu informieren.

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
        "telephones": [
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
