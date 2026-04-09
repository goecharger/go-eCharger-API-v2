# Deutsch

1.	Möglichkeit den Sim Karten Slot zu wählen
2.	Ladeprofil ist in RemoteStartTransaction Befehl wird nicht mehr ignoriert
3.	Fügt OCPP Konfigurationsschlüssel MinChargingCurrent ("mca") RequestedCurrent ("amp") und  LimitReason Messgröße zu Meter Values hinzu.
4.	Unterstützung für komplexere Scheduler-Regeln hinzugefügt
5.	Fügt LimitReason zu OCPP Meter Values hinzu
6.	Ein Fehler im Ladetimer wurde behoben. Zeiträume wie 10:00 - 11:00 laden nicht mehr für 1 Stunde und 1 Minute sondern genau 1 Stunde.
7.	V6 Konfiguration nun verfügbar
8.	V6 Charger können nun das Modem in Fabrik ein-/aus-geschaltet bekommen
9.	Zuverlässigere Namensauflösung im Netzwerk, wenn mehrere Verbindungen aktiv sind (LTE, WLAN, oder Ethernet, wenn vom Produkt unterstützt)
10.	Implementiert `ConnectionTimeOut` OCPP Konfigurationsparameter und dazugehörigen API Schlüssel `txt`.
11.	Repariert fehlenden betrag je Messwert in MeterValues.
12.	Failsafe Mechanismus implementiert via modbus und api
13.	V6 Charger können nun das Modem in Fabrik ein-/aus-geschaltet bekommen
14.	Fehlender API key ocppao außerhalb debug modus behoben
15.	Modbus register hinzugefügt, mit dem modbus swap bytes und register reihenfolge kontrolliert werden kann.
16.	Modbus Register hinzugefügt um die Byte- und Registerreihenfolge zu verändern
17.	Implementiert API Schlüssel `osr` und entsprechenden OCPP Konfigurationsparameter `StopChargingOnReboot` welcher eine laufende Ladesitzung stoppt, wenn `osr` True ist, das Ladegerät neu startet und OCPP aktiviert ist.
18.	Die Blinkfarbe für GeneralError wurde von Rot auf Orange geändert.
19.	Failsafe Countdown Funktionalität zur API und Modbus hinzugefügt
20.	Firmware bleibt nicht mehr stecken, wenn unzuverlässige websocket clients verbinden
21.	Die MQTT-Verbindung wird nun bei Konfigurationsänderungen wiederhergestellt.
22.	LTE Modem Stabilität wurde verbessert
23.	Geräte können nun ihre Hardware-Revision speichern (PCB Revisionen)
24.	Behebt falsch skalierten OCPP Temperature-measurand um Faktor 1000.


# English

1.	Sim Card Slot is no chooseable
2.	Charging profile in RemoteStartTransaction command is not ignored anymore
3.	Adds OCPP config keys  MinChargingCurrent ("mca") RequestedCurrent ("amp") and  LimitReason measurand to Meter Values.
4.	Add support for more fine-grained scheduler rules
5.	Adds LimitReason to OCPP Meter Values
6.	Fix scheduler being off by one minute. Ranges like 10:00 - 11:00 no longer charge for 1 hour and 1 minute and now charge exactly 1 hour.
7.	V6 configuration now available
8.	V6 chargers can now have the modem enabled/disabled in factory
9.	Improved network name resolution reliability when using multiple network connections (LTE, WiFi, or Ethernet on supported products)
10.	Implements `ConnectionTimeOut` OCPP parameter and corresponding API key `txt`.
11.	Fixes missing measurand value in MeterValues.
12.	Implemented failsafe functionality via modbus and api
13.	V6 chargers can now have the modem enabled/disabled in factory
14.	Fix API key ocppao not being sent
15.	Added modbus register to control modbus swap bytes and registers
16.	Added modbus registers to configure byte and register order
17.	Implements API key `osr` and respective OCPP configuration parameter `StopChargingOnReboot` that stops ongoing charging session if charger reboots, `osr` is `True` and OCPP is enabled.
18.	The blinking color for GeneralError was changed from red to orange
19.	Added failsafe countdown functionality to API and modbus
20.	Fixed firmware getting stuck with unreliable websocket client connections
21.	mqtt connection now reconnects on config changes
22.	Improved LTE modem stability
23.	Devices can now store their hardware revision (pcb revisions)
24.	Fixes wrongly scaled OCPP Temperature-measurand by factor 1000.
