# Überblick über die XFall API

Willkomen auf der API Dokumentation für die XFall RESTful API von FIT-Connect. Die XFall API baut auf dem bestehenden IT-Planungsrat Standard XFall auf und bietet Lösungsverantwortlichen antragssendenen und antragsempfangenden Systemen eine einfache Möglichkeit, ihre Software schnell und wirtschaftlich in länder und ebeneübergreifende Antragsprozesse zu integrieren.

## Was ist die XFall API und was unterscheidet diese API vom bisherigen XFall Standard?

Die XFall API baut auf den bisherigen Konzepten und Erfahrungen des bestehenden IT-Planungsrats Standards XFall auf. 

> Die übergreifende Zielstellung des Standards XFall besteht darin, Anträge und Berichte, die aus vorgelagerten Systemen (bspw. Onlineantragsdienste, Fachportale oder Berichtssysteme) erstellt werden, in die unterschiedlichen Systeme der elektronische Verfahrensbearbeitung (bspw. Fachverfahren, DMS) zu übergeben. 

Bei der Entwicklung der XFall API wurden viele Konzepte mit Hinblick auf die neuen Erfordernisse des Onlinezugangsgesetzes, der SDG-Verordnung sowie den Anforderungen digitaler Geschäftsmodelle. Technisch setzt die XFall API auf einen leichgewichtigen RESTful-Architekturstil und baut auf der föderalen Antragsübertragungsarchitektur von FIT-Connect auf.

## Was macht die XFall API und wie kann diese genutzt werden?

Die XFall API besteht aus zwei getrennt nutzbaren APIs für antragsempfangende Systeme (`Application Subscriber API` sowie eine `Callback` / Webhook Funktion) und antragssendenden Systeme (`Application Sender API`). Diese beiden APIs werden durch einen zentralen Intermediär (`XFall Zustelldienst`) als Angebote angeboten. Um auf diese APIs zuzugreifen, müssen interessierte Entwickler und Verfahrensverantwortliche ihre Anwendungen über zunächst beim FIT-Connect Autorisierungsdienst registrieren.

![Applicationtransfer_Architecture](https://raw.githubusercontent.com/fiep-poc/assets/2c7cc84217ea55a3004751c62ef49e80458b579a/images/api_overview/XFall_Integration_Architecture.jpg "Antragsübertragungsarchitektur FIT-Connect")

Über die `Application Subscriber API` können die zuständigen antragsempfangenden Stellen Zustellpunkte eröffnen, die über eine `destination-Id`eindeutig adressierbar sind. Mit dieser `destination-Id` können beliebigen antragssendene Systemen über die `Application Sender API` Anträge an die jeweils zuständige Stelle senden.

Für diese Zustellpunkte legen die zuständigen Stellen alle fachlichen Vorgaben (Zulässige Fachstandards, Verschlüsselung, Datenformate etc.) fest, damit eine medienbruchfreie Weiterverarbeitung gewährleistet ist. Damit der korrekte Zustellpunkt für eine konkrete Verwaltungsleistung und den jeweiligen regionalen Antragsbezug (bspw. Ort der Antragsstellung) ermittelt werden kann, ist langfristig vorgesehen, die `destination-Id` jeweils bekannten Zuständigkeitsfinder zu hinterlegen. Die dort hinterlegten Informationen sollen durch das Online-Gateway (https://www.onlinezugangsgesetz.de/Webs/OZG/DE/umsetzung/portalverbund/online-gateway/online-gateway-node.html) gebündelt und  über eine offene API für alle Antragsdienste im XZuFi Format (https://www.xrepository.de/details/urn:xoev-de:fim:standard:xzufi) nutzbar gemacht werden.

![Applicationtransfer_Architecture](https://raw.githubusercontent.com/fiep-poc/assets/master/images/api_overview/Pflege%20und%20Ermittlung%20destination-Id.jpg "Pflege und Ermittlung der destination-Id")

## Für wen ist die XFall API gedacht und warum sollte ich es nutzen?

Die XFall API ist für alle Hersteller, Entwickler und Verfahrensverantwortliche von antragssendenden und antragsempfangenden Systemen gedacht, mittels eine generischen, skalierbaren und offenen Ansatz ihre jeweiligen Systeme mit der Gegenseite im Rahmen der Antragsübermittlung verbinden wollen. Insbesondere folgende Umsetzungsmodelle von Antragsdiensten und Antragsbearbeitungssoftware sollen mit der XFall API und der unterliegenden FIT-Connect Antragsübertrachtungsarchitektur unterstützt werden:
- **Einer für alle (EfA) Verfahren**: Länderübergreifend entwickelte Antragsverfahren für eine bestimmte Verwaltungsleistung oder ein Leistungsbündel, die entweder in verschiedenen Ländern nachnutzbar betrieben werden oder sogar länderübergreifend generischer Antragsdienst für alle zuständigen Stellen betrieben werden.
- **Antragsgeneratoren / Antragsmanagementsysysteme**: Generische Systeme zu Erstellung von lauffähigen und dirket nutzbaren Onlineantragsdiensten für bestimmte Antragsleistungen sowohl für eine zuständige Stelle, ein ganzes Land oder das ganze Bundesgebiet. 
- **Von Standardsoftwareherstellern bereitgestellte Fachverfahrenssoftware, Prozessplattformen oder Dokumentenmanagementsystemen**: Bundesweit angebotene und eingesetzte Standardsoftware, die von den zuständigen Stellen für die Antragsbearbeitung eingesetzt wird.

Für diese fachlichen Szenarien bietet die XFall API ein großen Mehrwert 
- **Plug and Play Anbindung an die föderale Antragsübermittlung**: Durch die zentral bereitgestellten APIs und die Nutzung der bestehenden Zuständigsfinderinfrastruktur können Antragsdienste und antragsbearbeitende Systeme im föderalen Kontext standardisierte Antragsdaten austauschen, ohne zusätzliche Infrastrukturen für den Transport zu beauftragen oder aufzubauen. 
- **Leichgewichtige APIs und Industriestandards**: Die XFall API baut auf leichgewichtigen RESTful API Ansätzen auf und nutzt zudem verbreitete Industriestandards, wie bspw. OpenAPI und JSON Schema für API Spezifikation und OAuth 2.0 für die API Autorisierung, sodass keine spezialisierten Know-How und Komponenten für die Anbindung von Anwendungen erforderlich ist.
- **Flexibilität in der Antragsübermittlung**: Die XFall API verbindet Flexibilität und Standardisierung. Während die XFall API eine einheitliche Metadatenstruktur festlegt, um Anträge strukturiert zu verarbeiten, können beliebige Fachstandards sowie standardspezifische Datenformate und Anhänge übertragen werden. Auch die Übertragung von Anträgen im PDF Format ist möglich, sodass auch eine standardisierte Übertragung des Antrags schon möglich ist, während sich noch die enstprechende FIM Artefakte in der Entwicklung befinden.
**Nutzung bestehender Prozesse und Strukturen für die Pflege von Adressierungsinformationen**: Durch die Nutzung der XFall API können  langjährig erprobte Prozesse und Strukturen in den zuständigen Stellen zur Pflege ihrer Zuständnigskeitsinformationen beibehalten werden. Technische Adressierungsparameter der XFall API können genauso standardisiert in den vorhandenen Systemen gepflegt werden, wie heute schon Adressen, Rufnummer, E-Mail Adressen oder Anspechpartner.
- **Machine2Machine Ready**: Dadurch, dass die XFall API und FIT-Connect Antragsinfrastruktur von Grund auf als offene API konzipiert ist, können mit der XFall API auch verwaltungsexterne Antrags- und Berichtssysteme wie Drittsoftware oder Unternehmenssysteme direkt eingebunden werden, ohne Prozesse oder Infrastrukturen anzupassen. Die erlaubt ermöglicht es zuständigen Stellen einfach un kostengünstig über weitere Zugängskanale erreichbar zu sein und damit die Attraktivität des elektronischen Kanals zu erhöhen.

### Ist die XFall API nur für länder- und behördenübergreifende Antragskontexte gedacht?

Durch die einfache Anbindung und Nutzung bietet sich die XFall API auch dort an, wo das behördeneigene Antragsverfahren mit dem jeweiligen Antragssystem verbunden wird. Den durch die Nutzung der XFall API und die Antragsübertragungsinfrastruktur werden systeme standardisiert verbunden, ohne das die Behörde in Abhängigkeiten zu proprietären Technologien und Schnittstellen gerät.  

## In welchem Stand befindet sich XFall REST API und wann kann man die API nutzen?

Die Entwicklung und Bereitstellung der XFall REST API erfolgt im Rahmen eines Proof of Concepts für die geplante föderale Integrations- und Entwicklungsplattform. Seit dem zweiten Quartal 2020 ist interessierten Parteien möglich, einen Zugang zur XFall API zu bekommen und eine prototypische Anbindung von Verfahren umzusetzen.

Hieraus ergeben sich noch einige Einschränkungen der API Nutzung. So ist eine standardisierte Einbindung des Onlinegateway aktuell noch nicht möglich, sodass die `destination-Id` über eigene Zuständigkeitsfinder oder alternative Austauschmethoden an die Antragsdienste verteilt werden muss.

Die langfristige produktive Nutzung der XFall REST API hängt vom Ausgang des Proof of Concepts und der weiteren Planung von FIT-Connect ab.