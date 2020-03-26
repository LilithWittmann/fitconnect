# Status- und Fehlercodes

The beginning of an awesome article...

### Rückmeldungen zu clientseitig verursachten Fehlern

Zu einer Fehlermeldung, die durch den API-Client verursacht wurde (Kategorie 4XX), liefert die API über die Angabe Erroreine detailierte Rückmeldung zu einer nicht erfolgreichen Operation. Sie enthält folgende Angaben:


    code: integer - Fehlercode

    msg: string - Fehlermeldung

    ref: string - Referenz auf fehlerhafte Stelle

