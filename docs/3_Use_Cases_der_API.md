# Anwendungsfälle

## Überblick über die Anwendungsfälle

![Application_Transfer](https://raw.githubusercontent.com/fiep-poc/assets/master/images/use_case_documentation/use_case_diagramm.png "Use Case Diagramm der XFall APIs")

## Anwendungsfälle für den Sender

### Antrag bei einem Zustellpunkt abgeben

**Vorbedingung:** Es muss zuvor die `destination-id` eines gültigen Zustellpunkts ermittelt worden sein. Im Rahmen des PoC erfolgt die Übermittlung mittels bilateraler Absprachen und Kanäle zwischen dem Subscriber und Sender. 

**Ziel:** Alle Bestandteile des Antrags werden in den Abholbereich des addressierten Zustellpunkts übergeben und liegen dort zur Abholung durch den Subscriber bereit.

**Beschreibung:** Der Sender überträgt mittels eines POST die Metadaten des Antrags an die Sender API und legt damit den Antrag (`application`) als Ressource sowie die Fachdaten und die in den Metadaten angegebenen Anlagen als Subressourcen an. Für den Antrag bekommt der Sender eine eindeutige `application-id`in der Response mitgeteilt. Der Sender kann anschließend alle Bestandteile des Antrags an die jeweiligen Endpunkte per PUT übermitteln und die Übergabe an in den Abholbereich des Subscribers über einen abschließenden Commit initialisieren.

![Application_Transfer](https://raw.githubusercontent.com/fiep-poc/assets/master/images/use_case_documentation/application_transfer.png "Ablaufbeschreibung zur Uebertragung eines Antrags")

### Zustellstatus des abgegebenen Antrags abrufen

**Vorbedingung:** Der Antrag wurde als Ressource angelegt und dem Sender liegt eine `application-id` vor.

**Ziel:** Den Zustellungsstatus des Antrags abschließend überwachen.

**Beschreibung:** Der Sender fragt per GET über die `application-id` den `status` der Antrags ab. Als Antwort bekommt dieser den aktuellen Status sowie die Statushistorie übersendet. Diese Statusübergänge sind über standardisierte Codes (`incomplete`, `queued`, `forwarded`, `delivered`) definiert.

## Anwendungsfälle für den Subscriber

### Zustellpunkt einrichten

**Vorbedingung:** Keine

**Ziel:** Es wird ein Zustellpunkt (`destination`) eingerichtet und verwaltet, über den der Subscriber Anträge empfangen kann. Hierdurch wird grundsätzlich ein Zugang für alle Sender eröffnet, die die `destination-id` kennen.

**Beschreibung:** Der Subscriber erstellt einen Zustellpunkt per POST und bekommt von der API eine eindeutige `destination-id`. Für diesen Zustellpunkt sind fachliche und technische Ansprechpartner sowie das Schema der Fachdaten zu definieren. Zusätzlich besteht die Möglichkeit, eine Callback URL zu hinterlegen, über die der Zustelldienst den Subscriber über neue Anträge informieren kann.

### Benachrichtigungen über Anträge erhalten

**Vorbedingung:** Es wurden in den Zustellpunkten Callback URLs hinterlegt, die durch den XFall Zustelldienst erreichbar sind.

**Ziel:** Ziel ist, Benachrichtigungen über abholbereite Anträge zu empfangen. Diese Benachrichtigungen ersetzen ein konstantes Polling durch den Subscriber und entlasten damit die verfügbaren Hardware und Netzwerkressourcen.

**Beschreibung:** Für die Benachrichtung übernimmt der Subscriber die Rolle eines API Providers, indem dieser Requests vom Zustelldienst empfängt. Der Zustelldienst sendet beim Vorliegen einer oder mehrerer Anträge einen POST Request mit allen `application-id's` der abholbereiten Anträge an die hinterlegte Callback URL.

### Anträge abrufen

**Vorbedingung:** Der Subscriber hat einen Zustellpunkt erstellt und die dazugehörige `destination-id` einem oder mehreren Sendern mitgeteilt und es liegt einer oder mehrere Anträge zum abholen bereit.

**Ziel:** Ziel ist es, abholbereite Anträge abzurufen.

**Beschreibung:** Der Subscriber kann die Metadaten aller vorliegenden Anträge mit einem Request abrufen oder die Metadaten eines spezifischen Antrags abrufen, falls die `application-id` durch eine Callback Benachtigung bereits mitgeteilt wurde. Nach dem Abruf der Metadaten besteht die Möglichkeit, die Fachdaten (`data`) sowie die  Anlagen (`document`) abzurufen. Nach dem Abruf aller gewünschten Bestandteile des Antrags, muss der vollständige Abruf durch den Subscriber bestätigt werden. Diese Bestätigung hat zur Folge, dass innerhalb einer definierten Frist der Antrag unwiederruflich gelöscht wird. 

![Application_Retrieval](https://raw.githubusercontent.com/fiep-poc/assets/master/images/use_case_documentation/application_retrieval.png "Ablaufbeschreibung zum Abruf eines Antrags")

### Legende der verwendeten BPMN Symbole

#### Start- und Endereignisse

![Start_Event](https://raw.githubusercontent.com/fiep-poc/assets/master/images/use_case_documentation/BPMN%20Legend/Start_Event.png "Startereignis")

![End_Event](https://raw.githubusercontent.com/fiep-poc/assets/master/images/use_case_documentation/BPMN%20Legend/End_Event.png "Endereignis")

Startet oder beendet einen Prozessablauf.

#### Aktivität

![Activity](https://raw.githubusercontent.com/fiep-poc/assets/master/images/use_case_documentation/BPMN%20Legend/Activity.png "Aktivität")

Eine Tätigkeit innerhalb einer Prozessablaufs.

#### Aktivität mit mehrfachen parallelen Instanzen

![Activity_Multi_Instance](https://raw.githubusercontent.com/fiep-poc/assets/master/images/use_case_documentation/BPMN%20Legend/Activity_Multi_Instance.png "Aktivität mit mehrfachen parallelen Instanzen")

Eine Tätigkeit innerhalb einer Prozessablaufs, die ab dem aktivierungszeitpunkt mehrfach parallel durchgeführt werden kann.

#### Exclusive Gateway

![Exclusive Gateway](https://raw.githubusercontent.com/fiep-poc/assets/master/images/use_case_documentation/BPMN%20Legend/Exclusive%20Gateway.png "Exklusives Gateway")

Ein Entscheidungspunkt innerhalb des Prozessablaufs im Sinne einer ODER Entscheidung. Es wird nur der weitere Prozessablauf weiterverfolgt, der dem Entscheidungsergebnis entspricht.
#### Parallel Gateway

![Parallel Gateway](https://raw.githubusercontent.com/fiep-poc/assets/master/images/use_case_documentation/BPMN%20Legend/Parallel_Gateway.png "Paralleles Gateway")

Parallelisierungspunkt innerhalb des Prozessablauf. Prozessflüsse nach dem parallelen Gateway parallel durchgeführt.
