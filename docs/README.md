# Überblick über die XFall API

Willkomen auf der API Dokumentation für die XFall RESTful API von FIT-Connect. Die XFall API baut auf dem bestehenden IT-Planungsrat Standard XFall auf und bietet Lösungsverantwortlichen antragssendenen und antragsempfangenden Systemen eine einfache Möglichkeit, ihre Software schnell und wirtschaftlich in länder und ebeneübergreifende Antragsprozesse zu integrieren.

## Was ist die XFall API und was unterscheidet diese API vom bisherigen XFall Standard?

Die XFall API baut auf den bisherigen Konzepten und Erfahrungen des bestehenden IT-Planungsrats Standards XFall auf. 

> Die übergreifende Zielstellung des Standards XFall besteht darin, Anträge und Berichte, die aus vorgelagerten Systemen (bspw. Onlineantragsdienste, Fachportale oder Berichtssysteme) erstellt werden, in die unterschiedlichen Systeme der elektronische Verfahrensbearbeitung (bspw. Fachverfahren, DMS) zu übergeben. 

Bei der Entwicklung der XFall API wurden viele Konzepte mit Hinblick auf die neuen Erfordernisse des Onlinezugangsgesetzes, der SDG-Verordnung sowie den Anforderungen digitaler Geschäftsmodelle. Technisch setzt die XFall API auf einen leichgewichtigen RESTful-Architekturstil und baut auf der föderalen Antragsübertragungsarchitektur von FIT-Connect auf.

## Was macht die XFall API und wie kann diese genutzt werden?

Die XFall API besteht aus zwei getrennt nutzbaren APIs für antragsempfangende Systeme (`Application Subscriber API` sowie eine `Callback` / Webhook Funktion) und antragssendenden Systeme (`Application Sender API`). Diese beiden APIs werden durch einen zentralen Intermediär (`XFall Zustelldienst`) als Angebote angeboten. Um auf diese APIs zuzugreifen, müssen interessierte Entwickler und Verfahrensverantwortliche ihre Anwendungen über zunächst beim FIT-Connect Autorisierungsdienst registrieren.

(Abbildung mit Architekturübersicht einfügen)

Über die `Application Subscriber API` können die zuständigen antragsempfangenden Stellen Zustellpunkte eröffnen, die über eine `destination-Id`eindeutig adressierbar sind. Mit dieser `destination-Id` können beliebigen antragssendene Systemen über die `Application Sender API` Anträge an die jeweils zuständige Stelle senden.

Für diese Zustellpunkte legen die zuständigen Stellen alle fachlichen Vorgaben (Zulässige Fachstandards, Verschlüsselung, Datenformate etc.) fest, damit eine medienbruchfreie Weiterverarbeitung gewährleistet ist. Damit der korrekte Zustellpunkt für eine konkrete Verwaltungsleistung und den jeweiligen regionalen Antragsbezug (bspw. Ort der Antragsstellung) ermittelt werden kann, ist langfristig vorgesehen, die `Destination-ID` jeweils bekannten Zuständigkeitsfinder zu hinterlegen. Die dort hinterlegten Informationen sollen durch das Online-Gateway (https://www.onlinezugangsgesetz.de/Webs/OZG/DE/umsetzung/portalverbund/online-gateway/online-gateway-node.html) gebündelt und  über eine offene API für alle Antragsdienste im XZuFi Format (https://www.xrepository.de/details/urn:xoev-de:fim:standard:xzufi) nutzbar gemacht werden.

(Abbildung einfügen)

## Für wen ist die XFall API gedacht und warum sollte ich es nutzen?

Wie soll 

## In welchem Stand befindet sich XFall REST API und wann kann man die API nutzen?

Die Entwicklung und Bereitstellung der XFall REST API erfolgt im Rahmen eines Proof of Concepts für die geplante föderale Integrations- und Entwicklungsplattform. Seit dem zweiten Quartal 2020 ist interessierten Parteien möglich, einen Zugang zur XFall API zu bekommen und eine prototypische Anbindung von Verfahren umzusetzen.

Hieraus 

Die langfristige produktive Nutzung der XFall REST API hängt vom Ausgang des Proof of Concepts und der weiteren Planung der föderalen Integrations- und Entwicklungsplattform ab.

## 

