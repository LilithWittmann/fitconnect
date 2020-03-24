# Use Cases der XFall APIs

## Überblick

Die übergreifende Zielstellung der XFall APIs besteht darin, Anträge und Berichte, die aus den vorgelagerten Systemen (bspw. Onlineantragsdienste, Fachportal oder Berichtssysteme) in die elektronische Verfahrensbearbeitung der Verwaltung zu übergeben.

Um diese übergreifende Zielstellung zur erfüllen, werden über die Sender-API und Subscriber-API den `Sender` (Sender eines Antrags an einen Zustellpunkt) und `Subscriber` (Empfänger eines Antrags am Zustellpunkt) von Anträge folgende Anwendungsfälle zur Verfügung gestellt:

![Application_Transfer](https://raw.githubusercontent.com/fiep-poc/fiep-poc/documentation/assets/images/use_case_documentation/Use_Case_Diagramm.png?token=AOHBJRKJHOP6P3QZ4BKPMXK6QNDHU "Use Case Diagramm der XFall APIs")



### Legende der verwendeten BPMN Symbole bei Anwendungsfallabläufen

#### Aktivität

**(Platzhalter Grafik)**

Eine Tätigkeit innerhalb einer Prozessablaufs.

#### Aktivität mit multiplen parallelen Instanzen

(Platzhalter Grafik)

Eine Tätigkeit innerhalb einer Prozessablaufs, die ab dem aktivierungszeitpunkt mehrfach parallel durchgeführt werden kann.

#### Exclusive Gateways

**(Platzhalter Grafik)**

Ein Entscheidungspunkt innerhalb des Prozessablaufs im Sinne einer ODER Entscheidung. Es wird nur der weitere Prozessablauf weiterverfolgt, der dem Entscheidungsergebnis entspricht.

#### Parallel Gateways

**(Platzhalter Grafik)**

Parallelisierungspunkt innerhalb des Prozessablauf. Prozessflüsse nach dem parallelen Gateway parallel durchgeführt.

## Anwendungsfälle für den Sender

### Antrag bei einem Zustellpunkt abgeben

**Vorbedingung:** Es muss zuvor die `destination-id` eines gültigen Zustellpunkts ermittelt worden sein. Zum aktuellen Zeitpunkt wird dieser über einen persönlichen Kontakt zwischen dem Subscriber und den Sendern übermittelt. 

**Ziel:** Alle Bestandteile des Antrags sind in den Abholbereich des addressierten Zustellpunkts übergeben worden und liegen dort zur Abholung des Subscribers bereit.

**Beschreibung:** Der Sender überträgt mittels eines POST Request die Metadaten des Antrags an die Sender API und legt die `application` (Antrag) als Ressource an. Zudem werden alle weiteren zu übermittelnden Antragsbestandteile (`data`, `document`) auf Basis der Angaben in den Metadaten als Subressourcen angelegt und sind durch die doc-id aus den Metadaten adressierbar. Für diese Subressourcen überträgt der Sender die Inhalte per PUT. Nach Übermittlung aller Antragsbestandteile wird durch einen POST auf die `application` die vollständige Übertragung des Antrags bestätigt und damit der Antrag den Abholbereich des Zustellpunkts übermittelt.

![Application_Transfer] (../assets/images/use_case_documentation/application_transfer.png "Ablaufbeschreibung zur Uebertragung eines Antrags")

