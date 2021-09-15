 Deutsch &bull; [English](mqtt-en.md)

# MQTT

[Die API Keys](apikeys-de.md) können über MQTT gelesen und geschrieben werden. Ab Firmware 051.5 muss das Schreiben jedoch extra erlaubt werden, da es ab da nicht mehr standardmäßig erlaubt ist.

Dafür muss MQTT in der App erst aktiviert werden:

<img src="screenshots/mqtt-app-enable.png?raw=true" width="200" />

**Warnung:** Verwenden Sie die voreingestellte test Broker url wirklich nur für kurze Tests und nicht im Dauerbetrieb, da der Charger sonst von Fremden aus dem Internet gesehen und gesteuert werden kann. Es kann das konfigurierte WLAN gelöscht oder auch ein Neustart veranlasst werden.

## Topics

Für jeden [API Keys](apikeys-de.md) veröffentlicht der Charger ein (persistentes) Topic. Das Topic setzt sich zusammen aus einem gemeinsamen Prefix, der Seriennummer und dem Api Key. Der Message-Inhalt ist dabei immer als JSON encodiert. Strings zB. werden mit Anführungszeichen versehen.

Beispiele:

```
/go-eCharger/00000001/alw
/go-eCharger/00000001/acu
/go-eCharger/00000001/frc
```

Wenn mehrere go-e Charger am selben MQTT Server hängen, kann man mit MQTT wildcard queries einfach den aktuellesten Status alle Charger auflisten:

```
$ mosquitto_sub -v -t '/go-eCharger/#' | grep -P '/(?:alw|acu|fwv|rbt) '
/go-eCharger/00000001/alw true
/go-eCharger/00000001/acu 16
/go-eCharger/00000001/rbt 498429772
/go-eCharger/00000001/fwv "35.6-1-ga0d44e5"
/go-eCharger/00000004/alw true
/go-eCharger/00000004/acu 16
/go-eCharger/00000004/rbt 498008264
/go-eCharger/00000004/fwv "35.6-2-g99a02ad"
/go-eCharger/00000004/rbt 498009263
/go-eCharger/00000001/rbt 498430770
/go-eCharger/00000004/rbt 498010263
/go-eCharger/00000001/rbt 498431770
/go-eCharger/00000004/rbt 498011263
/go-eCharger/00000001/rbt 498432770
/go-eCharger/00000004/rbt 498012264
^C
```
