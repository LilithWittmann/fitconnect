# Architekturregeln

## OpenAPI

- Wir verwenden OpenAPI 3.0
- Die Spezifikation wird als JSON geschreiben
- Wir verwenden keine Versionsnummer im Dateinamen, da das Repo als Ganzes versioniert wird

## Verzeichnisse

Das Projektverzeichnis ist wie folgt aufgebaut:

- 📁`assets`
  - 📁`images` - Bilder
  - 📁`postman` - Postman-Collection und -Enviroment dazu
- 📁`docs` - Öffentliche Dokumentation zu den APIs
- 📁`models` - Modelle, die von mehreren (beiden) APIs verwendet werden
- 📁`reference` - Die APIs
- 📄`LICENSE`

## Bezeichner

- Die Bezeichner werden camelCase geschreiben und beginnen mit einem Kleinbuchstaben
- Eine ID (Identifikator) wird als `Id` (nicht `ID`) geschrieben

## Pfade

Multiple Resoucen werden im Pfad durch eine Collection-Resource und einer nachfolgenden ID aufgenommen

Beispiel: `/destinations/{destinationId}/applications/{applicationId}`

## Fehler

Es gibt ein einheitlichen Fehler-Body, der (soweit möglich) von allen Fehlermeldungen verwendet wird.


