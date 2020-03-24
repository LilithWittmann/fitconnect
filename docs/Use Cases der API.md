# Use Cases der XFall APIs

Die übergreifende Zielstellung der XFall APIs besteht darin, Anträge und Berichte, die aus den vorgelagerten Systemen (bspw. Onlineantragsdienste, Fachportal oder Berichtssysteme) in die elektronische Verfahrensbearbeitung der Verwaltung zu übergeben.

Um diese übergreifende Zielstellung zur erfüllen, werden über die Sender-API und Subscriber-API den Sender und Empfänger von Anträge folgende Anwendungsfälle zur Verfügung gestellt:

![Application_Transfer](https://raw.githubusercontent.com/fiep-poc/fiep-poc/documentation/assets/images/use_case_documentation/Use_Case_Diagramm.png?token=AOHBJRKJHOP6P3QZ4BKPMXK6QNDHU "Use Case Diagramm der XFall APIs")

## Systematik und Legende der verwendeten BPMN Symbole bei Anwendungsfallabläufen

### Aktivität

**(Platzhalter Grafik)**

Beschreibt eine Tätigkeit innerhalb einer Prozessablaufs.

### Aktivität mit multiplen parallelen Instanzen

(Platzhalter Grafik)

Beschreibt eine Tätigkeit innerhalb einer Prozessablaufs, die ab dem aktivierungszeitpunkt mehrfach parallel durchgeführt werden kann.

### Exclusive Gateways

**(Platzhalter Grafik)**

Ein Entscheidungspunkt innerhalb des Prozessablaufs im Sinne einer ODER Entscheidung. Es wird nur der weitere Prozessablauf weiterverfolgt, der dem Entscheidungsergebnis entspricht.

### Parallel Gateways

**(Platzhalter Grafik)**

Parallelisierungspunkt innerhalb des Prozessablauf. Prozessflüsse nach dem parallelen Gateway parallel durchgeführt.

## Anwendungsfälle für Subscriber

### Antrag bei einem Zustellpunkt abgeben

Ziel: 

![Application_Transfer] (../assets/images/use_case_documentation/application_transfer.png "Ablaufbeschreibung zur Uebertragung eines Antrags")

