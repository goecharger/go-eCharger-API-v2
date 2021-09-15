 Deutsch &bull; [English](mqtt-en.md)

# MQTT

[Die API Keys](apikeys-de.md) können über MQTT gelesen und geschrieben werden. Ab Firmware 051.5 muss das Schreiben jedoch extra erlaubt werden, da es ab da nicht mehr standardmäßig erlaubt ist.

Dafür muss MQTT in der App erst aktiviert werden:

<img src="screenshots/mqtt-app-enable.png?raw=true" width="200" />

**Warnung:** Verwenden Sie die voreingestellte test Broker url wirklich nur für kurze Tests und nicht im Dauerbetrieb, da der Charger sonst von Fremden aus dem Internet gesehen und gesteuert werden kann. Es kann das konfigurierte WLAN gelöscht oder auch ein Neustart veranlasst werden.

## Topics

TODO für go-e: die topics zum Lesen und Schreiben dokumentieren.
