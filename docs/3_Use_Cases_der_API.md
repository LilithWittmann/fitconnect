# Anwendungsfälle

## Überblick über die Anwendungsfälle

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

**Beschreibung:** Der Sender überträgt mittels eines POST Request die Metadaten des Antrags an die Sender API und legt die `application` (Antrag) als Ressource an. Hierfür bekommt der Sender durch die API eine eindeutige `application-id`in der Response zugeteilt. Zudem werden alle weiteren zu übermittelnden Antragsbestandteile (`data`, `document`) auf Basis der Angaben in den Metadaten als Subressourcen angelegt und sind durch die `doc-id` aus den Metadaten adressierbar. Für diese Subressourcen überträgt der Sender die Inhalte per PUT. Nach Übermittlung aller Antragsbestandteile wird durch einen POST auf die `application` die vollständige Übertragung des Antrags bestätigt und damit der Antrag den Abholbereich des Zustellpunkts übermittelt.

![Application_Transfer] (../assets/images/use_case_documentation/application_transfer.png "Ablaufbeschreibung zur Uebertragung eines Antrags")

### Zustellstatus des abgegebenen Antrags abrufen

**Vorbedingung:** Die `application` wurde als Ressourcen angelegt und dem Sender liegt eine `application-id` vor.

**Ziel:** Den Zustellungsstatus des Antrags bis zur weiterverarbeitenden Stelle überwachen.

**Beschreibung:** Der Sender fragt per GET über die `application-id` den `status` der Antrags ab. Als Antwort bekommt dieser den aktuellen Status sowie die Statushistorie übersendet. Alle Statusübergänge sind als entsprechende Codes (`incomplete`, `queued`, `forwarded`, `delivered`) definiert.

## Anwendungsfälle für den Subscriber

### Zustellpunkt einrichten

**Vorbedingung:** Keine

**Ziel:** Es wird ein Zustellpunkt (`destination`) eingerichtet und verwaltet, über den der Subscriber Anträge empfangen kann. Hierdurch wird  ein Zugang für alle Sender eröffnet, der über die `destination-id` eindeutig adressierbar ist.

**Beschreibung:** Der Subscriber erstellt einen Zustellpunkt per POST und bekommt von der API eine eindeutige `destination-id`. Für diesen Zustellpunkt sind noch fachliche und technische Ansprechpartner zu definieren und das Schema der Inhaltsdaten zu definieren. Zusätzlich besteht die Möglichkeit, eine Callback URL zu definieren, über die der Zustelldienst den Subscriber über neue Anträge informieren kann.

### Benachrichtigungen über Anträge erhalten

**Vorbedingung:** Es wurden in den Zustellpunkten Callback URLs hinterlegt, die durch den XFall Zustelldienst erreichbar sind.

**Ziel:** Ziel ist, Benachrichtigungen über abholbereite Anträge zu empfangen. Diese Benachrichtigungen ersetzen ein konstantes Polling durch den Subscriber und entlasten damit die verfügbaren Hardware und Netzwerkressourcen.

**Beschreibung:** Bei der Benachrichtung nimmt der Subscriber die Rolle eines API Providers auf, indem dieser Benachrichtigungen empfängt. Der Zustelldienst sendet beim Vorliegen einer oder mehrer Anträge in einem Zustellpunkt an die Callback URL einen POST mit allen `application-id's` der abholbereiten Anträge.

### Anträge abrufen

**Vorbedingung:** Der Subscriber hat einen Zustellpunkt erstellt und einem oder mehreren Sendern die dazugehörige ´destination-id´ mitgeteilt.

**Ziel:** Ziel ist es, abgegebene und abholbereite Anträge abzurufen.

**Beschreibung:** 

