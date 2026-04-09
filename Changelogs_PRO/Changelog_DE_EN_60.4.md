# Deutsch

1.	Unterstützung für Nutzung lokal am Charger angelernter RFID Karten bei Verwendung des Chargers zusammen mit dem go-e Portal hinzugefügt
2.	Untertützung für Push Notifications in der go-e App hinzugefügt
3.	Unterstützung für mTLS zu MQTT client hinzugefügt
4.	Unterstützung für Übermittlung des Initialisierungszustands des Ethernet Anschlusses hinzugefügt
5.	Unterstützung for Firmwareupdates über Mobilfunk hinzugefügt
6.	Modbus Register zum setzen der Modbus Wort- und Bytereihenfolge hinzugefügt
7.	OCPP: Unterstützung für in RemoteStartTransaction enthaltene Ladeprofile hinzugefügt
8.	OCPP: Unterstützung für Konfiguration MinChargingCurrent (äquivalent zum API key “mca“) hinzugefügt
9.	OCPP: Unterstützung für Konfiguration RequestedCurrent (äquivalent zum API key “amp“) hinzugefügt
10.	OCPP: Unterstützung für Konfiguration ConnectionTimeOut hinzugefügt (äquivalent zu API key “txt“) hinzugefügt
11.	OCPP: Unterstützung für Konfiguration StopChargingOnReboot hinzugefügt (äquivalent zu API key “osr“) hinzugefügt
12.	OCPP: Unterstützung für Messgröße LimitReason in MeterValues hinzugefügt
13.	OCPP: Fehler behoben durch welchen konfigurierte Messgrößen in MeterValues fehlen konnten
14.	Fehler behoben, durch welchen Zeitpläne Endes des Zeitplans inklusiv behandelt haben (10:00 - 11:00 entsprach 1h1m statt 1h)
15.	Inkorrekte Messung der abgegebenen Energiemenge pro RFID Karte behoben
16.	Fehler behoben durch welchen API key “ocppao” nicht übertragen wurde
17.	Fehler behoben durch welchen unzureichende Geräteversorgungsspannung als fehlende Daten des Ladecontrollers angezeigt wurde
18.	Unterscheidbarkeit der Anzeige unkategorisierter Fehlerzustände verbessert





# English


1.	Support using RFID tags locally enrolled on charger while charger is used together with go-e Portal
2.	Support push notifications in the go-e smartphone app
3.	Support mTLS on MQTT client
4.	Support indication of Ethernet initialization state
5.	Support firmware updates via cellular connectivity
6.	Support setting modbus byte and word order via modbus registers
7.	OCPP: Support charging profiles set in RemoteStartTransaction request
8.	OCPP: Add configuration item MinChargingCurrent (equivalent to API key “mca“)
9.	OCPP: Add configuration item RequestedCurrent (equivalent to API key “amp“)
10.	OCPP: Add configuration item ConnectionTimeOut (equivalent to API key “txt“)
11.	OCPP: Add configuration item StopChargingOnReboot hinzugefügt (equivalent to API key “osr“)
12.	OCPP: Support custom measurand LimitReason in MeterValues
13.	OCPP: Fix bug that caused configured measurand to be missing from MeterValues
14.	Fix bug that caused upper bound of time schedules to be handled inclusively inclusively instead of exclusively (10:00 - 11:00 referred to a 1h1m interval instead of 1h flat)
15.	Fix bug that caused incorrect accounting of per RFID card energy
16.	Fix bug that caused API key “ocppao“ not be transmitted
17.	Fix bug that caused too low a device supply voltage to be shown as missing charge controller data
18.	Improved visual distinction between uncategorized device errors

