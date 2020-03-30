# Überblick über die XFall API

Willkomen auf der API Dokumentation für die XFall RESTful API. Zusammen mit der föderalen Integrations- und Entwicklungsplattform ermöglicht die XFall RESTful API Lösungsverantwortlichen und Entwicklern von OZG-Verfahren, ihre Anwendungen schnell und wirtschaftlich in medienbruchfreie Antragsprozesse zu integrieren. 

Das zentrale Ziel der XFall RESTful API:
> Lösungsverantwortliche und Entwickler werden von wiederkehrenden Integrationsherausforderungen im Antragsprozess entlastet und können wertvolle Kapazitäten darauf fokussieren, Innovationen in der Verwaltung voranzutreiben und nutzerzentrierte Lösungen für Antragssteller und Sachbearbeitern schnell und kostengünstig in die Breite zu bringen!

## Was ist die XFall RESTful API und was unterscheidet diese vom bisherigen XFall Standard?

Die XFall RESTful API baut auf den bisherigen Konzepten und Erfahrungen des bestehenden IT-Planungsrats Standards XFall auf. Die übergreifende Zielstellung von XFall besteht darin, Anträge und Berichte, die aus vorgelagerten Systemen (bspw. Onlineantragsdienste, Fachportale oder Berichtssysteme) erstellt werden, in die unterschiedlichen Systeme der elektronische Verfahrensbearbeitung zu übergeben. 

Ausgehend von dieser Aufgabestellung, ist die XFall RESTful API auch keine einheitliche API, sondern besteht aus zwei dedizierten APIs für Sender (`Application Sender API`) und Empfänger von Anträgen (`Application Subscriber API`).

Bei der Entwicklung der XFall RESTful API wurden viele Konzepte mit Hinblick auf die neuen Erfordernisse des Onlinezugangsgesetzes, dem EU-Single Digital Gateway sowie den Anforderungen moderner digitaler Geschäftsmodelle grundlegend weiterentwickelt. Im Vergleich zum bisherigen XFall-Standard, setzt die XFall RESTful API auf einen leichgewichtigen REST-Architekturstil und ergänzt die API um eine einheitliche föderale Integrations- und Entwicklungsinfrastruktur:
- Eine Integrationsplattform, welche die APIs für die Beteiligten bereitstellt und viele Integrationsherausforderungen zentral löst. Die Integrationsplattform folgt dem "Lightweight Messaging Principle", sodass keine Fachlogik im Übermittelungsprozess durch die Integrationsplattform übernommen wird, sondern die Hohheit beim Empfänger liegt und für den Sender die Zustellunglogik transparent.
- Ein Entwicklerportal, da alle Informationen und Ressourcen für Anbindung an die XFall RESTful API bereitstellt. Neben zentral erstellten Informationen und Werkzeugen ,sollen auch bisher dezentral vorliegende Informationen bedarfsgerecht gebündelt und vernetzt werden, sodass für Entwickler eine mühsame Suche kritischer Informationen entfällt.

## In welchem Stand befindet sich XFall RESTful API und wann kann man die API nutzen?

Die Entwicklung und Bereitstellung der XFall RESTful API erfolgt im Rahmen eines Proof of Concepts für die geplante föderale Integrations- und Entwicklungsplattform. Der Proof of Concept und das Gesamtvorhaben wird durch die FITKO (https://www.fitko.de) verantwortet. 

Im Rahmen des Proof of Concepts wird es ab dem zweiten Quartal 2020 möglich sein, dass interessierte Organisationen und Projekte einen Zugang zum API-Portal bekommen und eine prototypische Anbindung von Verfahren umsetzen können. 

Die langfristige produktive Nutzung der XFall RESTful API hängt jedoch vom Ausgang des Proof of Concepts und der weiteren Planung der föderalen Integrations- und Entwicklungsplattform ab.

### Was ist die föderale Integrations- und Entwicklungsplattform? 

Die föderale Integrations- und Entwicklungsplattform ist ein strategischer Ansatz, um die aktuellen Herausforderungen in der verteilten OZG Umsetzung zu adressieren. 

Durch die föderale Integrations- und Entwicklungsplattform soll den OZG-Umsetzungsverantwortlichen und Lösungsentwicklern eine stabile und leistungsfähige Basis bereitgestellt werden, um schnell und wirtschaftlich bundesweit nutzbare und interopable Lösungen für Verwaltungsleistungen zu entwickeln.

Die föderale Integrations- und Entwicklungsplattform baut hierbei auf zwei zentralen Säulen auf:
-	Leichtgewichtige Schnittstellen auf Basis etablierter Industriestandards sowie zentral bereitgestellte Integrationskomponenten, um wiederkehrende Integrationsherausforderungen im verteilten föderalen Vorgehen zu lösen oder zu minimieren.
-	Eine gemeinsame Entwicklerplattform mit zentral bereitgestellten Entwicklungs- und Testwerkwerkzeugen, um die Entwicklung interoperabler Verfahren für die Antragsstellung und Antragsbearbeitung zu vereinfachen und zu beschleunigen.

Die föderale Integrations- und Entwicklungsplattform folgt einem offenen Plattformgedanken und soll einen Kulturwandel in der Entwicklung digitaler Verwaltungslösungen einleuten.
-	Der Staat stellt eine digitale Basis an Funktionen und Daten auf Basis offener Standards und Komponenten jedem frei zur Verfügung. 
-	Dies ermöglicht es allen gesellschaftlichen Akteuren (Behörden, Unternehmen, Non-Profit Organisationen, Bürger) neue digitale Lösungen und Innovationen frei zu erstellen. 
-	Entwickelte Lösungen können durch den Staat eingebunden, beauftragt oder eingekauft werden oder abseits des Staates im Rahmen neuer kommerzieller oder gesellschaftlicher Geschäftsmodelle eingebunden werden.

Die föderale Integrations- und Entwicklungsplattform ist dabei ganz bewusst nicht als zentralischer Ansatz zu sehen, sondern als ein föderaler Ansatz, da sowohl bei der Entwicklung von Antragsdiensten als Antragsbearbeitungssystem eine hohe Autonomie in der Umsetzung belassen wird.

![FIEP_Strategic_Vision](https://raw.githubusercontent.com/fiep-poc/assets/master/images/api_overview/FIEP_strategic_vision.png "Vision der föderalen Integrations- und Entwicklungsplattform")

### Wozu dient der Proof of Concept?

Der Proof of Concept (PoC) soll wesentliche Grundprinzipien und Lösungsansätze der föderalen Integrations- und Entwicklungsplattform am Beispiel der Antragsübermittlung praktisch erproben. Für diesen Zweck wird der bestehende XFall Standard für den PoC als offene RESTful API weiterentwickelt und die dazugehörigen Integrationskomponenten und Entwicklerressourcen prototypisch bereitgestellt.

Mit dem PoC soll aufgezeigt werden, dass mit den zwei Säulen der föderalen Integrations- und Entwicklungsplattform und dem offenen Plattformansatz ein echter Mehrwert für die Entwicklung interoperabler und skalierbarer Lösungen geschaffen werden kann, um die föderale Verwaltungsdigitalisierung in Deutschland grundlegend voranzutreiben.

Bei einem positiven Ergebnis des PoC wird angestrebt, die föderale Integrations- und Entwicklungsplattform als Gesamtansatz umzusetzen und die XFall RESTful API produktiv anzubieten sowie weitere APIs für das Antragsmanagement zu entwickeln.

### Überblick PoC-Integrationsarchitektur

![PoC_Integrationarchitecture](https://raw.githubusercontent.com/fiep-poc/assets/master/images/api_overview/PoC_integrationarchitecture.jpg "Integrationsarchitektur für den PoC")

#### Komponenten
Für den PoC werden zwei zentrale Komponenten bereitgestellt:
- **XFall-Zustelldienst:** Dieser Dienst stellt die `Application Sender API` und `Application Subscriber API` bereit.
- **API-Gateway:** Das API-Gatway regelt den Zugriff auf die API (Authorisierung, Rate-Limiting, Sicherheitsüberprüfungen, etc.) des XFall-Zustelldienstes und stellt zusammen mit der angebundenen IdM-Komponente die Authentifizierung für den API-Zugriff bereit. Für einen API-Client ist das API-Gatway in der API-Nutzung nicht direkt sichtbar.

#### Ablauf
Die Integrationsarchitektur sieht vor, dass eine empfangende Behörde oder ein Dienstleister (bspw. eine kommunales Rechenzentrum) über die `Application Subscriber API` initial eine Zustellpunkt mit einer eindeutigen `destination-id` anlegt. 

Diese `destination-id` wird im Rahmen des PoC mit der Antragssenderseite bilateral ausgetauscht bzw. über einen vereinbaren Kanal veröffentlicht. Diese ID wird dann durch die Anwendung auf der Senderseite in der `Application Sender API` genutzt, um die korrekte Stelle zu adressieren und den Antrag beim Zustellpunkt abzugeben. Die empfangende Behörde oder der Dienstleister können dann mit beliebigen technischen Systemen diesen Antrag beim angelegten Zustellpunkt abholen.

#### Langfristige Vision
Die Integrationsarchitektur wird im Rahmen des PoC um einige zentrale Aspekte vereinfacht, die für die zukünftige Integrationsarchitektur fest eingeplant sind:
- **Nutzung von Zuständigkeitsfindern:** Langfristig ist angedacht, die `destination-id` über die bestehenden und etablierten Zuständigkeitsfindern von Bund und Ländern und deren Redaktionsprozesse zu veröffentlichen. Damit steht ein skalierbarer Ansatz bereit, bei dem Antragsdienste in Echtzeit während der Antragsstellung die `destination-id` der fachlich und örtlich zuständigen Stelle beim einem Zuständigkeitsfinder ermitteln können. Durch diesen Ansatz sind keine aufwendigen bilateralen Absprachen in der Entwicklung mehr notwendig, sondern die Antragsdienste können einen universellen zuständigkeitsbasierten Ansatz auf Basis föderaler Basisinfrastukturen nutzen!

![destination-id_publishing_jurisdiction-finder](https://raw.githubusercontent.com/fiep-poc/fiep-poc/develop/assets/images/api_overview/destination-id_publishing_jurisdiction-finder.png?token=AOHBJRJFNZQDZFRNM25AFSS6RMN2C "Redaktionsprozess zur Veröffentlichung einer Destination-ID in einem Zuständigkeitsfinder")

- **Standardisierte XTA-Einbindung:** Mit XTA steht ein in vielen Teilen der Verwaltung etablierter Standard bereit, um standardisiert Transportverfahren anzubinden, welche die eigentliche Übertragung von Fachdaten über diverse Protokolle und Kommunikationsinfrastrukturen für das Fachverfahren übernehmen. Während es schon im PoC prinzipiell möglich sein sollte, technische Intermedäre für die XFall RESTful API Anbindung per XTA-SOAP Webservice anzusprechen, wird zukünftig eine vollumfängliche Unterstützung alle XTA Bestandteile (wie bspw. Reports) angestrebt.
- **Anbindung von Servicekonten und Antragsmanagementkomponenten:** Zukünftig soll der XFall-Zustelldienst alle antragsrelevenaten Daten (Kopien der Antragsdaten und Statusinformationen) bei definierten Ereignissen (Abgabe beim Zustelldienst und Abholung am Zustellpunkt) in den Hohheitsbereich des Antragsstellers übermitteln und damit Antragsdienst und Fachverfahren von dieser Querschnittsaufgabe entlasten. Hierfür ist angedacht, die zukünftig verfügbaren interoperablen Postfächer als standardisierten Übertragsweg in den Hohheitsbereich des Antragsstellers zu nutzen.

![future_integrationarchitecture](https://raw.githubusercontent.com/fiep-poc/assets/master/images/api_overview/future_integrationarchitecture.jpg "Zielvision Integrationsarchitektur für die Antragsstellung")
