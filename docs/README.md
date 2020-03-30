# Überblick über die XFall API

Willkomen auf der API Dokumentation für die XFall RESTful API. Zusammen mit der föderalen Integrations- und Entwicklungsplattform ermöglicht die XFall RESTful API es, dass Lösungsverantwortlichen und Entwicklern von OZG-Verfahren, ihre Verfahren schnell und wirtschaftlich in medienbruchfreie Antragsprozesse zu integrieren. 

Das Ziel der XFall RESTful API:
> Lösungsverantwortliche und Entwickler werden von wiederkehrenden Integrationsherausforderungen im Antragsprozess entlastet und können wertvolle Kapazitäten darauf fokussieren, neue Innovationen voranzutreiben und nutzerzentrierte  Lösungen für Antragssteller und Sachbearbeitern in die Breite zu bringen!

## Was ist die XFall RESTful API und was unterscheidet diese vom bisherigen XFall Standard?

Die XFall RESTful API baut auf den bisherigen Konzepten und Erfahrungen des bestehenden IT-Planungsrats auf. Die übergreifende Zielstellung von XFall besteht darin, Anträge und Berichte, die aus den vorgelagerten Systemen (bspw. Onlineantragsdienste, Fachportal oder Berichtssysteme) erstellt werden, in die elektronische Verfahrensbearbeitung der Verwaltung zu übergeben. 

Ausgehend hiervon ist die XFall RESTful API keine einheitliche API, sondern besteht aus zwei dedizierten APIs für die Sender von Anträgen (`Application Sender API`) und die Empfänger von Anträgen (`Application Subscriber API`).

Bei der Entwicklung der XFall RESTful API wurde viele Konzepte mit Hinblick auf die neuen Erfordernisse des Onlinezugangsgesetzes, dem EU-Single Digital Gateway sowie Anforderungen moderner digitaler Geschäftsmodelle grundlegend weiterentwickelt. Im Vergleich zum bisherigen XFall-Standard setzt die XFall RESTful API auf einen leichgewichtigen REST-Architekturstil und ergänzt die API um eine einheitliche föderale Infrastruktur:
- Eine dem "Lightweight Messaging Principle" folgende Integrationsplattform, die die APIs für die Beteiligten anbietet und viele Integrationsherausforderungen auf beiden Seiten löst.
- Eine zentrale Entwicklerplattform, die alle Informationen und Ressourcen für Anbindung an die XFall RESTful API bereitstellt.

### Langfristige Vision der Integrationsarchitektur

**...
Vision mit Schaubild und Ausführungen aufzeigen
**

**Abweichungn klar machen
...**

## In welchem Stand befindet sich XFall RESTful API und wann kann man die API nutzen?

Die Entwicklung und Bereitstellung der XFall RESTful API erfolgt im Rahmen des Proof of Concepts der zukünftig angedachten föderalen Integrations- und Entwicklungsplattform. Im Rahmen dieses Proof of Concepts wird es ab dem zweiten Quartal 2020 möglich sein, dass interessierte Beteiligte einen Zugang zum API-Portal bekommen und für verschiedene Verwaltungsleistungen eine prototypische Anbindung von Verfahren umsetzen können. 

Die langfristige Nutzung der API hängt jedoch vom Ausgang des Proof of Concepts und der weiteren Planung der föderalen Integrations- und Entwicklungsplattform ab.

### Was ist die föderale Integrations- und Entwicklungsplattform? 

Die föderale Integrations- und Entwicklungsplattform ist ein strategischer Ansatz, um die aktuellen Herausforderungen in der verteilten OZG Umsetzung zu adressieren. Sie soll den OZG-Umsetzungsverantwortlichen und Lösungsentwicklern eine Basis bereitstellen, um schnell und wirtschaftlich bundesweit nutzbare und interopable Lösungen für Verwaltungsleistungen zu entwickeln.

Die föderale Integrations- und Entwicklungsplattform baut auf zwei Säulen auf:
-	Leichtgewichtige Schnittstellen auf Basis etablierter Industriestandards sowie zentral bereitgestellte Integrationskomponenten, um wiederkehrende Integrationsherausforderungen im verteilten föderalen Vorgehen zu lösen oder zu minimieren.
-	Eine gemeinsame Entwicklerplattform und zentral bereitgestellte Entwicklungs- und Testwerkwerkzeuge, um die Entwicklung interoperabler Verfahren für die Antragsstellung und Antragsbearbeitung zu vereinfachen und zu beschleunigen. Hierbei sollen Ressourcen und Informationen zu allen gängigen föderalen Integrationsfällen und Basisdiensten für Softwareentwickler und Verfahrenverantwortliche in transparenter Weise gebündelt und zentral bereitgestellt werden.

Die föderale Integrations- und Entwicklungsplattform folgt einem offenen Plattformgedanken und wird hiermit einen Kulturwandel in der Entwicklung digitaler Verwaltungslösungen einleuten.
-	Der Staat stellt eine digitale Basis an Funktionen und Daten auf Basis offener Standards und Komponenten jedem frei zur Verfügung. 
-	Dies ermöglicht es allen gesellschaftlichen Akteuren (Behörden, Unternehmen, Non-Profit Organisationen, Bürger) neue digitale Lösungen und Innovationen frei zu erstellen. 
-	Entwickelte Lösungen können durch den Staat eingebunden, beauftragt oder eingekauft werden oder abseits des Staates im Rahmen neuer kommerzieller oder gesellschaftlicher Geschäftsmodelle eingebunden werden.

![FIEP_Strategic_Vision](https://raw.githubusercontent.com/fiep-poc/fiep-poc/documentation/assets/images/api_overview/FIEP_strategic_vision.png?token=AOHBJRMFXOHXXYUFKVCPVNC6Q5KM6 "Vision der föderalen Integrations- und Entwicklungsplattform")

### Wozu dient der Proof of Concept?

Der Proof of Concept soll wesentliche Grundprinzipien und Lösungsansätze der föderalen Integrations- und Entwicklungsplattform am Beispiel der Antragsübermittlung praktisch zu erproben. Für diesen Zweck wurde der bestehende XFall Standard für den PoC als offene RESTful API weiterentwicklet und die dazugehörigen Integrationskomponenten und Entwicklerressourcen prototypisch bereitgestellt.

Ziel ist es aufzuzeigen, dass mit den zwei Säulen der föderalen Integrations- und Entwicklungsplattform und dem offenen Plattformansatz ein echter Mehrwert für die Entwicklung interoperabler und skalierbarer Lösungen generiert werden kann, um somit die Verwaltungsdigitalisierung in Deutschland grundlegend voranzutreiben. 

Bei einem positiven Ergebnis des Proof of Concepts wird angestrebt, die föderale Integrations- und Entwicklungsplattform als Gesamtansatz föderal umzusetzen und die XFall RESTful API sowie weitere APIs für die föderale Entwicklungsbereiche produktiv anzubieten.
