# Verschlüsselte Übertragung

## Architektur

![FIT-Connect Architektur](https://raw.githubusercontent.com/fiep-poc/assets/fa582b1bf765cbe5059b5f22f100923da595d6f9/images/encryption/Architektur_PoC_einfach_2.svg "FIT-Connect Architektur")

Kern von FIT-Connect ist der Zustelldienst, der über die beiden APIs "Application Sender API" und "Application Subscriber API" den Absender (Sender) und Empfänger (Subscriber) eines Antrags verbindet.

## Vorgaben

Unter Berücksichtigung der Vorgaben des BSI in der Richtlinie [TR-02102-1](https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Publikationen/TechnischeRichtlinien/TR02102/BSI-TR-02102.html) wurden die [Liste der möglichen Algorithmen](https://www.iana.org/assignments/jose/jose.xhtml#web-signature-encryption-algorithms) eingeschränkt.

- Asymmetrisches Verschlüsselungsverfahren, um den "Content Encryption Key" zu verschlüsseln ("alg"): "RSA-OAEP-256"
- Symmetrisches Verschlüsselungsverfahren zur Verschlüsselung des Payloads ("enc"): "A128GCM", "A192GCM" oder "A256GCM"

## Konzept

### Aufbau der Übertragung

Eine Übertragung über FIT-Connect besteht aus einem Metadatensatz, optionalen Fachdaten und beliebig vielen (0-∞) Dokumenten (Anlagen). Da die Metadaten transportrelevante Informationen enthalten, werden diese immer unverschlüsselt übertragen. Bei aktivierter Verschlüsselung werden nur die Fachdaten und Anlagen verschlüsselt.

### Destination

Ein Antrag wird an eine Destination (Zielort) geschickt. Diese Destination legt der Empfänger über die "Application Subscriber API" an. Der Absender muss die ID der Destination kennen und kann dann Anträge über die "Application Sender API" an diese ID senden. Der Empfänger legt in der Destinatin fest, ob die Übertragung optional oder verpflichtend verschlüsselt werden muss. Hierzu enthält die Destination eine Liste von Schemas, aus denen der Absender eines auswählen muss. Diese Schemas enthalten unter anderem eine Angabe zum Encoding, über das eine Verschüsselung vorgegeben wird.

## Application Schema

Das Application Schema wurde in der Beta 7 um die Angabe "encoding" erweitert. Es kann drei verschiedene Werte annehmen: "plain", "base64" und "jwe".

### encoding: plain

"plain" ist der Defaultwert und entspricht der Arbeitsweise bis Beta 6. Hierbei werden die Fachdaten und Anlagen uncodierter Form übermittelt.

#### Beispiel

```json
{"test":true,"hello":"world"}
```

### encoding: base64

"base64" legt fest, dass die Daten base64-codiert übertragen werden.

#### Beispiel

```
eyJ0ZXN0Ijp0cnVlLCJoZWxsbyI6IndvcmxkIn0K
```

### encoding: jwe

Beim Encoding "jwe" werden die Fachdaten und Anlagen mit der JSON Web Encryption (RFC 7516) verschlüsselt.

#### Beispiel

```
eyJlbmMiOiJBMjU2R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.nlXGAufYH36IABDy0En0LXEhGfC2
0IZSSchs27ADalHpRoTZKfXhc7hcMk8Y9V8yTP0jYbmrq6NtEg-QS2O5TQFD9Hluhpb631PBgKjPXHYX
1Y6iUcR1sXxSUPjePi8F8PcZUZuUJLnhz6myyc9scdAq9BXG2cDJVgkfLI8eZdrqnrY24Hh32_7d5OKL
FSpSDrBlqfyQuY8Wbs2h8Wy4Z4hwT1aWDO7b-SqJA181hUbNcF_rR4Mze3Fdtu-3uOIQYgLBBRmN1ZHD
Lk0EKNCI4B8MyDKLGPoM0ZomV5lVwVWjAMRI4CgQkIQ9rnm-Adof-GbegQL3yJSoNIWRWgzCnZBYZ638
QgPllCMVW3WvEVvsgj0Hj16PbofqXTQ5S73LINfP6FZawfC0yMrYjSV_N2L0Lkp2KI3BkJcy-PcFhBnh
wu2IsJGAlyDRCnXdVqig8m5yLHuSMQTpLW69LzPEskfsjhnNDR-CEBZpicjMfc-4CL6U7E7YoGc_99Dz
E5U5._JfqyKH23GiKsnDW.ZtMMjZ3GgcgHss8qbFRhrjl4L0kAfbco-oXICkk.VBHJ00FyDTYjOA_OYf
iz5g
```

## Application Subscriber API

Über die Application Subscriber API werden die Destinations verwaltet, an die die Anträge gesenet werden. Eine Destination enthält eine Liste von Schemas, welche Formate der Empfänger akzeptiert. Um sicherzustellen, dass immer eine verschlüsselte Übertragung stattfindet muss jedes dieser Schemas bei der Eigenschaft "encoding" den Wert "jwe" enthalten. Sofern mindestens ein verschlüsseltes Schema angeboten wird, muss auch mindestens ein öffentlicher Schlüssel angeboten werden.

Der Empfänger kann in der Destination mehrere Schemas und mehrere öffentliche Schlüssel hinterlegen. Der Absender sucht sich davon für die Übertragung ein Schema udn einen öffentlichen Schlüssel aus. Es wird empfohlen, genau ein Schema und genau einen öffentlichen Schlüssel anzubieten.

Es ist geplant, dass die hinterlegten öffentlichen Schlüssel so organisiert werden, dass ein kontrolliertes Key-Rollover stattfinden kann. Dazu werden zu den Schlüsseln die Gültigkeitszeiträume ergänzt.

#### Beispiel

```json
{
  "publicKeys": {
    "keys": [
      {
        "kty": "RSA",
        "e": "AQAB",
        "use": "enc",
        "kid": "c3bb7326-c498-4027-85f4-b102d0c69ebb",
        "n": "zcKRdaV9RjpekpyYqlbXQRhNgs_L2RwerlZKJJWdSaQWCD90yHk-bOlG6gjadalWpL
OF9aOPqqviVKRO2Gq-_mkdBJVuX2pLcx7IuxbEFaFRi81CXPUB3rbKiV_L5bQ2U9_m3X97wV72bkV07R
IJgH9QfCxcGwohN9hU_qLNMfrbwiwOF2WWgxL-x3NpnKhmWiXmIH0b17NH0NTeLTkXnKPWvFmTd_fCwW
Y-Z3L3hQik170z2R-hT4SpQOHN-UhXAbZ-SOER3roGObjHj3K8scFOhyOfd0wUPYP8gX_Lz6nR4AU-Ty
qqfpJ_kaeJdcWbH1z0HWXAenNxTGHOJeyYJGCjctphlSUwJVqrrtNAq15ilFWCw38vvOHbnt8WIqfE-j
hjtz80el2ieb4wQwcwFLGefKcnaNs5K82bIBXF993RqKKKtJfimz8KJAIPYsxpJ9swx4voPjUAdV99Ek
ofh__YzMgEdzoIJ6_pd3nojtm1vRKfcKWiT4Z09DW8qoF1"
      }
    ]
  },
  "schemas": [
    {
      "schemaSource": "none",
      "mimeType": "json",
      "encoding": "jwe"
    },
    {
      "schemaSource": "none",
      "mimeType": "xml",
      "encoding": "jwe"
    }
  ],
  "destinationId": "b444a551-74af-4a98-aa65-d1ffccd385d1"
}
```

## Application Sender API

Der Absender muss die Destination-ID vorliegen haben und erfagt über die Application Sender API die Informationen zur Destination. Diesen entnimmt er die Liste der möglichen Schemas und wählt eines aus. Sofern es sich um eine verschlüsselte Übertragung handelt, wählt er einen öffentlichen Schlüssel.

Derzeit muss die Destination-ID manuell vom Empfänger an den Absender übergeben werden. Dies soll in Zukunft automatisch mithilfe bestehender Mechanismen, z.B. XZufi oder DVDV passieren.

## Übertragungsvarianten

Das gewählte Schema wird in den Metadaten des Antrags (Application Metadata) eingetragen und legt die Art der Übertragung fest. Im folgenden Beispiel wird ein verschlüsselter Fachdatensatz im JSON-Format und ein PDF-Dokument übertragen.

**Hinweis:** Das Encoding der Anlagen ist an das Encoding der Fachdaten gebunden. Alle Anlagen müssen mit dem gleichen Encoding wie die Fachdaten übertragen werden. Hier im Beispiel also verschlüsselt.

#### Beispiel (Metadaten)

```json
{
  "contentStructure": {
    "data": {
      "schema": {
        "schemaSource": "none",
        "mimeType": "json",
        "encoding": "jwe"
      }
    },
    "docs": [
      {
        "size": 13046,
        "purpose": "attachment",
        "docId": "1",
        "mimeType": "application/pdf"
      }
    ]
  },
  "applicationId": "6f7b00f1-2f0c-46da-93c9-ca020aa1758f"
}
````

#### Beispiel (Fachdaten)

```
eyJlbmMiOiJBMjU2R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.yTSVS7re6hZKO46aDriHrRFOyc5-
3TIIrvcKUf2qAfGdH7InufWPCrDyEnazSDI7HtOa5X2MU3iUnmmiEuP-Lef76xTPv2lmL4_lyhW5D8zq
7zbrIaIaVhtg7ekF1r9Oy9nLsEBQWLD4EWda2PfAibV7iQbOVMn1rVk4DzKtCykj5RSrH96i-lbPVFl-
Xw_E2G5XsL0gOHrdbAsjTF1h67bvh2hnojc9SH1GnlD0TlUO30n0GKLgC7tNNiLGtNrRo8ih3LUWYo-m
34Q6NGjaNTycHnWMYZzXHbIcBzYr6WLTsrB07rKXEyrHGLaRL88y2c-ACyEzpgv4qR5DAp98Su2u45ar
pfGU_7HxX4d-PLEoDfIRnh32nprarbaIesj9Ppgiu7QciWRApcyszk0a5rzZ7Dk_6-ydMfD92H2p3tdt
OcFhj3XGUshVKec2nRhtCZPOMPTIjxFpozsiRetjZo9LFHzRcvr1eSS_hpteKJ3ltioY9nzt1IX2JqQm
TGtY.VGOCnGM9LEZP5mUO.LQeKj4SKqsUNsBp4ZRN_56QbS8MQ01YTzRVFStk.Z0YMEua9kvCV7LkeJH
kprA
````

### encoding: plain

Bei der Übertragung der Fachdaten muss der passende Content-Type gesetzt werden, also "application/json" bzw. "application/xml". Alternativ ist "text/json" und "text/xml" auch zulässig. Bei der Übertragung der Anlage ist der in den Metadaten angegebene Datentyp (z.B. "application/pdf") zu verwenden.

#### Beispiel

```
PUT /delivery-service-beta7/sender/destinations/e1009dea-d97e-4104-b389-bf653d8bd30e/applications//data HTTP/1.1
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjM1ZTM2Nzk2LTM1NDAtNDUwMy1iYT...
 
{"test":true,"hello":"world"}
```

### encoding: base64

Bei der Übertragung der Fachdaten und Anlagen wird der Content-Type "text/plain" für Base64 verwendet.

#### Beispiel

```
PUT /delivery-service-beta7/sender/destinations/e1009dea-d97e-4104-b389-bf653d8bd30e/applications//data HTTP/1.1
Content-Type: text/plain
Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjM1ZTM2Nzk2LTM1NDAtNDUwMy1iYT...
 
eyJ0ZXN0Ijp0cnVlLCJoZWxsbyI6IndvcmxkIn0K
```

### encoding: jwe

Bei der Übertragung der Fachdaten und Anlagen wird der Content-Type "application/jose" (Achtung: jose, nicht json) verwendet.

#### Beispiel

```
PUT /delivery-service-beta7/sender/destinations/e1009dea-d97e-4104-b389-bf653d8bd30e/applications//data HTTP/1.1
Content-Type: application/jose
Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IjM1ZTM2Nzk2LTM1NDAtNDUwMy1iYT...
 
eyJlbmMiOiJBMjU2R0NNIiwiYWxnIjoiUlNBLU9BRVAtMjU2In0.yTSVS7re6hZKO46aDriHrRFOyc5-
3TIIrvcKUf2qAfGdH7InufWPCrDyEnazSDI7HtOa5X2MU3iUnmmiEuP-Lef76xTPv2lmL4_lyhW5D8zq
7zbrIaIaVhtg7ekF1r9Oy9nLsEBQWLD4EWda2PfAibV7iQbOVMn1rVk4DzKtCykj5RSrH96i-lbPVFl-
Xw_E2G5XsL0gOHrdbAsjTF1h67bvh2hnojc9SH1GnlD0TlUO30n0GKLgC7tNNiLGtNrRo8ih3LUWYo-m
34Q6NGjaNTycHnWMYZzXHbIcBzYr6WLTsrB07rKXEyrHGLaRL88y2c-ACyEzpgv4qR5DAp98Su2u45ar
pfGU_7HxX4d-PLEoDfIRnh32nprarbaIesj9Ppgiu7QciWRApcyszk0a5rzZ7Dk_6-ydMfD92H2p3tdt
OcFhj3XGUshVKec2nRhtCZPOMPTIjxFpozsiRetjZo9LFHzRcvr1eSS_hpteKJ3ltioY9nzt1IX2JqQm
TGtY.VGOCnGM9LEZP5mUO.LQeKj4SKqsUNsBp4ZRN_56QbS8MQ01YTzRVFStk.Z0YMEua9kvCV7LkeJH
kprA
```
