# Überblick über XFall

Die übergreifende Zielstellung von XFall besteht darin, Anträge und Berichte, die aus den vorgelagerten Systemen (bspw. Onlineantragsdienste, Fachportal oder Berichtssysteme) erstellt werden, in die elektronische Verfahrensbearbeitung der Verwaltung zu übergeben.

Um diese übergreifende Zielstellung zur erfüllen, werden dem Sender eines Antrags (`Sender`) und Empfänger eines Antrags (`Subscriber`) dedizierte APIs bereitgestelt, um Anträge bzw. Berichte beim XFall API-Gateway abzugeben bzw. abzuholen.

Das XFall API-Gateway ist ein Teilbereich der zukünftigen föderalen Integrations- und Entwicklungsplattform und wird aktuell als Proof of Concept umgesetzt.

### Welches Problem löst das XFall API-Gateway bzw. die dahinliegende Integrationsinfrastruktur?

...

### Überblick der Integrationsarchitektur

...


### Was bedeutet ist die föderale Integrations- und Entwicklungsplattform und wozu dient der Proof of Concept?

#### Die föderale Integrations- und Entwicklungsplattform
Die föderale Integrations- und Entwicklungsplattform ist ein strategischer Ansatz, um die aktuellen Herausforderungen in der verteilten OZG Umsetzung zu adressieren. Sie soll den Umsetzungsverantwortlichen und Lösungsentwicklern in der OZG-Verantwortlichen einen transparenten Rahmen bieten, um schnell und wirtschaftlich bundesweit nutzbare Lösungen für Verwaltungsleistungen zu entwickeln.

Die föderale Integrations- und Entwicklungsplattform baut auf zwei Säulen auf:
-	Leichtgewichtige Schnittstellen auf Basis etablierter Industriestandards sowie zentral bereitgestellte Integrationskomponenten, um wiederkehrende Integrationsherausforderungen im verteilten föderalen Vorgehen zu lösen oder zu minimieren.
-	Eine gemeinsame Entwicklerplattform und zentral bereitgestellter Entwicklungs- und Testwerkwerkzeuge, um die Entwicklung interoperabler Verfahren für die Antragsstellung und Antragsbearbeitung zu vereinfachen und zu beschleunigen. Hierbei sollen Ressourcen und Informationen zu allen gängigen föderalen Integrationsfällen und Basisdiensten für Softwareentwickler und Verfahrenverantwortliche in transparenter Weise gebündelt und zentral bereitgestellt werden.

Beide Säulen folgen der Philosophie einer offenen Plattform und leiten einen Kulturwandel in der Entwicklung digitaler Verwaltungslösungen ein: 
-	Der Staat stellt eine digitale Basis an Funktionen und Daten auf Basis offener Standards und Komponenten jedem frei zur Verfügung. 
-	Dies ermöglicht es allen gesellschaftlichen Akteuren (Behörden, Unternehmen, Non-Profit Organisationen, Bürger) neue digitale Lösungen und Innovationen frei erstellen. 
-	Die Lösungen können durch den Staat eingebunden, beauftragt oder eingekauft werden oder abseits des Staats im Rahmen neuer kommerzieller oder gesellschaftlicher Geschäftsmodelle eingebunden werden.

![FIEP_Strategic_Vision](https://raw.githubusercontent.com/fiep-poc/fiep-poc/documentation/assets/images/quick_reference/application_structure.png?token=AOHBJROKKDX4MECV4WW6IKC6Q4ZYS "Vision der föderalen Integrations- und Entwicklungsplattform")

#### Zielstellung des Proof of Concepts

Der Proof of Concept (PoC) soll wesentliche Grundprinzipien und Lösungsansätze der föderalen Integrations- und Entwicklungsplattform im Bereich der Antragsübermittlung praktisch zu erproben. Für diesen Zweck wird der bestehende XFall Standard für den PoC als offene RESTful-API weiterentwicklet und mit einer prototypischen Integrationsarchitektur und Entwicklungsplattform verknüpft.

Ziel ist es, mit der Anbindung echter Antragsdienste und Verfahrenssysteme im Rahmen unterschiedlicher Verwaltungsleistungen zu aufzuzeigen, dass mit den zwei Säulen der föderalen Integrations- und Entwicklungsplattform und dem offenen Plattformansatz, ein echter Mehrwert für die Entwicklung interoperabler und skalierbarer Lösungen generiert werden kann.