DE
Unterstützung für Nutzung lokal am Charger angelernter RFID Karten bei Verwendung des Chargers zusammen mit dem go-e Portal hinzugefügt

Untertützung für Push Notifications in der go-e App hinzugefügt

Unterstützung für mTLS zu MQTT client hinzugefügt

Unterstützung für Übermittlung des Initialisierungszustands des Ethernet Anschlusses hinzugefügt

Unterstützung for Firmwareupdates über Mobilfunk hinzugefügt

Modbus Register zum setzen der Modbus Wort- und Bytereihenfolge hinzugefügt

OCPP: Unterstützung für in RemoteStartTransaction enthaltene Ladeprofile hinzugefügt

OCPP: Unterstützung für Konfiguration MinChargingCurrent (äquivalent zum API key “mca“) hinzugefügt

OCPP: Unterstützung für Konfiguration RequestedCurrent (äquivalent zum API key “amp“) hinzugefügt

OCPP: Unterstützung für Konfiguration ConnectionTimeOut hinzugefügt (äquivalent zu API key “txt“) hinzugefügt

OCPP: Unterstützung für Konfiguration StopChargingOnReboot hinzugefügt (äquivalent zu API key “osr“) hinzugefügt

OCPP: Unterstützung für Messgröße LimitReason in MeterValues hinzugefügt

OCPP: Fehler behoben durch welchen konfigurierte Messgrößen in MeterValues fehlen konnten

Fehler behoben, durch welchen Zeitpläne Endes des Zeitplans inklusiv behandelt haben (10:00 - 11:00 entsprach 1h1m statt 1h)

Inkorrekte Messung der abgegebenen Energiemenge pro RFID Karte behoben

Fehler behoben durch welchen API key “ocppao” nicht übertragen wurde

Fehler behoben durch welchen unzureichende Geräteversorgungsspannung als fehlende Daten des Ladecontrollers angezeigt wurde

Unterscheidbarkeit der Anzeige unkategorisierter Fehlerzustände verbessert



EN

Support using RFID tags locally enrolled on charger while charger is used together with go-e Portal

Support push notifications in the go-e smartphone app

Support mTLS on MQTT client

Support indication of Ethernet initialization state

Support firmware updates via cellular connectivity

Support setting modbus byte and word order via modbus registers

OCPP: Support charging profiles set in RemoteStartTransaction request

OCPP: Add configuration item MinChargingCurrent (equivalent to API key “mca“)

OCPP: Add configuration item RequestedCurrent (equivalent to API key “amp“)

OCPP: Add configuration item ConnectionTimeOut (equivalent to API key “txt“)

OCPP: Add configuration item StopChargingOnReboot hinzugefügt (equivalent to API key “osr“)

OCPP: Support custom measurand LimitReason in MeterValues

OCPP: Fix bug that caused configured measurand to be missing from MeterValues

Fix bug that caused upper bound of time schedules to be handled inclusively inclusively instead of exclusively (10:00 - 11:00 referred to a 1h1m interval instead of 1h flat)

Fix bug that caused incorrect accounting of per RFID card energy

Fix bug that caused API key “ocppao“ not be transmitted

Fix bug that caused too low a device supply voltage to be shown as missing charge controller data

Improved visual distinction between uncategorized device errors
