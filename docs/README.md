# Überblick über die XFall API

Willkomen auf der API Dokumentation für die XFall RESTful API. Zusammen mit der föderalen Integrations- und Entwicklungsplattform ermöglicht die XFall RESTful API Lösungsverantwortlichen und Entwicklern von OZG-Verfahren, ihre Anwendungen schnell und wirtschaftlich in medienbruchfreie Antragsprozesse zu integrieren. 

Das Ziel der XFall RESTful API:
> Lösungsverantwortliche und Entwickler werden von wiederkehrenden Integrationsherausforderungen im Antragsprozess entlastet und können wertvolle Kapazitäten darauf fokussieren, neue Verwaltungsinnovationen voranzutreiben und nutzerzentrierte Lösungen für Antragssteller und Sachbearbeitern schnell und kostengünstig in die Breite zu bringen!

## Was ist die XFall RESTful API und was unterscheidet diese vom bisherigen XFall Standard?

Die XFall RESTful API baut auf den bisherigen Konzepten und Erfahrungen des bestehenden IT-Planungsrats Standards XFall auf. Die übergreifende Zielstellung von XFall besteht darin, Anträge und Berichte, die aus vorgelagerten Systemen (bspw. Onlineantragsdienste, Fachportale oder Berichtssysteme) erstellt werden, in die unterschiedlichen Systeme der elektronische Verfahrensbearbeitung der Verwaltung zu übergeben. 

Ausgehend von dieser Aufgabestellung ist die XFall RESTful API keine einheitliche API, sondern besteht aus zwei dedizierten APIs für Sender (`Application Sender API`) und von Anträgen (`Application Subscriber API`).

Bei der Entwicklung der XFall RESTful API wurde viele Konzepte mit Hinblick auf die neuen Erfordernisse des Onlinezugangsgesetzes, dem EU-Single Digital Gateway sowie Anforderungen moderner digitaler Geschäftsmodelle grundlegend weiterentwickelt. Im Vergleich zum bisherigen XFall-Standard setzt die XFall RESTful API auf einen leichgewichtigen REST-Architekturstil und ergänzt die API um eine einheitliche föderale Integrations- und Entwicklungsinfrastruktur:
- Eine Integrationsplattform, welche die APIs für die Beteiligten anbietet und viele viele Integrationsherausforderungen gemeinsam löst. Diese Integrationsplattform folgt dem "Lightweight Messaging Principle", sodass keine Fachlogik im Übermittelungsprozess durch die Integrationsplattform übernommen wird, sondern die Hohheit beim Empfänger liegt und für den Sender eine transparente Zustellunglogik besteht.
- Eine zentrale Entwicklerplattform, die alle Informationen und Ressourcen für Anbindung an die XFall RESTful API bereitstellt. Neben zentral erstellten Informationen und Werkzeugen soll auch bisher verteilte vorliegende Informationen bedarfsgerecht gebündelt oder vernetzt werden, sodass für Entwickler eine mühsame Suche kritischer Informationen entfällt.

## In welchem Stand befindet sich XFall RESTful API und wann kann man die API nutzen?

Die Entwicklung und Bereitstellung der XFall RESTful API erfolgt im Rahmen des Proof of Concepts der geplanten föderalen Integrations- und Entwicklungsplattform und durch die FITKO (https://www.fitko.de) verantwortet. Im Rahmen dieses Proof of Concepts wird es ab dem zweiten Quartal 2020 möglich sein, dass interessierte Beteiligte einen Zugang zum API-Portal bekommen und für verschiedene Verwaltungsleistungen eine prototypische Anbindung von Verfahren umsetzen können. 

Die langfristige Nutzung der XFall RESTful API hängt vom Ausgang des Proof of Concepts und der weiteren Planung der föderalen Integrations- und Entwicklungsplattform ab.

### Was ist die föderale Integrations- und Entwicklungsplattform? 

Die föderale Integrations- und Entwicklungsplattform ist ein strategischer Ansatz, um die aktuellen Herausforderungen in der verteilten OZG Umsetzung zu adressieren. Sie soll den OZG-Umsetzungsverantwortlichen und Lösungsentwicklern eine stabile und leistungsfähige Basis bereitstellen, um schnell und wirtschaftlich bundesweit nutzbare und interopable Lösungen für Verwaltungsleistungen zu entwickeln.

Die föderale Integrations- und Entwicklungsplattform baut auf zwei Säulen auf:
-	Leichtgewichtige Schnittstellen auf Basis etablierter Industriestandards sowie zentral bereitgestellte Integrationskomponenten, um wiederkehrende Integrationsherausforderungen im verteilten föderalen Vorgehen zu lösen oder zu minimieren.
-	Eine gemeinsame Entwicklerplattform mit zentral bereitgestellten Entwicklungs- und Testwerkwerkzeugen, um die Entwicklung interoperabler Verfahren für die Antragsstellung und Antragsbearbeitung zu vereinfachen und zu beschleunigen. Hierbei sollen Ressourcen und Informationen zu allen gängigen föderalen Integrationsfällen und Basisdiensten für Softwareentwickler und Verfahrenverantwortliche bedarfsgerecht gebündelt und bereitgestellt werden.

Die föderale Integrations- und Entwicklungsplattform folgt einem offenen Plattformgedanken und soll einen Kulturwandel in der Entwicklung digitaler Verwaltungslösungen einleuten.
-	Der Staat stellt eine digitale Basis an Funktionen und Daten auf Basis offener Standards und Komponenten jedem frei zur Verfügung. 
-	Dies ermöglicht es allen gesellschaftlichen Akteuren (Behörden, Unternehmen, Non-Profit Organisationen, Bürger) neue digitale Lösungen und Innovationen frei zu erstellen. 
-	Entwickelte Lösungen können durch den Staat eingebunden, beauftragt oder eingekauft werden oder abseits des Staates im Rahmen neuer kommerzieller oder gesellschaftlicher Geschäftsmodelle eingebunden werden.

Die föderale Integrations- und Entwicklungsplattform ist dabei ganz bewusst nicht als zentralischer Ansatz zu sehen, sondern als ein föderaler Ansatz, der die Stärken des Föderalismus und der sozialen Markwirtschaft zum Tragen kommen lässt.

![FIEP_Strategic_Vision](https://raw.githubusercontent.com/fiep-poc/fiep-poc/documentation/assets/images/api_overview/FIEP_strategic_vision.png?token=AOHBJRMFXOHXXYUFKVCPVNC6Q5KM6 "Vision der föderalen Integrations- und Entwicklungsplattform")

### Wozu dient der Proof of Concept?

Der Proof of Concept (PoC) soll wesentliche Grundprinzipien und Lösungsansätze der föderalen Integrations- und Entwicklungsplattform am Beispiel der Antragsübermittlung praktisch erproben. Für diesen Zweck wurde der bestehende XFall Standard für den PoC als offene RESTful API weiterentwicklet und die dazugehörigen Integrationskomponenten und Entwicklerressourcen prototypisch bereitgestellt.

Ziel ist es aufzuzeigen, dass mit den zwei Säulen der föderalen Integrations- und Entwicklungsplattform und dem offenen Plattformansatz ein echter Mehrwert für die Entwicklung interoperabler und skalierbarer Lösungen generiert werden kann, um hiermit die föderale Verwaltungsdigitalisierung in Deutschland grundlegend voranzutreiben und zu beschleunigen.

Bei einem positiven Ergebnis des PoC wird angestrebt, die föderale Integrations- und Entwicklungsplattform als Gesamtansatz föderal umzusetzen und die XFall RESTful API sowie weitere APIs für die föderale Entwicklungsbereiche produktiv anzubieten.

### Überblick PoC-Integrationsarchitektur

![PoC_Integrationarchitecture]( "Integrationsarchitektur für den PoC")

Für den PoC werden zwei zentrale Komponenten bereitgestellt:
- XFall-Zustelldienst: Dieser Dienst stellt die `Application Sender API` und `Application Subscriber API` und die dahinter liegenden fachlichen Funktionen bereit.
- API-Gateway: Das API-Gatway regelt den Zugriff (Authorisierung, Rate-Limiting, Sicherheitsüberprüfungen, etc.) auf die APIs des XFall-Zustelldienstes und stellt die Authentifizierung für den Zugriff auf die API. Für einen API-Client ist das API-Gatway im Rahmen der Zustelldienstes nicht direkt sichtbar.

Die Integrationsarchitektur sieht vor, dass eine empfangende Behörde oder ein Dienstleister (bspw. eine kommunales Rechenzentrum) über die `Application Subscriber API` eine Zustellpunkt mit einer eindeutigen `destination-id` anlegen. Diese wird im Rahmen des PoC mit der Antragssenderseite bilateral ausgetauscht bzw. über einen vereinbaren Kanal veröffentlicht. Diese ID wird dann durch die Anwendung auf der Senderseite in der API genutzt, um die korrekte Stelle zu adressieren und bei deren Zustellpunkt den Antrag abzugeben. Die empfangende Behörde oder der Dienstleister können mit beliebigen technischen Systemen diesen Antrag beim angelegten Zustellpunkt abholen.

Die Integrationsarchitektur vereinfacht jedoch einige zentrale Aspekte, die für die zukünftige Integrationsplattform im Rahmen der Antragsstellung vorgesehen sind:
- **Nutzung von Zuständigkeitsfindern: **Langfristig ist angedacht, die `destination-id` über die bestehenden und etablierten Zuständigkeitsfindern von Bund und Ländern und deren Redaktionsprozesse zu veröffentlichen. Damit steht ein skalierbarer Ansatz bereit, bei dem Antragsdienste in Echtzeit während der Antragsstellung die `destination-id` der fachlich und örtlich zuständigen Stelle beim einem Zuständigkeitsfinder ermitteln können. Durch diesen Ansatz sind keine aufwendigen bilateralen Absprachen in der Entwicklung mehr notwendig, sondern die Antragsdienste können einen universellen zuständigkeitsbasierten Ansatz auf Basis föderaler Basisinfrastukturen nutzen!
- **Standardisierte XTA-Einbindung: **Mit XTA steht ein in vielen Teilen der Verwaltung etablierter Standard bereit, um standardisiert Transportverfahren anzubinden, welche die eigentliche Übertragung von Fachdaten über diverse Protokolle und Kommunikationsinfrastrukturen für das Fachverfahren übernehmen. Während es schon im PoC prinzipiell möglich sein sollte, technische Intermedäre für die XFall RESTful API Anbindung per XTA-SOAP Webservice anzusprechen, wird zukünftig eine vollumfängliche Unterstützung alle XTA Bestandteile (wie bspw. Reports) angestrebt.
- **Anbindung von Servicekonten und Antragsmanagementkomponenten:** Zukünftig soll der XFall-Zustelldienst alle antragsrelevenaten Daten (Kopien der Antragsdaten und Statusinformationen) bei definierten Ereignissen (Abgabe beim Zustelldienst und Abholung am Zustellpunkt) in den Hohheitsbereich des Antragsstellers übermitteln und damit Antragsdienst und Fachverfahren von dieser Querschnittsaufgabe entlasten. Hierfür ist angedacht, die zukünftig verfügbaren interoperablen Postfächer als standardisierten Übertragsweg in den Hohheitsbereich des Antragsstellers zu nutzen.