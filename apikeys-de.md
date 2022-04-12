Deutsch &bull; [English](apikeys-en.md)

# API Keys

| Key        | R/W        | Type                         | Category      | Description                                                                         |
| ---------- | ---------- | ---------------------------- | ------------- | ----------------------------------------------------------------------------------- |
| rfb        | R          | int                          | Status        | Relay Feedback                                                                      |
| rst        | W          | any                          | Other         | Ladestation neustarten                                                              |
| alw        | R          | bool                         | Status        | Darf das Auto derzeit laden?                                                        |
| acu        | R          | int                          | Status        | Mit wie vielen Ampere darf das Auto derzeit laden?                                  |
| adi        | R          | bool                         | Status        | Wird der 16A Adapter benutzt? Limitiert den Ladestrom auf 16A                       |
| dwo        | R/W        | optional&lt;double&gt;       | Config        | Lade Energy Limit, gemessen in Wh, null bedeutet deaktiviert, nicht mit der Next-Trip Energie zu verwechseln |
| tpa        | R          | float                        | Status        | 30 Sekunden Gesamtleistungsdurchschnitt (wird für genauere next-trip vorhersagen berechnet) |
| sse        | R          | string                       | Constant      | serial number                                                                       |
| eto        | R          | uint64                       | Status        | energy_total, measured in Wh                                                        |
| wifis      | R/W        | array                        | Config        | WiFi Konfiguration mit SSID und Passwort; Wenn man nur den zweiten Eintrag ändern möchte, einfach das erste Objekt leer lassen: `[{}, {"ssid":"","key":""}]` |
| delw       | W          | uint8                        | Other         | set this to 0-9 to delete sta config (erases ssid, key, ...)                        |
| scan       | R          | array                        | Status        | wifi scan result (encryptionType: OPEN=0, WEP=1, WPA_PSK=2, WPA2_PSK=3, WPA_WPA2_PSK=4, WPA2_ENTERPRISE=5, WPA3_PSK=6, WPA2_WPA3_PSK=7) |
| scaa       | R          | milliseconds                 | Status        | wifi scan age                                                                       |
| wst        | R          | uint8                        | Status        | WiFi STA status (IDLE_STATUS=0, NO_SSID_AVAIL=1, SCAN_COMPLETED=2, CONNECTED=3, CONNECT_FAILED=4, CONNECTION_LOST=5, DISCONNECTED=6, CONNECTING=8, DISCONNECTING=9, NO_SHIELD=10 (for compatibility with WiFi Shield library)) |
| wsc        | R          | uint8                        | Status        | WiFi STA error count                                                                |
| wsm        | R          | string                       | Status        | WiFi STA error message                                                              |
| wsms       | R          | uint8                        | Status        | WiFi state machine state (None=0, Scanning=1, Connecting=2, Connected=3)            |
| ccw        | R          | optional&lt;object&gt;       | Status        | Currently connected WiFi                                                            |
| wfb        | R          | array                        | Status        | WiFi failed mac addresses                                                           |
| wcb        | R          | string                       | Status        | WiFi current mac address                                                            |
| wpb        | R          | array                        | Status        | WiFi planned mac addresses                                                          |
| nif        | R          | string                       | Status        | Default route                                                                       |
| dns        | R          | object                       | Status        | DNS server                                                                          |
| host       | R          | optional&lt;string&gt;       | Status        | hostname used on STA interface                                                      |
| rssi       | R          | optional&lt;int8&gt;         | Status        | RSSI signal strength                                                                |
| tse        | R/W        | bool                         | Config        | time server enabled (NTP)                                                           |
| tsss       | R          | uint8                        | Config        | time server sync status (RESET=0, COMPLETED=1, IN_PROGRESS=2)                       |
| tof        | R/W        | minutes                      | Config        | timezone offset in minutes                                                          |
| tds        | R/W        | uint8                        | Config        | timezone daylight saving mode, None=0, EuropeanSummerTime=1, UsDaylightTime=2       |
| utc        | R/W        | string                       | Status        | utc time                                                                            |
| loc        | R          | string                       | Status        | local time                                                                          |
| led        | R          | object                       | Status        | internal infos about currently running led animation                                |
| lbr        | R/W        | uint8                        | Config        | led_bright, 0-255                                                                   |
| lmo        | R/W        | uint8                        | Config        | logic mode (Default=3, Awattar=4, AutomaticStop=5)                                  |
| ama        | R/W        | uint8                        | Config        | ampere_max limit                                                                    |
| clp        | R/W        | array                        | Config        | current limit presets, max. 5 entries                                               |
| bac        | R/W        | bool                         | Config        | Button allow Current change                                                         |
| sdp        | R/W        | bool                         | Config        | Button Allow Force change                                                           |
| lbp        | R          | milliseconds                 | Status        | lastButtonPress in milliseconds                                                     |
| amp        | R/W        | uint8                        | Config        | requestedCurrent in Ampere, used for display on LED ring and logic calculations     |
| fna        | R/W        | string                       | Config        | friendlyName                                                                        |
| cid        | R/W        | string                       | Config        | color_idle, format: #RRGGBB                                                         |
| cwc        | R/W        | string                       | Config        | color_waitcar, format: #RRGGBB                                                      |
| cch        | R/W        | string                       | Config        | color_charging, format: #RRGGBB                                                     |
| cfi        | R/W        | string                       | Config        | color_finished, format: #RRGGBB                                                     |
| ust        | R/W        | uint8                        | Config        | unlock_setting (Normal=0, AutoUnlock=1, AlwaysLock=2)                               |
| lck        | R          | uint8                        | Status        | Effective lock setting, as sent to Charge Ctrl (Normal=0, AutoUnlock=1, AlwaysLock=2, ForceUnlock=3) |
| sch_week   | R/W        | object                       | Config        | scheduler_weekday, control enum values: Disabled=0, Inside=1, Outside=2             |
| sch_satur  | R/W        | object                       | Config        | scheduler_saturday, control enum values: Disabled=0, Inside=1, Outside=2            |
| sch_sund   | R/W        | object                       | Config        | scheduler_sunday, control enum values: Disabled=0, Inside=1, Outside=2              |
| nmo        | R/W        | bool                         | Config        | norway_mode / ground check enabled when norway mode is disabled (inverted)          |
| fsp        | R/W        | bool                         | Status        | force_single_phase (shows if currently single phase charge is enforced              |
| lrn        | W          | uint8                        | Other         | set this to 0-9 to learn last read card id                                          |
| del        | W          | uint8                        | Other         | set this to 0-9 to clear card (erases card name, energy and rfid id)                |
| acs        | R/W        | uint8                        | Config        | access_control user setting (Open=0, Wait=1)                                        |
| frc        | R/W        | uint8                        | Config        | forceState (Neutral=0, Off=1, On=2)                                                 |
| rbc        | R          | uint32                       | Status        | reboot_counter                                                                      |
| rbt        | R          | milliseconds                 | Status        | time since boot in milliseconds                                                     |
| car        | R          | optional&lt;uint8&gt;        | Status        | carState, null if internal error (Unknown/Error=0, Idle=1, Charging=2, WaitCar=3, Complete=4, Error=5) |
| err        | R          | optional&lt;uint8&gt;        | Status        | error, null if internal error (Unknown/Error=0, Idle=1, Charging=2, WaitCar=3, Complete=4, Error=5) |
| cbl        | R          | optional&lt;int&gt;          | Status        | cable_current_limit in A                                                            |
| pha        | R          | optional&lt;array&gt;        | Status        | phases                                                                              |
| wh         | R          | double                       | Status        | energy in Wh since car connected                                                    |
| trx        | R/W        | optional&lt;uint8&gt;        | Status        | transaction, null when no transaction, 0 when without card, otherwise cardIndex + 1 (1: 0. card, 2: 1. card, ...) |
| fwv        | R          | string                       | Constant      | FW_VERSION                                                                          |
| ccu        | R          | optional&lt;object&gt;       | Status        | charge controller update progress (null if no update is in progress)                |
| oem        | R          | string                       | Constant      | OEM manufacturer                                                                    |
| typ        | R          | string                       | Constant      | Devicetype                                                                          |
| fwc        | R          | string                       | Constant      | firmware from CarControl                                                            |
| ccrv       | R          | string                       | Constant      | chargectrl recommended version                                                      |
| lse        | R/W        | bool                         | Config        | led_save_energy                                                                     |
| cdi        | R          | object                       | Status        | charging duration info (null=no charging in progress, type=0 counter going up, type=1 duration in ms) |
| lccfi      | R          | optional&lt;milliseconds&gt; | Status        | lastCarStateChangedFromIdle (in ms)                                                 |
| lccfc      | R          | optional&lt;milliseconds&gt; | Status        | lastCarStateChangedFromCharging (in ms)                                             |
| lcctc      | R          | optional&lt;milliseconds&gt; | Status        | lastCarStateChangedToCharging (in ms)                                               |
| tma        | R          | array                        | Status        | temperature sensors                                                                 |
| amt        | R          | int                          | Status        | temperatureCurrentLimit                                                             |
| nrg        | R          | array                        | Status        | energy array, U (L1, L2, L3, N), I (L1, L2, L3), P (L1, L2, L3, N, Total), pf (L1, L2, L3, N) |
| modelStatus | R         | uint8                        | Status        | Reason why we allow charging or not right now (NotChargingBecauseNoChargeCtrlData=0, NotChargingBecauseOvertemperature=1, NotChargingBecauseAccessControlWait=2, ChargingBecauseForceStateOn=3, NotChargingBecauseForceStateOff=4, NotChargingBecauseScheduler=5, NotChargingBecauseEnergyLimit=6, ChargingBecauseAwattarPriceLow=7, ChargingBecauseAutomaticStopTestLadung=8, ChargingBecauseAutomaticStopNotEnoughTime=9, ChargingBecauseAutomaticStop=10, ChargingBecauseAutomaticStopNoClock=11, ChargingBecausePvSurplus=12, ChargingBecauseFallbackGoEDefault=13, ChargingBecauseFallbackGoEScheduler=14, ChargingBecauseFallbackDefault=15, NotChargingBecauseFallbackGoEAwattar=16, NotChargingBecauseFallbackAwattar=17, NotChargingBecauseFallbackAutomaticStop=18, ChargingBecauseCarCompatibilityKeepAlive=19, ChargingBecauseChargePauseNotAllowed=20, NotChargingBecauseSimulateUnplugging=22, NotChargingBecausePhaseSwitch=23, NotChargingBecauseMinPauseDuration=24) |
| lmsc       | R          | milliseconds                 | Status        | last model status change                                                            |
| mca        | R/W        | uint8                        | Config        | minChargingCurrent                                                                  |
| awc        | R/W        | uint8                        | Config        | awattar country (Austria=0, Germany=1)                                              |
| awp        | R/W        | float                        | Config        | awattarMaxPrice in ct                                                               |
| awcp       | R          | optional&lt;object&gt;       | Status        | awattar current price                                                               |
| ido        | R          | optional&lt;object&gt;       | Config        | Inverter data override                                                              |
| frm        | R          | uint8                        | Config        | roundingMode PreferPowerFromGrid=0, Default=1, PreferPowerToGrid=2                  |
| fup        | R/W        | bool                         | Config        | usePvSurplus                                                                        |
| awe        | R/W        | bool                         | Config        | useAwattar                                                                          |
| fst        | R/W        | float                        | Config        | startingPower in watts                                                              |
| fmt        | R/W        | milliseconds                 | Config        | minChargeTime in milliseconds                                                       |
| att        | R/W        | seconds                      | Config        | automatic stop time in seconds since day begin, calculation: (hours*3600)+(minutes*60)+(seconds) |
| ate        | R/W        | double                       | Config        | automatic stop energy in Wh                                                         |
| ara        | R/W        | bool                         | Config        | automatic stop remain in aWATTar                                                    |
| acp        | R/W        | bool                         | Config        | allowChargePause (car compatiblity)                                                 |
| cco        | R/W        | double                       | Config        | car consumption (only stored for app)                                               |
| esk        | R/W        | bool                         | Config        | energy set kwh (only stored for app)                                                |
| fzf        | R/W        | bool                         | Config        | zeroFeedin                                                                          |
| sh         | R/W        | float                        | Config        | stopHysteresis in W                                                                 |
| psh        | R/W        | float                        | Config        | phaseSwitchHysteresis in W                                                          |
| po         | R/W        | float                        | Config        | prioOffset in W                                                                     |
| zfo        | R/W        | float                        | Config        | zeroFeedinOffset in W                                                               |
| psmd       | R/W        | milliseconds                 | Config        | forceSinglePhaseDuration (in milliseconds)                                          |
| sumd       | R/W        | milliseconds                 | Config        | simulate unpluging duration (in milliseconds)                                       |
| mpwst      | R/W        | milliseconds                 | Config        | min phase wish switch time (in milliseconds)                                        |
| mptwt      | R/W        | milliseconds                 | Config        | min phase toggle wait time (in milliseconds)                                        |
| ferm       | R          | uint8                        | Status        | effectiveRoundingMode                                                               |
| mmp        | R          | float                        | Status        | maximumMeasuredChargingPower (debug)                                                |
| tlf        | R          | bool                         | Status        | testLadungFinished (debug)                                                          |
| tls        | R          | bool                         | Status        | testLadungStarted (debug)                                                           |
| atp        | R          | optional&lt;object&gt;       | Status        | nextTripPlanData (debug)                                                            |
| lpsc       | R          | milliseconds                 | Status        | last pv surplus calculation                                                         |
| inva       | R          | milliseconds                 | Status        | age of inverter data                                                                |
| pgrid      | R          | optional&lt;float&gt;        | Status        | pGrid in W                                                                          |
| ppv        | R          | optional&lt;float&gt;        | Status        | pPv in W                                                                            |
| pakku      | R          | optional&lt;float&gt;        | Status        | pAkku in W                                                                          |
| deltap     | R          | float                        | Status        | deltaP                                                                              |
| pnp        | R          | uint8                        | Status        | numberOfPhases                                                                      |
| deltaa     | R          | float                        | Other         | deltaA                                                                              |
| pvopt_avergagePGrid | R | float                        | Status        | averagePGrid                                                                        |
| pvopt_avergagePPV | R   | float                        | Status        | averagePPv                                                                          |
| pvopt_avergagePAkku | R | float                        | Status        | averagePAkku                                                                        |
| mci        | R/W        | milliseconds                 | Config        | minimumChargingInterval in milliseconds (0 means disabled)                          |
| mcpd       | R/W        | milliseconds                 | Config        | minChargePauseDuration in milliseconds (0 means disabled)                           |
| mcpea      | R/W        | optional&lt;milliseconds&gt; | Status        | minChargePauseEndsAt (set to null to abort current minChargePauseDuration)          |
| su         | R/W        | bool                         | Config        | simulateUnpluggingShort                                                             |
| sua        | R/W        | bool                         | Config        | simulateUnpluggingAlways                                                            |
| hsa        | R/W        | bool                         | Config        | httpStaAuthentication                                                               |
| var        | R          | uint8                        | Constant      | variant: max Ampere value of unit (11: 11kW/16A, 22: 22kW/32A)                      |
| loe        | R/W        | bool                         | Config        | Load balancing enabled                                                              |
| log        | R/W        | string                       | Config        | load_group_id                                                                       |
| lop        | R/W        | uint16                       | Config        | load_priority                                                                       |
| lof        | R/W        | uint8                        | Config        | load_fallback                                                                       |
| map        | R/W        | array                        | Config        | load_mapping (uint8_t[3])                                                           |
| upo        | R/W        | bool                         | Config        | unlock_power_outage                                                                 |
| pwm        | R          | uint8                        | Status        | phase wish mode for debugging / only for pv optimizing / used for timers later (Force_3=0, Wish_1=1, Wish_3=2) |
| lfspt      | R          | optional&lt;milliseconds&gt; | Status        | last force single phase toggle                                                      |
| fsptws     | R          | optional&lt;milliseconds&gt; | Status        | force single phase toggle wished since                                              |
| spl3       | R/W        | float                        | Config        | threePhaseSwitchLevel                                                               |
| psm        | R/W        | uint8                        | Config        | phaseSwitchMode (Auto=0, Force_1=1, Force_3=2)                                      |
| oct        | W          | string                       | Other         | firmware update trigger (must specify a branch from ocu)                            |
| ocu        | R          | array                        | Status        | list of available firmware branches                                                 |
| cwe        | R/W        | bool                         | Config        | cloud websocket enabled"                                                            |
| cus        | R          | uint8                        | Status        | Cable unlock status (Unknown=0, Unlocked=1, UnlockFailed=2, Locked=3, LockFailed=4, LockUnlockPowerout=5) |
| ffb        | R          | uint8                        | Status        | lock feedback (NoProblem=0, ProblemLock=1, ProblemUnlock=2)                         |
| fhz        | R          | optional&lt;float&gt;        | Status        | Stromnetz frequency (~50Hz) or 0 if unknown                                         |
| loa        | R          | optional&lt;uint8&gt;        | Status        | load balancing ampere                                                               |
| lot        | R/W        | uint32                       | Config        | load balancing total amp                                                            |
| loty       | R/W        | uint8                        | Config        | load balancing type (Static=0, Dynamic=1)                                           |
