# Überblick über die XFall API

Willkommen auf der API Dokumentation für die XFall REST API von FIT-Connect. Die XFall API baut auf dem bestehenden IT-Planungsrat Standard XFall auf und bietet Lösungsverantwortlichen von antragssendenden und antragsempfangenden Systemen eine einfache Möglichkeit, ihre Software schnell und wirtschaftlich in länder- und ebenenübergreifende Antragsprozesse zu integrieren.

## Was ist die XFall API und was unterscheidet diese API vom bisherigen XFall Standard?

Die XFall API baut auf den bisherigen Konzepten und Erfahrungen des bestehenden IT-Planungsrats Standards XFall auf. 

> Die übergreifende Zielstellung des Standards XFall besteht darin, Anträge und Berichte, die aus vorgelagerten Systemen (bspw. Onlineantragsdienste, Fachportale oder Berichtssysteme) erstellt werden, in die unterschiedlichen Systeme der elektronischen Verfahrensbearbeitung (bspw. Fachverfahren, Dokumentenmanagementsystem oder Prozessplattformen) zu übergeben. 

Bei der Entwicklung der XFall API wurden viele Konzepte mit Hinblick auf die neuen Erfordernisse des Onlinezugangsgesetzes, der SDG-Verordnung sowie den Anforderungen digitaler Geschäftsmodelle weiterentwickelt. Technisch nutzt die XFall API auf einen leichtgewichtigen RESTful-Architekturstil und baut auf der föderalen Antragsübertragungsarchitektur von FIT-Connect auf.

## Was macht die XFall API und wie kann diese genutzt werden?

Die XFall API besteht aus zwei getrennt nutzbaren APIs:
- Für antragsempfangende Systeme wird eine `Application Subscriber API` für den Empfang von Anträgen sowie eine `Callback` / Webhook Funktion für die technische Benachrichtigung über vorliegende Anträge angeboten. 
- Für antragssendende Systeme wird eine `Application Sender API` angeboten, um an beliebige antragsempfangende Systeme Anträge zu senden, die sich mit einem Zustellpunkt registriert haben.

Diese beiden APIs werden durch einen zentralen Intermediär (`XFall Zustelldienst`) bereitgestellt. Um auf diese APIs zuzugreifen, müssen interessierte Entwickler ihre Anwendungen beim FIT-Connect Autorisierungsdienst vorab registrieren.

### Zusammenspiel der APIs in der Antragsübermittlung
![Applicationtransfer_Architecture](https://raw.githubusercontent.com/fiep-poc/assets/2c7cc84217ea55a3004751c62ef49e80458b579a/images/api_overview/XFall_Integration_Architecture.jpg "Antragsübertragungsarchitektur FIT-Connect")

Über die `Application Subscriber API` können die zuständigen Stellen für ihre Systeme einen Zustellpunkt eröffnen, der über eine `destination-Id` eindeutig adressierbar ist. Für diese Zustellpunkte legen die zuständigen Stellen alle fachlichen Vorgaben (Zulässige Fachstandards, Verschlüsselung, Datenformate etc.) fest, damit eine medienbruchfreie Weiterverarbeitung in ihren Systemen gewährleistet ist. Über die Angabe der `destination-Id` in der `Application Sender API` können beliebige antragssendende Systemen Anträge an die zuständige Stelle senden.

Dieser Zustellpunkt ist jedoch vorab für eine Verwaltungsleistung und den jeweiligen örtlichen Antragskontext (bspw. Ort der Antragsstellung) korrekt zu ermitteln. Damit die Ermittlung des korrekten Zustellpunkts skalierbar für das ganze Bundesgebiet funktioniert, ist langfristig vorgesehen, die `destination-Id` in den Leistungs- und Zuständigkeitsinformationen des jeweils bekannten Zuständigkeitsfinders zu hinterlegen. Diese dezentral gepflegten Informationen sollen durch das Online-Gateway (https://www.onlinezugangsgesetz.de/Webs/OZG/DE/umsetzung/portalverbund/online-gateway/online-gateway-node.html) gebündelt und über eine offene API im XZuFi Format (https://www.xrepository.de/details/urn:xoev-de:fim:standard:xzufi) nutzbar gemacht werden.

![Applicationtransfer_Architecture](https://raw.githubusercontent.com/fiep-poc/assets/master/images/api_overview/Pflege%20und%20Ermittlung%20destination-Id.jpg "Pflege und Ermittlung der destination-Id")

## Für wen ist die XFall API gedacht und warum sollte ich sie nutzen?

Die XFall API ist für alle Hersteller, Entwickler und Verfahrensverantwortliche von antragssendenden und antragsempfangenden Systemen gedacht. Insbesondere folgende Systeme mit bundesweiten Nutzungsszenarien sollen mit der XFall API unterstützt werden:
- **Einer für alle (EfA) Verfahren**: Länderübergreifend entwickelte Antragsverfahren für eine bestimmte Verwaltungsleistung oder ein Leistungsbündel, die entweder in verschiedenen Ländern nachnutzbar betrieben werden oder länderübergreifend als gemeinsamer Antragsdienst für alle zuständigen Stellen betrieben werden.
- **Antragsgeneratoren / Antragsmanagementsysteme**: Standardsoftware zur Erstellung und dem Betrieb von direkt nutzbaren Onlineantragsdiensten, die im ganzen Bundesgebiet bei einzelnen Stellen oder Gebietskörperschaften (bspw. als Basiskomponente) im Einsatz sind.
- **Als Standardsoftware bereitgestellte Fachverfahrenssoftware, Prozessplattformen oder Dokumentenmanagementsysteme**: Bundesweit angebotene und eingesetzte Standardsoftware, die von den zuständigen Stellen für die Antragsbearbeitung eingesetzt wird.

Für diese Systeme bietet die XFall bei der schnellen und wirtschaftlichen Realisierung medienbruchfreier Antragsprozesse eine Reihe von Mehrwerten: 
- **Plug and Play Anbindung an die föderale Antragsübermittlung**: Durch die zentral bereitgestellten APIs und die Nutzung der bestehenden Zuständigkeitsfinderinfrastruktur können Systeme schnell an eine föderale Antragsübermittlungsinfrastruktur angebunden werden, ohne eigene Infrastrukturen hierfür zu beauftragen oder aufzubauen.
- **Leichgewichtige APIs und Industriestandards**: Die XFall API baut auf leichgewichtigen RESTful API Ansätzen auf und nutzt verbreitete Industriestandards wie die OpenAPI Specification und OAuth 2.0, sodass kein spezialisiertes Know-How und spezifische Softwarekomponenten für die Anbindung erforderlich sind.
- **Flexibilität in der Antragsübermittlung**: Die XFall API verbindet Flexibilität und Standardisierung. Während die XFall API eine einheitliche Metadatenstruktur festlegt, um Anträge strukturiert zu verarbeiten, können beliebige Fachstandards und Anhänge übertragen werden. Auch die Übertragung von Anträgen im PDF Format ist möglich, solange für die Antragsdaten noch kein FIM Schema vorhanden ist.
**Nutzung bestehender Prozesse und Strukturen für die Pflege von Adressierungsinformationen**: Langjährig erprobte Prozesse und Strukturen zur Pflege der Zuständigkeitsinformationen, können in den zuständigen Stellen beibehalten werden. Technische Adressierungsparameter der XFall API werden über die gleichen Systeme und Prozesse gepflegt, die schon heute bei Informationen zu Anschriften, Rufnummern, E-Mail-Adressen oder Ansprechpartnern genutzt werden.
- **Machine2Machine Ready**: Die XFall API und die FIT-Connect Antragsübertragungsarchitektur sind von Grund auf als offene API-Plattform konzipiert. Dadurch können auch verwaltungsexterne Antrags- und Berichtssysteme wie Drittsoftware oder Unternehmenssysteme direkt eingebunden werden, ohne das hierfür eine gesonderte Infrastruktur notwendig ist.

### Ist die XFall API nur für länder- und behördenübergreifende Antragskontexte gedacht?

Durch die einfache Anbindung und Nutzung bietet sich die XFall API auch dort an, wo das behördeneigene Antragsverfahren mit dem behördeneigenen Fachverfahren verbunden wird. Durch die Nutzung der XFall API werden diese Systeme standardisiert verbunden, ohne das die Behörde in Abhängigkeiten zu proprietären Technologien und Schnittstellen gerät. Dies ermöglicht es der Behörde, ihre Systeme auf beiden Seiten flexibel auszutauschen und weiterzuentwickeln, um somit auf neue technische Trends und Möglichkeit schnell zu reagieren.

## In welchem Stand befindet sich XFall REST API und wann kann man die API nutzen?

Die Entwicklung und Bereitstellung der XFall REST API erfolgt im Rahmen eines Proof of Concepts für die geplante föderale Integrations- und Entwicklungsplattform FIT-Connect. Seit dem zweiten Quartal 2020 ist es interessierten Parteien möglich, einen Zugang zur XFall API zu bekommen und eine prototypische Anbindung von Verfahren umzusetzen.