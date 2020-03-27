# Überblick über die XFall API

Willkomen auf der API Dokumentation für die XFall RESTful API. Zusammen mit der föderalen Integrations- und Entwicklungsplattform ermöglicht die XFall RESTful API es, dass Lösungsverantwortlichen und Entwicklern von OZG-Verfahren, ihre Verfahren schnell und wirtschaftlich in medienbruchfreie Antragsprozesse zu integrieren. 

> Entlastet von wiederkehrenden Integrationsherausforderungen, werden wertvolle Kapazitäten freigestellt, um skalierbare Innovationen und nutzerzentrierte Lösungen für Antragssteller und Sachbearbeitern voranzutreiben!

## Was ist die XFall RESTful API und was unterscheides diese vom bisherigen XFall Standard?

Die XFall RESTful API baut auf den bisherigen Konzepten und Erfahrungen des bestehenden IT-Planungsrats auf. Die übergreifende Zielstellung von XFall besteht darin, Anträge und Berichte, die aus den vorgelagerten Systemen (bspw. Onlineantragsdienste, Fachportal oder Berichtssysteme) erstellt werden, in die elektronische Verfahrensbearbeitung der Verwaltung zu übergeben. Ausgehend hiervon ist die XFall RESTful API keine einheitliche API, sondern besteht aus zwei dedizierten APIs für die Sender von Anträgen (`Application Sender API`) und die Empfänger von Anträgen (`Application Subscriber API`).

Bei der Entwicklung der XFall RESTful API wurde viele Konzepte mit Hinblick auf die Erfordernisse des Onlinezugangsgesetzes, dem EU-Single Digital Gateway sowie Anforderungen moderner digitaler Geschäftsmodelle grundlegend weiterentwickelt. 

Im Vergleich zum bisherigen XFall-Standard wird die XFall RESTful API setzt auf einen leichgewichtige REST-Architekturstil und um eine föderale Infrastruktur ergänzt:
- Eine dem "Lightweight Messagin Principle" folgende Integrationsplattform, die die jeweiligen XFall APIs anbietet und viele typische Integrationsherausforderungen für beide Seiten löst
- Eine zentrale Entwicklerplattform, die alle Informationen und Ressourcen für Anbindung an die XFall RESTful API bereitstellt.

### Überblick der Integrationsarchitektur

...

## In welchem Stand befindet sich XFall RESTful API und wann kann man die API nutzen?

Die Entwicklung und Bereitstellung der XFall RESTful API erfolgt im Rahmen des Proof of Concepts der zukünftig angedachten föderalen Integrations- und Entwicklungsplattform. Im Rahmen dessen wird ab dem zweiten Quartal 2020 interessierten Beteiligten möglich sein, einen Zugang zu der API-Dokumentation zu bekommen und für ihre Verwaltungsleistungen eine prototypische Anbindung auszutesten.

### Was ist die föderale Integrations- und Entwicklungsplattform und wozu dient der Proof of Concept?

#### Die föderale Integrations- und Entwicklungsplattform
Die föderale Integrations- und Entwicklungsplattform ist ein strategischer Ansatz, um die aktuellen Herausforderungen in der verteilten OZG Umsetzung zu adressieren. Sie soll den OZG-Umsetzungsverantwortlichen und Lösungsentwicklern eine Basis bereitstellen, um schnell und wirtschaftlich bundesweit nutzbare und interopable Lösungen für Verwaltungsleistungen zu entwickeln.

Die föderale Integrations- und Entwicklungsplattform baut auf zwei Säulen auf:
-	Leichtgewichtige Schnittstellen auf Basis etablierter Industriestandards sowie zentral bereitgestellte Integrationskomponenten, um wiederkehrende Integrationsherausforderungen im verteilten föderalen Vorgehen zu lösen oder zu minimieren.
-	Eine gemeinsame Entwicklerplattform und zentral bereitgestellter Entwicklungs- und Testwerkwerkzeuge, um die Entwicklung interoperabler Verfahren für die Antragsstellung und Antragsbearbeitung zu vereinfachen und zu beschleunigen. Hierbei sollen Ressourcen und Informationen zu allen gängigen föderalen Integrationsfällen und Basisdiensten für Softwareentwickler und Verfahrenverantwortliche in transparenter Weise gebündelt und zentral bereitgestellt werden.

Beide Säulen folgen der Philosophie einer offenen Plattform und leiten einen Kulturwandel in der Entwicklung digitaler Verwaltungslösungen ein: 
-	Der Staat stellt eine digitale Basis an Funktionen und Daten auf Basis offener Standards und Komponenten jedem frei zur Verfügung. 
-	Dies ermöglicht es allen gesellschaftlichen Akteuren (Behörden, Unternehmen, Non-Profit Organisationen, Bürger) neue digitale Lösungen und Innovationen frei erstellen. 
-	Die Lösungen können durch den Staat eingebunden, beauftragt oder eingekauft werden oder abseits des Staats im Rahmen neuer kommerzieller oder gesellschaftlicher Geschäftsmodelle eingebunden werden.

![FIEP_Strategic_Vision](https://raw.githubusercontent.com/fiep-poc/fiep-poc/documentation/assets/images/api_overview/FIEP_strategic_vision.png?token=AOHBJRMFXOHXXYUFKVCPVNC6Q5KM6 "Vision der föderalen Integrations- und Entwicklungsplattform")

#### Zielstellung des Proof of Concepts

Der Proof of Concept (PoC) soll wesentliche Grundprinzipien und Lösungsansätze der föderalen Integrations- und Entwicklungsplattform im Bereich der Antragsübermittlung praktisch zu erproben. Für diesen Zweck wird der bestehende XFall Standard für den PoC als offene RESTful-API weiterentwicklet und mit einer prototypischen Integrationsarchitektur und Entwicklungsplattform verknüpft.

Ziel ist es, mit der Anbindung echter Antragsdienste und Verfahrenssysteme im Rahmen unterschiedlicher Verwaltungsleistungen zu aufzuzeigen, dass mit den zwei Säulen der föderalen Integrations- und Entwicklungsplattform und dem offenen Plattformansatz, ein echter Mehrwert für die Entwicklung interoperabler und skalierbarer Lösungen generiert werden kann.


