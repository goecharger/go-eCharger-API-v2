 Deutsch &bull; [English](mqtt-en.md)

# MQTT

[Die API Keys](apikeys-de.md) können über MQTT gelesen und geschrieben werden. Ab Firmware 051.5 muss das Schreiben jedoch extra erlaubt werden, da es ab da nicht mehr standardmäßig erlaubt ist. MQTT kann über die App oder die [http API](http-de.md) aktiviert werden.

Ein mqtt topic prefix wurde neulich implementiert, mit dem kann eingestellt werden, auf welchen topics der Charger lauscht und veröffentlicht.

## Über die App die MQTT Verbindung aktivieren und prüfen

Unten im Tab "Internet", dann "Erweiterte Einstelluingen" im Menü anwählen, dann ganz unten bei MQTT

<img src="screenshots/mqtt-app-enable.png?raw=true" width="200" />

**Warnung:** Verwenden Sie die voreingestellte test Broker url wirklich nur für kurze Tests und nicht im Dauerbetrieb, da der Charger sonst von Fremden aus dem Internet gesehen und gesteuert werden kann. Es kann das konfigurierte WLAN gelöscht oder auch ein Neustart veranlasst werden.

## Über die http API die MQTT Verbindung aktivieren und prüfen

Die Chargers verfügen über API Keys zum Konfigurieren und Prüfen der MQTT Verbindung. Diese API Keys können mit der http api verwendet werden.

Beispiel: http://192.168.0.77/api/set?mce=true&mcu=mqtt://mqtt.server:1234/

| api key | Beschreibung                 | Datentyp | R?W? | Kategorie |
| ------- | ---------------------------- | -------- | ---- | -------- |
| mce     | MQTT aktiviert               | bool     | R/W  | Config   |
| mcu     | MQTT broker url              | string   | R/W  | Config   |
| mcr     | MQTT readonly (erlaube kein Schreiben vom mqtt-broker aus) | bool   | R/W  | Config   |
| mtp     | MQTT topic prefix (auf null setzen um auf Werkseinstellung zurückzusetzen) | optional&lt;string&gt; | R/W  | Config   |
| mqg     | MQTT use global CA Store     | bool     | R/W  | Config   |
| mqcn    | MQTT skipCertCommonNameCheck | bool     | R/W  | Config   |
| mqss    | MQTT skipServerVerification  | bool     | R/W  | Config   |
| mcs     | MQTT gestartet               | bool     | R    | Status   |
| mcc     | MQTT verbunden               | bool     | R    | Status   |
| mcca    | MQTT connected (Zeitstempel in Millisekunden seit dem Hochfahren) Subtrahiere von der reboot-zeit (rbt) um die Dauer seit Verbunden zu erhalten | null or milliseconds | R | Status |
| mlr     | MQTT letzter error           | string or null | R | Status |
| mlra    | MQTT last error (Zeitstempel in Millisekunden seit dem Hochfahren) Subtrahiere von der reboot-zeit (rbt) um die Dauer seit Error zu erhalten | null or milliseconds | R | Status |
| mck     | MQTT client key              | string   | R/W  | Config   |
| mqcc    | MQTT client cert             | string   | R/W  | Config   |
| msc     | MQTT server cert             | string   | R/W  | Config   |

## Topics

Für jeden [API Keys](apikeys-de.md) veröffentlicht der Charger ein (persistentes) Topic. Das Topic setzt sich zusammen aus einem gemeinsamen Prefix, der Seriennummer und dem Api Key. Der Message-Inhalt ist dabei immer als JSON encodiert. Strings zB. werden mit Anführungszeichen versehen.

Beispiele:

```
go-eCharger/00000001/alw
go-eCharger/00000001/acu
go-eCharger/00000001/frc
```

Wenn mehrere go-e Charger am selben MQTT Server hängen, kann man mit MQTT wildcard queries einfach den aktuellesten Status alle Charger auflisten:

```
$ mosquitto_sub -v -t 'go-eCharger/#' | grep -P '/(?:alw|acu|fwv|rbt) '
go-eCharger/00000001/alw true
go-eCharger/00000001/acu 16
go-eCharger/00000001/rbt 498429772
go-eCharger/00000001/fwv "35.6-1-ga0d44e5"
go-eCharger/00000004/alw true
go-eCharger/00000004/acu 16
go-eCharger/00000004/rbt 498008264
go-eCharger/00000004/fwv "35.6-2-g99a02ad"
go-eCharger/00000004/rbt 498009263
go-eCharger/00000001/rbt 498430770
go-eCharger/00000004/rbt 498010263
go-eCharger/00000001/rbt 498431770
go-eCharger/00000004/rbt 498011263
go-eCharger/00000001/rbt 498432770
go-eCharger/00000004/rbt 498012264
^C
```

## Werte setzen

**Achtung:** Seit Firmware 051.5 muss das Setzen von Werten über MQTT extra erlaubt werden (siehe Screenshot oben).

Dem Topic muss noch ein `/set` hinten angefügt werden, damit es für andere MQTT Teilnehmer keine Verwechslungen gibt zwischen der Anfrage einen Wert zu Ändern und dem tatsächlich geltenden Wert, ausgesendet vom Charger. **Seit Firmware 051.5** wird, nachdem der Charger den Befehl erhalten hat, eine (nicht persistente) Antwort am Topic mit `/result` angestellt gesendet.

Beispiele:

```
go-eCharger/00000001/frc/set
go-eCharger/00000001/frc/result
```

wenn das `/set` topic auf 1 gesetzt wird, wird das Laden sofort gestoppt, wenn es auf 2 gesetzt wird, wird das Laden sofort erlaubt, 0 stellt wieder die ursprüngliche Logik her mit Scheduler, Awattar, Überschussladen und NextTrip.

Mehr Beispiele:

```
$ mosquitto_pub -t "go-eCharger/00000002/fna/set" -m "new_name"
$ mosquitto_pub -t "go-eCharger/00000002/fna/set" -m "0"
$ mosquitto_pub -t "go-eCharger/00000002/fna/set" -m "\"mein charger\""
```

Mit den jeweiligen Antworten dazu (seit Firmware 051.5):

```
$ mosquitto_sub -v -t "go-eCharger/00000002/#" | grep /fna
go-eCharger/00000002/fna "go-echarger_00000002"
go-eCharger/00000002/fna/set new_name
go-eCharger/00000002/fna/result invalid json IncompleteInput: new_name
go-eCharger/00000002/fna/set 0
go-eCharger/00000002/fna/result value must be string 0
go-eCharger/00000002/fna/set "mein charger"
go-eCharger/00000002/fna/result success
go-eCharger/00000002/fna "mein charger"
```
