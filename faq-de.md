Deutsch &bull; [English](faq-en.md)

# FAQ

# OCPP

## [Wie man die Verbindung aufbaut](ocpp-de.md) 

## Wie mann die Transaction startet ohne Authorisierung mit RFID Karte
Um eine Start Transaktion zu starten wird die Anfrage RemoteStartTransaction.req verwendet. Damit startet der Ladevorgang.

### RemoteStartTransaction

| FELD NAME | FELD TYP | KARTE | BESCHREIBUNG |
| ----------- | ------------- | ---------- | ------------------------------------- |
| connectorId | integer | 0..1 | Optional. Nummer des Verbinders mit der die Transaktion gestartet werden soll. connectorId SHALL be > 0 |
| idTag | IdToken | 1..1 | Notwendig. Der Identifiezierer den der Ladepunkt für den Beginn einer Transaktion verwenden muss.
| chargingProfile | ChargingProfile | 0..1 | Optional. Lade Profil welches der Ladepunkt verwenden soll für die angefragte Transaktion ChargingProfilePurpose MUSS auf TxProfile gesetzt sein |

## Eine Anfrage mit RemoteStartTransaktion welche charginProfile beinhaltet is derzeit noch nicht implementiert und es muss somit eine Seperate Anfrage mit SetChargingProfile.req gesendet werden.

### SetChargingProfile.req

| FELD NAME | FELD TYPE | KARTE | BESCHREIBUNG |
| ----------- | ------------- | ---------- | ------------------------------------- |
| connectorId | integer | 1..1 | Notwendig.  Der Verbinder für welches das Lade Profil gilt. Wenn die connectorID = 0 dann gilt das limit für den Charger allgemein.|
| csChargingProfiles | ChargingProfile | 1..1 | Notwendig. Das Lade Profil welches auf dem Ladepunkt gesetzt wird|


### RemoteStopTransaction

Um eine Stop Transaktions Anfrage zu senden muss RemoteStopTransaction.req. verwendet werden. Hiermit wird das Laden gestoppt.

| FELD NAME | FELD TYP | KARTE | BESCHREIBUNG |
| ----------- | ------------- | ---------- | ------------------------------------- |
| transactionId | integer |  1..1 | Notwendig. Der Identifizierer welcher für die Transaktion mit dem Ladepunkt verwendet wird.|





# API 

## [Alle API Keys in Verwendung](apikeys-de.md)

## How to get started with API. 
  ### [Cloud API verwenden](cloudapi-de.md)
  ### [Grid API verwenden](gridapi-de.md)
  ### [http API verwenden](http-de.md)

  ### Konfiguration des physichen Tasters auf dem Ladepunkt
    https://000001.api.v3.go-e.io/api/set?token=myapitoken&clp=[6,10,12,14,16]
TDer Taster wird verwendet um zwischen biszu 5 verschiedenen maximla Ladeströmen zu wechslen.

|FELD NAME | R/W | TYP | KATEGORY | BESCHREIBUNG |
| ----------- | ------------- | ------ | ---- | ------------------------------------- |
| clp | R/W | array | Config | Derzeite Liste an Strömen, maximum 5 Einträge

