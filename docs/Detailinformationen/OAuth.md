# OAuth Details

## API Aufruf mit wget

Sie können auch mit dem Kommandozeilentool "wget" testen. In diesem Beispiel wird die Liste aller Destinations abgerufen:

```bash
wget --quiet --output-document - \
  --method GET \
  --timeout=0 \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer 5eadf042ef434913a5724d5e5ce38bc0' \
   'https://subscriber.fiep-poc.de/beta6/subscriber-c94ae37e-dcc5-345e-a530-8651bdfa5f2c/destinations'
```

## Manueller OAuth 2.0 Fluss

Ein Entwickler hat in der Regel keine OAuth 2.0 Funktion direkt zur Verfügung. Daher müssen die Schritte einzeln durchgeführt werden. Um Zugriff auf die APIs zu erhalten muss Ihr Client zuerst einen OAuth Zugriff machen, um mit “client_id“, “client_secret“ ein Zugriffs-Token zu erhalten.

Die URL für den OAuth Zugriff lautet:
https://oauth.fiep-poc.de/invoke/pub.apigateway.oauth2/getAccessToken

Folgende Query Parameter sind dabei mitzugeben:
- grant_type:	client_credentials (fix)
- client_id: c1bbee16-fae1-4dc1-b0c6-b75a02b359b0 (Beispiel)
- client_secret:	91e7f6dd-5567-456f-a8be-aac10237c4c8 (Beispiel)
- scope: subscriber-c94ae37e-dcc5-345e-a530-8651bdfa5f2c:manage (Beispiel)

<!-- theme: warning -->
> **Hinweis zu den Token:**
> Für den Zugriff auf die beiden APIs sind zwei unterschiedliche Scopes erforderlich. Diese enthalten beide Ihre Anwender-ID und könnten beispielsweise wie folgt aussehen:
> - Für die Application Subscriber API: **subscriber-**c94ae37e-dcc5-345e-a530-8651bdfa5f2c:manage
> - Für die Application Sender API: **sender-**c94ae37e-dcc5-345e-a530-8651bdfa5f2c:manage
> 
> Sie können beim holen des Access Token das richtige Scope einsetzen oder ein Token für beide Scopes/APIs beziehen. Dazu schreiben Sie beide Scopes mit einem Leerzeichen dazwischen hintereinander:
> 
> `subscriber-c94ae37e-dcc5-345e-a530-8651bdfa5f2c:manage sender-c94ae37e-dcc5-345e-a530-8651bdfa5f2c:manage`
> 
> ![Zwei Scopes](https://raw.githubusercontent.com/fiep-poc/assets/master/images/oauth/18_zwei_scopes.png)
> 
> Bitte beachten Sie, dass Sie statt "c94ae37e-dcc5-345e-a530-8651bdfa5f2c" Ihre Anwender-ID einsetzen müssen.

Ein Aufruf mit dem Werkzeug "wget" sieht z.B. wie folgt aus:

```bash
wget --quiet --output-document - \
  --method GET \
   'https://oauth.fiep-poc.de/invoke/pub.apigateway.oauth2/getAccessToken?grant_type=client_credentials&client_id=c1bbee16-fae1-4dc1-b0c6-b75a02b359b0&client_secret=91e7f6dd-5567-456f-a8be-aac10237c4c8&scope=subscriber-c94ae37e-dcc5-345e-a530-8651bdfa5f2c:manage'
```

Alternativ kann der Request auch per POST durchgeführt werden:

```bash
wget --quiet --output-document - \
  --post-data 'grant_type=client_credentials&client_id=c1bbee16-fae1-4dc1-b0c6-b75a02b359b0&client_secret=91e7f6dd-5567-456f-a8be-aac10237c4c8&scope=subscriber-c94ae37e-dcc5-345e-a530-8651bdfa5f2c:manage' \
  'https://oauth.fiep-poc.de/invoke/pub.apigateway.oauth2/getAccessToken'
```

Die Antwort sieht in etwa wie folgt aus:

```json
{
  "access_token": "0bd226153b394d209a9d57bd7a42ee70",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

Der Wert für "access_token" wird dann als Header Parameter "Authorization" zusammen mit dem Text "Bearer" verwendet.

Hier wieder ein Beispiel mit dem Tool "wget":

```bash
wget --quiet --output-document - \
  --method GET \
  --header 'Authorization: Bearer 0bd226153b394d209a9d57bd7a42ee70' \
   'https://subscriber.fiep-poc.de/beta6/subscriber-c94ae37e-dcc5-345e-a530-8651bdfa5f2c/destinations'
```
