Deutsch &bull; [English](modbus-en.md)

# Modbus

Die go-eCharger bieten ein Modbus TCP Interface an, mit dem einige Leistungs- und Energiewerte abgefragt werden können. Dieses Interface muss erst über die App oder [http API](http-de.md) aktiviert werden. Daten gelesen werden können über die [Modbus Funktion 3](https://www.simplymodbus.ca/FC03.htm) und die [Modbus Funktion 4](https://www.simplymodbus.ca/FC04.htm). Daten können über die [Modbus Funktion 16](https://www.simplymodbus.ca/FC16.htm) geschrieben werden. Nach Aktivierung kann der TCP Port 502 verwendet werden.

| Funktion Nr | Name                      | Unterstützt?                            |
| ----------- | ------------------------- | --------------------------------------- |
| 01          | Read Coil Status          | Nein                                    |
| 02          | Read Input Status         | Nein                                    |
| 03          | Read Holding Registers    | Ja, für alle Register unten aufgelistet |
| 04          | Read Input Registers      | Ja, für alle Register unten aufgelistet |
| 05          | Force Single Coil         | Nein                                    |
| 06          | Preset Single Register    | Nein                                    |
| 15          | Force Multiple Coils      | Nein                                    |
| 16          | Preset Multiple Registers | Ja, für alle Register unten aufgelistet |

## Über die App das Modbus Interface aktivieren und prüfen

Unten im Tab "Internet", dann "Erweiterte Einstelluingen" im Menü anwählen, dann relativ weit unten bei Modbus

<img src="screenshots/modbus-app-enable.png?raw=true" width="200" />

## Über die http API das Modbus interface aktivieren und prüfen

Die Chargers verfügen über API Keys zum Konfigurieren und Prüfen des Modbus interface. Diese API Keys können mit der http api verwendet werden.

Beispiel: http://192.168.0.77/api/set?men=true

| api key | Beschreibung                 | Datentyp | R?W? | Kategorie |
| ------- | ---------------------------- | -------- | ---- | --------- |
| men     | modbus slave aktiviert       | bool     | R/W  | Config    |
| msp     | modbus slave port (erfordert Neustart) | uint16 | R/W | Config |
| msb     | modbus slave Bytes vertauschen | bool     | R/W  | Config    |
| msr     | modbus slave Register vertauschen | bool     | R/W  | Config    |
| mro     | modbus slave Lese-Operationen | size_t   | R    | Status    |
| mwo     | modbus slave Schreib-Operationen | size_t  | R    | Status    |

## Modbus Profil

### Holding Registers (read/write)

Daten in dieser Tabelle können mit der Modbus Funktion 03 gelesen und mit der Modbus Funktion 16 geschrieben werden.

| Register (wire-format) | Bezeichnung                 | Register Typ     | Datentyp | Länge | Beschreibung |
| ---------------------- | --------------------------- | ---------------- | -------- | ----- | - |
| 40201 (200)            | ALLOW                       | Holding Register | uint16_t | 1     | **allow_charging:** PWM Signal darf<br>anliegen<br>0: nein<br>1: ja |
| 40202 (201)            | ACCESS_STATE                | Holding Register | uint16_t | 1     | **access_state**: Zugangskontrolle.<br>0: Offen<br>1: RFID / App benötigt<br>2: Strompreis / automatisch<br>3: Scheduler |
| 40205 (204)            | CABLE_LOCK_MODE             | Holding Register | uint16_t | 1     | Kabelverriegelung Einstellung<br>0: Verriegeln solange Auto angesteckt<br>1: Nach Ladevorgang automatisch<br>entriegeln<br>2: Kabel immer verriegelt lassen |
| 40207 (206)            | LED_BRIGHTNESS              | Holding Register | uint16_t | 1     | **LED Helligkeit** von 0-255<br>0: LED aus<br>255: LED Helligkeit maxima |
| 40208 (207)            | LED_SAVE_ENERGY             | Holding Register | uint16_t | 1     | **led_save_energy**: LED automatisch<br>nach 10 Sekunden abschalten<br>0: Energiesparfunktion deaktiviert<br>1: Energiesparfunktion aktiviert |
| 40209 (208)            | ELECTRICITY_PRICES_HOURS    | Holding Register | uint16_t | 1     | Minimale **​Anzahl** ​von Stunden in der<br>mit "Strompreis - automatisch" geladen<br>werden muss<br>Beispiel: 2 ("Auto ist nach 2 Stundenvoll genug") |
| 40210 (209)            | ELECTRICITY_PRICES_FINISHED | Holding Register | uint16_t | 1     | Stunde (**​Uhrzeit​**) in der mit "Strompreis<br>- automatisch" die Ladung mindestens<br>aho ​Stunden gedauert haben muss.<br>Beispiel: 7 ("Fertig bis 7:00, also davor<br>mindestens 2 Stunden geladen") |
| 40211 (210)            | ELECTRICITY_PRICES_ZONE     | Holding Register | uint16_t | 1     | Awattar Preiszone<br>0: Österreich<br>1: Deutschland |
| 40212 (211)            | AMPERE_MAX                  | Holding Register | uint16_t | 1     | Absolute max. Ampere: Maximalwert<br>für Ampere Einstellung<br>Beispiel: 20 (Einstellung auf mehr als<br>20A in der App nicht möglich) |
| 40213 (212)            | AMPERE_L1                   | Holding Register | uint16_t | 1     | Ampere Level 1 für Druckknopf am<br>Gerät.<br>6-32: Ampere Stufe aktiviert<br>0: Stufe deaktivert (wird übersprungen) |
| 40214 (213)            | AMPERE_L2                   | Holding Register | uint16_t | 1     | Ampere Level 2 für Druckknopf am<br>Gerät.<br>6-32: Ampere Stufe aktiviert<br>0: Stufe deaktivert (wird übersprungen) |
| 40215 (214)            | AMPERE_L3                   | Holding Register | uint16_t | 1     | Ampere Level 3 für Druckknopf am<br>Gerät.<br>6-32: Ampere Stufe aktiviert<br>0: Stufe deaktivert (wird übersprungen) |
| 40216 (215)            | AMPERE_L4                   | Holding Register | uint16_t | 1     | Ampere Level 4 für Druckknopf am<br>Gerät.<br>6-32: Ampere Stufe aktiviert<br>0: Stufe deaktivert (wird übersprungen) |
| 40217 (216)            | AMPERE_L5                   | Holding Register | uint16_t | 1     | Ampere Level 5 für Druckknopf am<br>Gerät.<br>6-32: Ampere Stufe aktiviert<br>0: Stufe deaktivert (wird übersprungen) |
| 40218 (217)            | CLOUD_DISABLED              | Holding Register | uint16_t | 1     | **Cloud disabled**<br>0: cloud enabled<br>1: cloud disabled |
| 40219 (218)            | NORWAY_MODE                 | Holding Register | uint16_t | 1     | **Norwegen-Modu**s​ aktiviert<br>0: deaktiviert (Erdungserkennung<br>aktiviert)<br>1: aktiviert (keine Erdungserkennung, <br>nur für IT-Netze gedacht) |
| 40300 (299)            | AMPERE_VOLATILE             | Holding Register | uint16_t | 1     | Ampere Wert für die PWM<br>Signalisierung in ganzen Ampere von<br>**6-32A**<br><br>Wird nicht im EEPROM gespeichert<br>und wird beim nächsten Bootvorgang<br>auf den zuletzt im EEPROM<br>gespeicherten Wert **​zurückgesetzt​**.<br>Für Energieregelung |
| 40301 (300)            | AMPERE_EEPROM               | Holding Register | uint16_t | 1     | Ampere Wert für die PWM<br>Signalisierung in ganzen Ampere von<br>**6-32A**<br><br>Wird im EEPROM ​gespeichert ​(max.<br>Schreibzyklen ca. 100.000) |
| 40333 (332)            | PHASE_SWITCH_MODE           | Holding Register | uint16_t | 1     | Selbe wie api key psm, akzeptiert nur 0, 1, 2 (Seit Firmware 55.5) |
| 40334 (333)<br>40335 (334)<br>40336 (335)<br>40337 (336) | ENERGY_LIMIT | Holding Register | float (64)            | 4     | Selbe wie api key dwo, auf float Inf setzen, um "null" Limit auszudrücken (Limit deaktiviert), oder jede andere float Zahl in Wattstunden (Wh) (Seit Firmware 55.5) |
| 40338 (337)            | FORCE_STATE                 | Holding Register | uint16_t | 1     | Selbe wie api key frc, akzeptiert nur 0, 1, 2 (Seit Firmware 55.6) |

### Input Registers (read-only)

Daten in dieser Tabelle können mit der Modbus Funktion 04 gelesen werden.

| Register(wire-format)     | Bezeichnung     | Register Typ   | Datentyp | Länge | Beschreibung |
| -------------------------- | --------------- | -------------- | -------- | ----- | - |
| 30101 (100)                | CAR_STATE       | Input Register | uint16_t | 1     | **Status PWM Signalisierung**<br>0: unbekannt, Ladestation defekt<br>1: Ladestation bereit, kein Fahrzeug<br>2: Fahrzeug lädt<br>3: Warte auf Fahrzeug<br>4: Ladung beendet, Fahrzeug noch<br>verbunden |
| 30102 (101)                | PP_CABLE        | Input Register | uint16_t | 1     | Typ2 **Kabel Ampere codierung**<br>13-32: Ampere Codierung<br>0: kein Kabel |
| 30106 (105)<br>30107 (106) | FWV             | Input Register | ascii (4 byte) | 2 | Firmware Version als ASCII |
| 30108 (107)                | ERROR           | Input Register | uint16_t | 1     | error:<br>1: RCCB (Fehlerstromschutzschalter)<br>3: PHASE (Phasenstörung)<br>8: NO_GROUND (Erdungserkennung)<br>10, default: INTERNAL (sonstiges) |
| 30109 (108)<br>30110 (109) | VOLT_L1         | Input Register | uint32_t | 2     | Spannung auf L1 in Volt |
| 30111 (110)<br>30112 (111) | VOLT_L2         | Input Register | uint32_t | 2     | Spannung auf L2 in Volt |
| 112 <br>113                | VOLT_L3         | Input Register | uint32_t | 2     | Spannung auf L3 in Volt |
| 114<br>115                 | AMP_L1          | Input Register | uint32_t | 2     | Ampere auf L1 in 0.1A (123 entspricht 12, 3A) |
| 116<br>117                 | AMP_L2          | Input Register | uint32_t | 2     | Ampere auf L2 in 0.1A (123 entspricht 12, 3A) |
| 118 <br>119                | AMP_L3          | Input Register | uint32_t | 2     | Ampere auf L3 in 0.1A (123 entspricht 12, 3A) |
| 120<br>121                 | POWER_TOTAL     | Input Register | uint32_t | 2     | Leistung gesamt in 0.01W (360000 entspricht 3,6kW) |
| 128 <br>129                | ENERGY_TOTAL    | Input Register | uint32_t | 2     | Gesamt geladene Energiemenge in 0.1kWh (360 entspricht 36kWh) |
| 132<br>133                 | ENERGY_CHARGE   | Input Register | uint32_t | 2     | **Geladene Energiemenge** in<br>Deka-Watt-Sekunden<br>Beispiel:100’000 bedeutet, 1’000’000<br>Ws (=277Wh = 0, 277kWh) wurden in<br>diesem Ladevorgang geladen. |
| 144 <br>145                | VOLT_N          | Input Register | uint32_t | 2     | Spannung auf N in Volt |
| 146 <br>147                | POWER_L1        | Input Register | uint32_t | 2     | Leistung auf L1 in 0.1kW (36 entspricht 3, 6kW) |
| 148<br>149                 | POWER_L2        | Input Register | uint32_t | 2     | Leistung auf L2 in 0.1kW (36 entspricht 3, 6kW) |
| 150 <br>151                | POWER_L3        | Input Register | uint32_t | 2     | Leistung auf L3 in 0.1kW (36 entspricht 3, 6kW) |
| 152 <br>153                | POWER_FACTOR_L1 | Input Register | uint32_t | 2     | Leistungsfaktor auf L1 in % |
| 154<br>155                 | POWER_FACTOR_L2 | Input Register | uint32_t | 2     | Leistungsfaktor auf L2 in % |
| 156<br>157                 | POWER_FACTOR_L3 | Input Register | uint32_t | 2     | Leistungsfaktor auf L3 in % |
| 158 <br>159                | POWER_FACTOR_N  | Input Register | uint32_t | 2     | Leistungsfaktor auf N in % |
| 202                        | ADAPTER_INPUT   | Input Register | uint16_t | 1     | **adapter_in**: Ladebox ist mit Adapter<br>angesteckt<br>0: NO_ADAPTER<br>1: 16A_ADAPTER |
| 203                        | UNLOCKED_BY     | Input Register | uint16_t | 1     | Nummer der RFID Karte, die den<br>jetzigen Ladevorgang freigeschalten<br>hat |
| 205                        | PHASES          | Input Register | uint16_t | 1     | **Phasen** vor und nach dem Schütz<br>binary flags: 0b00ABCDEF<br>A... phase 3, vor dem Schütz<br> B... phase 2 vor dem Schütz<br>C... phase 1 vor dem Schütz<br>D... phase 3 nach dem Schütz<br>E... phase 2 nach dem Schütz<br>F... phase 1 nach dem Schütz<br>pha 0b00001000: Phase 1 ist<br>vorhanden<br>pha 0b00111000: Phase1-3 ist<br>vorhanden<br> |
| 301<br>302<br>303          | MAC             | Input Register | unsigned integer (48) | 3 | MAC Adresse der WLAN Station, binär |
| 304<br>305<br>306<br>307<br>308<br>309 | SNR | Input Register | ascii (12 byte) | 6 | Seriennummer des go-eCharger, als<br>ASCII |
| 310<br>311<br>312<br>313<br>314 | HOSTNAME   | Input Register | ascii (10 byte) | 6 | Hostname des go-eCharger, als ASCII |
| 315<br>316<br>317<br>318   | IP              | Input Register | ascii (8 byte)  | 4 | IP Adresse des go-eCharger, 1 Bytepro Register |
| 319<br>320<br>321<br>322   | SUBNET          | Input Register | unsigned integer (64) | 4 | Subnetzmaske des go-eCharger, 1<br>Byte pro Register |
| 323<br>324<br>325<br>326   | GATEWAY         | Input Register | ascii (4 byte)  | 4 | Gateway des go-eCharger, 1 Byte proRegister |
| 30328 (327)<br>30329 (328)<br>30330 (329)<br>30331 (330)<br>30332 (331) | RFID_CARD | Input Register | binary (10 byte)      | 5     | Zuletzt hingehaltene RFID Seriennummer, 4-byte und 7-byte lange Nummern werden mit Nullen am Ende aufgefüllt, 10-byte lange Nummern füllen die 5 modbus register sowieso schon (Seit Firmware 55.5) |
| 30333 (332)<br>30334 (333)<br>30335 (334)<br>30336 (335) | ENERGY_CARD0    | Input Register | double   | 4     | Energie aufgebucht auf RFID Karte 1 (in W) |
| 30337 (336)<br>30338 (337)<br>30339 (338)<br>30340 (339) | ENERGY_CARD1    | Input Register | double   | 4     | Energie aufgebucht auf RFID Karte 2 (in W) |
| 30341 (340)<br>30342 (341)<br>30343 (342)<br>30344 (343) | ENERGY_CARD2    | Input Register | double   | 4     | Energie aufgebucht auf RFID Karte 3 (in W) |
| 30345 (344)<br>30346 (345)<br>30347 (346)<br>30348 (347) | ENERGY_CARD3    | Input Register | double   | 4     | Energie aufgebucht auf RFID Karte 4 (in W) |
| 30349 (348)<br>30350 (349)<br>30351 (350)<br>30352 (351) | ENERGY_CARD4    | Input Register | double   | 4     | Energie aufgebucht auf RFID Karte 5 (in W) |
| 30353 (352)<br>30354 (353)<br>30355 (354)<br>30356 (355) | ENERGY_CARD5    | Input Register | double   | 4     | Energie aufgebucht auf RFID Karte 6 (in W) |
| 30357 (356)<br>30358 (357)<br>30359 (358)<br>30360 (359) | ENERGY_CARD6    | Input Register | double   | 4     | Energie aufgebucht auf RFID Karte 7 (in W) |
| 30361 (360)<br>30362 (361)<br>30363 (362)<br>30364 (363) | ENERGY_CARD7    | Input Register | double   | 4     | Energie aufgebucht auf RFID Karte 8 (in W) |
| 30365 (364)<br>30366 (365)<br>30367 (366)<br>30368 (367) | ENERGY_CARD8    | Input Register | double   | 4     | Energie aufgebucht auf RFID Karte 9 (in W) |
| 30369 (368)<br>30370 (369)<br>30371 (370)<br>30372 (371) | ENERGY_CARD9    | Input Register | double   | 4     | Energie aufgebucht auf RFID Karte 10 (in W) |