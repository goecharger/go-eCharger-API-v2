[Deutsch](apikeys-de.md) &bull; English

# API Keys

| Key        | R/W        | Type                         | Category      | Description                                                                         |
| ---------- | ---------- | ---------------------------- | ------------- | ----------------------------------------------------------------------------------- |
| rst        | W          | JsonVariantConst             | Unknown       | Reset the charger and chargectrl                                                    |
| alw        | R          | bool                         | Status        | Is the car allowed to charge at all now?                                            |
| acu        | R          | optional<int>                | Status        | How many ampere is the car allowed to charge now?                                   |
| cll        | R          | legacy                       | Status        | Current limits list                                                                 |
| adi        | R          | bool                         | Status        | Is the 16A adapter used? Limits the current to 16A                                  |
| dwo        | R/W        | optional<double>             | Config        | energy limit, measured in Wh, null means disabled, not the next trip energy         |
| tpa        | R          | float                        | Status        | 30 seconds total power average (not used by next-trip, use mmp for next-trip related power) |
| sse        | R          | string                       | Constant      | serial number                                                                       |
| eto        | R          | uint64_t                     | Status        | energy_total, measured in Wh                                                        |
| wifis      | R/W        | get: legacy set: JsonArray   | Config        | wifi configurations with ssids and keys, if you only want to change the second entry, send an array with 1 empty and 1 filled wifi config object: [{}, {"ssid":"","key":""}] |
| delw       | W          | uint8_t                      | Unknown       | set this to 0-9 to delete sta config (erases ssid, key, ...)                        |
| scan       | R          | legacy                       | Status        | wifi scan result (encryptionType: OPEN=0, WEP=1, WPA_PSK=2, WPA2_PSK=3, WPA_WPA2_PSK=4, WPA2_ENTERPRISE=5, WPA3_PSK=6, WPA2_WPA3_PSK=7) |
| lwf        | R          | optional<int64_t>            | Status        | last wifi connect failed (milliseconds since boot)                                  |
| scaa       | R          | optional<int64_t>            | Status        | wifi scan age                                                                       |
| wst        | R          | uint8_t                      | Status        | WiFi STA status (IDLE_STATUS=0, NO_SSID_AVAIL=1, SCAN_COMPLETED=2, CONNECTED=3, CONNECT_FAILED=4, CONNECTION_LOST=5, DISCONNECTED=6, CONNECTING=7, DISCONNECTING=8, NO_SHIELD=9, WAITING_FOR_IP=10 (for compatibility with WiFi Shield library)) |
| wsc        | R          | uint8_t                      | Status        | WiFi STA error count                                                                |
| wsl        | R          | legacy                       | Status        | WiFi STA error messages log                                                         |
| wsms       | R          | uint8_t                      | Status        | WiFi state machine state (None=0, Scanning=1, Connecting=2, Connected=3)            |
| ccw        | R          | legacy                       | Status        | Currently connected WiFi                                                            |
| wfb        | R          | legacy                       | Status        | WiFi failed mac addresses (bssids)                                                  |
| wcb        | R          | string                       | Status        | WiFi current mac address (bssid connecting to)                                      |
| wpb        | R          | legacy                       | Status        | WiFi planned mac addresses (future bssids)                                          |
| nif        | R          | string                       | Status        | Default route                                                                       |
| dns        | R          | legacy                       | Status        | dns servers                                                                         |
| host       | R          | string                       | Status        | configured hostname                                                                 |
| wbw        | R          | unsigned int                 | Config        | WiFi Bandwidth (for both AP and STA) WIFI_BW_HT20=1, WIFI_BW_HT40=2                 |
| rssi       | R          | optional<int8_t>             | Status        | RSSI signal strength                                                                |
| wda        | R/W        | bool                         | Config        | disable AccessPoint when cloud is connected                                         |
| mia        | R          | legacy                       | Status        | Modem IP Address                                                                    |
| tse        | R/W        | bool                         | Config        | time server enabled                                                                 |
| tsss       | R          | unsigned int                 | Status        | time server sync status (RESET=0, COMPLETED=1, IN_PROGRESS=2)                       |
| tof        | R/W        | int32_t                      | Config        | timezone offset in minutes                                                          |
| tds        | R/W        | uint8_t                      | Config        | timezone daylight saving mode, None=0, EuropeanSummerTime=1, UsDaylightTime=2, AustralianDaylightTime=3 |
| tzt        | R/W        | string                       | Config        | timezone type, freetext string for app selection                                    |
| utc        | R/W        | string                       | Status        | utc time                                                                            |
| loc        | R          | string                       | Status        | local time                                                                          |
| tab        | R          | uint64_t                     | Status        | time at boot in utc in milliseconds, add rbt to get to current utc time             |
| lto        | R          | int64_t                      | Status        | local time offset in milliseconds, tab + rbt + lto = local time                     |
| led        | R          | legacy                       | Status        | LED animation                                                                       |
| lbr        | R/W        | uint8_t                      | Config        | led_bright, 0-255                                                                   |
| lmo        | R/W        | uint8_t                      | Config        | logic mode (Default=3, Awattar=4, NextTrip=5)                                       |
| ama        | R/W        | uint8_t                      | Config        | ampere_max limit                                                                    |
| tcl        | R/W        | optional<uint8_t>            | Config        | temporary current limit (does not change the user current limit, will be reset after 10min if not updated regulary) |
| die        | R/W        | bool                         | Config        | digital Input Enabled                                                               |
| dii        | R/W        | bool                         | Config        | digital Input Inverted                                                              |
| din        | R          | uint32_t                     | Status        | digital input states                                                                |
| la1        | R/W        | uint8_t                      | Config        | limit adapter 1-phase (in A)                                                        |
| la3        | R/W        | uint8_t                      | Config        | limit adapter 3-phase (in A)                                                        |
| di1        | R/W        | bool                         | Config        | digital Input 1-phase                                                               |
| pgr        | R/W        | bool                         | Config        | protect Grid Requirements                                                           |
| pdi        | R/W        | bool                         | Config        | protect Digital Input                                                               |
| ufe        | R/W        | bool                         | Config        | Underfrequency Control enabled                                                      |
| ufm        | R/W        | uint8_t                      | Config        | Underfrequency Control mode (TypeNominal=0, TypeActual=1)                           |
| ufa        | R/W        | float                        | Config        | Underfrequency Control activation threshold                                         |
| ufs        | R/W        | float                        | Config        | Underfrequency Control stop frequency                                               |
| clp        | R/W        | get: legacy set: JsonArray   | Config        | current limit presets, max. 5 entries                                               |
| bac        | R/W        | get: uint8_t set: JsonVariantConst | Config        | Button allow Current change (0=AlwaysLock, 1=LockWhenCarIsConnected, 2=LockWhenCarIsCharging, 3=NeverLock) |
| sdp        | R/W        | get: uint8_t set: JsonVariantConst | Config        | Button Allow Force change (0=AlwaysLock, 1=LockWhenCarIsConnected, 2=LockWhenCarIsCharging, 3=NeverLock) |
| bar        | R/W        | uint8_t                      | Config        | Button Allow WiFi AP reset (0=AlwaysLock, 1=LockWhenCarIsConnected, 2=LockWhenCarIsCharging, 3=NeverLock) |
| lbp        | R          | optional<int64_t>            | Config        | lastButtonPress                                                                     |
| lbl        | R          | optional<int64_t>            | Config        | lastButtonHoldLong                                                                  |
| amp        | R/W        | uint8_t                      | Config        | requestedCurrent, used for display on LED ring and logic calculations               |
| fna        | R/W        | string                       | Config        | friendlyName                                                                        |
| isgo       | R          | bool                         | Constant      | is go                                                                               |
| simo       | R          | bool                         | Config        | simplified mode                                                                     |
| aus        | R          | bool                         | Config        | is australia                                                                        |
| rdbs       | R/W        | int32_t                      | Config        | randomDelayStartScheduledCharging in seconds                                        |
| rdes       | R/W        | int32_t                      | Config        | randomDelayStopScheduledCharging in seconds                                         |
| rdbf       | R/W        | int32_t                      | Config        | randomDelayStartFlexibleTariffCharging in seconds                                   |
| rdef       | R/W        | int32_t                      | Config        | randomDelayStopFlexibleTariffCharging in seconds                                    |
| rdre       | R/W        | int32_t                      | Config        | randomDelayReconnection in seconds                                                  |
| rdpl       | R/W        | int32_t                      | Config        | randomDelayWhenPluggingCar in seconds                                               |
| rdbse      | R/W        | optional<int64_t>            | Config        | randomDelayStartScheduledChargingEndsAt (set to null to abort current randomDelayStartScheduledCharging) |
| rdese      | R/W        | optional<int64_t>            | Config        | randomDelayStopScheduledChargingEndsAt (set to null to abort current randomDelayStopScheduledCharging) |
| rdbfe      | R/W        | optional<int64_t>            | Config        | randomDelayStartFlexibleTariffChargingEndsAt (set to null to abort current randomDelayStartFlexibleTariffCharging) |
| rdefe      | R/W        | optional<int64_t>            | Config        | randomDelayStopFlexibleTariffChargingEndsAt (set to null to abort current randomDelayStopFlexibleTariffCharging) |
| rdree      | R/W        | optional<int64_t>            | Config        | randomDelayReconnectionEndsAt (set to null to abort current randomDelayReconnection) |
| rdple      | R/W        | optional<int64_t>            | Config        | randomDelayWhenPluggingCarEndsAt (set to null to abort current randomDelayWhenPluggingCar) |
| gmtr       | R/W        | int32_t                      | Config        | gridMonitoringTimeReconnection in seconds                                           |
| gsa        | R/W        | optional<int64_t>            | Status        | gridMonitoring last failure                                                         |
| rsa        | R/W        | optional<int64_t>            | Status        | rampup started at                                                                   |
| rmiv       | R/W        | float                        | Config        | reconnectionMinimumVoltage in Volt                                                  |
| rmav       | R/W        | float                        | Config        | reconnectionMaximumVoltage in Volt                                                  |
| rmif       | R/W        | float                        | Config        | reconnectionMinimumFrequency in Hz                                                  |
| rmaf       | R/W        | float                        | Config        | reconnectionMaximumFrequency in Hz                                                  |
| rsre       | R/W        | bool                         | Config        | rampupAtStartAndReconnectionEnabled                                                 |
| rsrr       | R/W        | float                        | Config        | rampupAtStartAndReconnectionRate in %/s                                             |
| cid        | R/W        | string                       | Config        | color_idle, format: #RRGGBB                                                         |
| cwc        | R/W        | string                       | Config        | color_waitcar, format: #RRGGBB                                                      |
| cch        | R/W        | string                       | Config        | color_charging, format: #RRGGBB                                                     |
| cfi        | R/W        | string                       | Config        | color_finished, format: #RRGGBB                                                     |
| ust        | R/W        | uint8_t                      | Config        | unlock_setting (Normal=0, AutoUnlock=1, AlwaysLock=2)                               |
| lck        | R          | uint8_t                      | Status        | Effective lock setting, as sent to Charge Ctrl (Normal=0, AutoUnlock=1, AlwaysLock=2, ForceUnlock=3) |
| sch_week   | R/W        | get: legacy set: JsonObject  | Config        | scheduler_weekday, control enum values: Disabled=0, Allow=1, Block=2, AllowFromGrid=3, BlockFromGrid=4 |
| sch_satur  | R/W        | get: legacy set: JsonObject  | Config        | scheduler_saturday, control enum values: Disabled=0, Allow=1, Block=2, AllowFromGrid=3, BlockFromGrid=4 |
| sch_sund   | R/W        | get: legacy set: JsonObject  | Config        | scheduler_sunday, control enum values: Disabled=0, Allow=1, Block=2, AllowFromGrid=3, BlockFromGrid=4 |
| nmo        | R/W        | bool                         | Config        | norway_mode / ground check enabled when norway mode is disabled                     |
| fsp        | R/W        | bool                         | Status        | force_single_phase                                                                  |
| lrn        | W          | uint8_t                      | Config        | set this to 0-9 to learn last read card id                                          |
| del        | W          | uint8_t                      | Unknown       | set this to 0-9 to clear card (erases card name, energy and rfid id)                |
| acs        | R/W        | uint8_t                      | Config        | access_control user setting (Open=0, Wait=1, EVCMS=2)                               |
| frc        | R/W        | uint8_t                      | Config        | forceState (Neutral=0, Off=1, On=2)                                                 |
| rbc        | R          | uint32_t                     | Status        | reboot_counter                                                                      |
| rbt        | R          | int64_t                      | Status        | time since boot in milliseconds                                                     |
| car        | R          | optional<uint8_t>            | Status        | charge ctrl car state, null if no connection to chargectrl established (Unknown/Error=0, Idle=1, Charging=2, WaitCar=3, Complete=4, Error=5) |
| err        | R          | optional<uint8_t>            | Status        | charge ctrl error, null if no connection to charge ctrl established (None=0, FiAc=1, FiDc=2, Phase=3, Overvolt=4, Overamp=5, Diode=6, PpInvalid=7, GndInvalid=8, ContactorStuck=9, ContactorMiss=10, StatusLockStuckOpen=12, StatusLockStuckLocked=13, FiUnknown=14, Unknown=15, Overtemp=16, NoComm=17, CpInvalid=18) |
| cbl        | R          | optional<int>                | Status        | cable_current_limit in A                                                            |
| pha        | R          | legacy                       | Status        | phases                                                                              |
| wh         | R          | double                       | Status        | energy in Wh since car connected                                                    |
| whs        | R          | double                       | Status        | energy SOLAR in Wh since car connected                                              |
| whb        | R          | double                       | Status        | energy BATTERY in Wh since car connected                                            |
| whg        | R          | double                       | Status        | energy GRID in Wh since car connected                                               |
| who        | R          | double                       | Status        | energy OTHER in Wh since car connected                                              |
| ws         | R          | optional<double>             | Status        | power SOLAR in W                                                                    |
| wb         | R          | optional<double>             | Status        | power BATTERY in W                                                                  |
| wg         | R          | optional<double>             | Status        | power GRID in W                                                                     |
| wo         | R          | optional<double>             | Status        | power OTHER in W                                                                    |
| trx        | R/W        | optional<uint8_t>            | Status        | transaction, null when no transaction, 0 when without card, otherwise cardIndex + 1 (1: 0. card, 2: 1. card, ...) |
| evt        | R          | optional<string>             | Status        | EVCMS transaction id                                                                |
| fwv        | R          | string                       | Status        | FW_VERSION                                                                          |
| oem        | R          | string                       | Constant      | OEM manufacturer                                                                    |
| typ        | R          | string                       | Constant      | Devicetype                                                                          |
| lse        | R/W        | bool                         | Config        | led_save_energy                                                                     |
| cdi        | R          | legacy                       | Status        | charging duration info (null=no charging in progress, type=0 counter going up, type=1 duration in ms) |
| lccfi      | R          | optional<int64_t>            | Status        | lastCarStateChangedFromIdle (in ms)                                                 |
| lccfc      | R          | optional<int64_t>            | Status        | lastCarStateChangedFromCharging (in ms)                                             |
| lcctc      | R          | optional<int64_t>            | Status        | lastCarStateChangedToCharging (in ms)                                               |
| tma        | R          | legacy                       | Status        | temperature sensors                                                                 |
| amt        | R          | int                          | Status        | temperatureCurrentLimit                                                             |
| nrg        | R          | legacy                       | Status        | energy array, U (L1, L2, L3, N), I (L1, L2, L3), P (L1, L2, L3, N, Total), pf (L1, L2, L3, N) |
| modelStatus | R          | uint8_t                      | Status        | Reason why we allow charging or not right now (NotChargingBecauseNoChargeCtrlData=0, NotChargingBecauseOvertemperature=1, NotChargingBecauseAccessControl=2, ChargingBecauseForceStateOn=3, NotChargingBecauseForceStateOff=4, NotChargingBecauseScheduler=5, NotChargingBecauseEnergyLimit=6, ChargingBecauseAwattarPriceLow=7, ChargingBecauseAutomaticStopTestLadung=8, ChargingBecauseAutomaticStopNotEnoughTime=9, ChargingBecauseAutomaticStop=10, ChargingBecauseAutomaticStopNoClock=11, ChargingBecausePvSurplus=12, ChargingBecauseFallbackV2Default=13, ChargingBecauseFallbackV2Scheduler=14, ChargingBecauseFallbackDefault=15, NotChargingBecauseFallbackV2Awattar=16, NotChargingBecauseFallbackAwattar=17, NotChargingBecauseFallbackAutomaticStop=18, ChargingBecauseCarCompatibilityKeepAlive=19, ChargingBecauseChargePauseNotAllowed=20, NotChargingBecauseSimulateUnplugging=22, NotChargingBecausePhaseSwitch=23, NotChargingBecauseMinPauseDuration=24, NotChargingBecauseError=26, NotChargingBecauseLoadManagementDoesntWant=27, NotChargingBecauseOcppDoesntWant=28, NotChargingBecauseReconnectDelay=29, NotChargingBecauseAdapterBlocking=30, NotChargingBecauseUnderfrequencyControl=31, NotChargingBecauseUnbalancedLoad=32, ChargingBecauseDischargingPvBattery=33, NotChargingBecauseGridMonitoring=34, NotChargingBecauseOcppFallback=35, NotChargingBecauseOcppInoperable=37) |
| lmsc       | R          | int64_t                      | Status        | last model status change                                                            |
| mca        | R/W        | uint8_t                      | Config        | minChargingCurrent                                                                  |
| awc        | R/W        | uint16_t                     | Config        | awattar country (Austria=0, Germany=1,...)                                          |
| awp        | R/W        | float                        | Config        | awattarMaxPrice in ct                                                               |
| awcp       | R          | legacy                       | Status        | awattar current price                                                               |
| awpl       | W          | get: legacy set: JsonArray   | Status        | awattar price list, timestamps are measured in unix-time, seconds since 1970        |
| frm        | R/W        | uint8_t                      | Config        | roundingMode PreferPowerFromGrid=0, Default=1, PreferPowerToGrid=2                  |
| fup        | R/W        | bool                         | Config        | usePvSurplus                                                                        |
| awe        | R/W        | bool                         | Config        | useAwattar                                                                          |
| fst        | R/W        | float                        | Config        | startingPower in watts                                                              |
| fmt        | R/W        | int32_t                      | Config        | minChargeTime in milliseconds                                                       |
| att        | R/W        | int32_t                      | Config        | automatic stop time in seconds since day begin, calculation: (hours*3600)+(minutes*60)+(seconds) |
| ate        | R/W        | double                       | Config        | nextTripEnergy in Wh                                                                |
| ara        | R/W        | bool                         | Config        | automatic stop remain in aWATTar                                                    |
| acp        | R/W        | bool                         | Config        | allowChargePause                                                                    |
| cco        | R/W        | double                       | Config        | car consumption (for app)                                                           |
| esk        | R/W        | bool                         | Config        | energy set kwh (for app)                                                            |
| fzf        | R/W        | bool                         | Config        | zeroFeedin                                                                          |
| pgt        | R/W        | float                        | Config        | pGridTarget in W                                                                    |
| sh         | R/W        | float                        | Config        | stopHysteresis in W                                                                 |
| psh        | R/W        | float                        | Config        | phaseSwitchHysteresis in W                                                          |
| po         | R/W        | float                        | Config        | prioOffset in W                                                                     |
| zfo        | R/W        | float                        | Config        | zeroFeedinOffset in W                                                               |
| psmd       | R/W        | int32_t                      | Config        | forceSinglePhaseDuration (in milliseconds)                                          |
| sumd       | R/W        | int32_t                      | Config        | simulate unpluging duration (in milliseconds)                                       |
| mpwst      | R/W        | int32_t                      | Config        | min phase wish switch time (in milliseconds)                                        |
| mptwt      | R/W        | int32_t                      | Config        | min phase toggle wait time (in milliseconds)                                        |
| mmp        | R          | float                        | Status        | maximumMeasuredChargingPower                                                        |
| tlf        | R          | bool                         | Status        | testLadungFinished                                                                  |
| tls        | R          | optional<int64_t>            | Status        | testLadungStarted                                                                   |
| lpc        | R          | optional<int64_t>            | Status        | lastPvCalculation                                                                   |
| atp        | R          | legacy                       | Status        | nextTripPlanData                                                                    |
| lpsc       | R          | optional<int64_t>            | Status        | last pv surplus calcuation                                                          |
| ids        | W          | optional<JsonObject>         | Status        | inverter data setter {"pGrid": 1000., "pPv": 1000., "pAkku": 1000.}                 |
| inva       | R          | optional<int64_t>            | Status        | age of inverter data                                                                |
| pgrid      | R          | optional<float>              | Status        | pGrid in W                                                                          |
| ppv        | R          | optional<float>              | Status        | pPv in W                                                                            |
| pakku      | R          | optional<float>              | Status        | pAkku in W                                                                          |
| dsrc       | R          | optional<string>             | Status        | inverter data source                                                                |
| deltap     | R          | float                        | Status        | deltaP                                                                              |
| pnp        | R          | uint8_t                      | Status        | numberOfPhases                                                                      |
| deltaa     | R          | float                        | Unknown       | deltaA                                                                              |
| pvopt_averagePGrid | R          | float                        | Status        | averagePGrid                                                                        |
| pvopt_averagePPv | R          | float                        | Status        | averagePPv                                                                          |
| pvopt_averagePAkku | R          | float                        | Status        | averagePAkku                                                                        |
| ct         | R/W        | string                       | Config        | car type, free text string (max. 64 characters)                                     |
| mci        | R/W        | int32_t                      | Config        | minimumChargingInterval in milliseconds (0 means disabled)                          |
| mcpd       | R/W        | int32_t                      | Config        | minChargePauseDuration in milliseconds (0 means disabled)                           |
| mcpea      | R/W        | optional<int64_t>            | Config        | minChargePauseEndsAt (set to null to abort current minChargePauseDuration)          |
| su         | R/W        | bool                         | Config        | simulateUnpluggingShort                                                             |
| sua        | R/W        | bool                         | Config        | simulateUnpluggingAlways                                                            |
| hsa        | W          | bool                         | Config        | httpStaAuthentication                                                               |
| var        | R          | uint8_t                      | Constant      | variant: max Ampere value of unit (11: 11kW/16A, 22: 22kW/32A)                      |
| loe        | R/W        | bool                         | Config        | Load balancing enabled                                                              |
| log        | R/W        | string                       | Config        | load_group_id                                                                       |
| lop        | R/W        | uint16_t                     | Config        | load_priority                                                                       |
| lopr       | R/W        | bool                         | Config        | load balancing protected                                                            |
| lof        | R/W        | uint8_t                      | Config        | load_fallback                                                                       |
| map        | R/W        | get: legacy set: JsonArray   | Config        | load_mapping (uint8_t[3])                                                           |
| upo        | R/W        | bool                         | Config        | unlock_power_outage                                                                 |
| pwm        | R          | uint8_t                      | Status        | phase wish mode for debugging / only for pv optimizing / used for timers later (Force_3=0, Wish_1=1, Wish_3=2) |
| lfspt      | R          | optional<int64_t>            | Status        | last force single phase toggle                                                      |
| fsptws     | R          | optional<int64_t>            | Status        | force single phase toggle wished since                                              |
| spl3       | R/W        | float                        | Config        | threePhaseSwitchLevel                                                               |
| oct        | W          | JsonVariantConst             | Config        | ota from cloud url trigger                                                          |
| ocu        | R          | get: legacy set: JsonVariantConst | Config        | ota from cloud url, url to download new firmware code from                          |
| cwe        | R/W        | bool                         | Config        | cloud websocket enabled                                                             |
| clea       | R          | optional<int64_t>            | Status        | Cloud last error (age)                                                              |
| cle        | R          | optional<string>             | Status        | Cloud last error                                                                    |
| cus        | R          | uint8_t                      | Status        | Cable unlock status (Unknown=0, Unlocked=1, UnlockFailed=2, Locked=3, LockFailed=4, LockUnlockPowerout=5) |
| ffb        | R          | uint8_t                      | Status        | lock feedback (NoProblem=0, ProblemLock=1, ProblemUnlock=2)                         |
| fhz        | R          | optional<float>              | Status        | Stromnetz frequency (~50Hz) or 0 if unknown                                         |
| avgfhz     | R          | optional<float>              | Status        | Stromnetz average frequency (~50Hz)                                                 |
| loa        | R          | get: optional<uint8_t> set: uint8_t | Status        | load balancing ampere                                                               |
| lot        | R/W        | get: legacy set: JsonVariantConst | Config        | load balancing total amp                                                            |
| loty       | R/W        | get: uint8_t set: JsonVariantConst | Config        | load balancing type (Static=false, Dynamic=true)                                    |
| cards      | R/W        | get: legacy set: JsonArray   | Config        | RFID cards array of objects, if you only want to change the second entry, send an array with 1 empty and 1 filled card config object: [{}, {"name":"","energy":"","rfid":""}] |
| smd        | R          | legacy                       | Status        | smart meter data                                                                    |
| men        | R/W        | bool                         | Config        | modbus slave enabled                                                                |
| msp        | R/W        | uint16_t                     | Config        | modbus slave port (requires off/on toggle)                                          |
| msb        | R/W        | bool                         | Config        | modbus slave swap bytes                                                             |
| msr        | R/W        | bool                         | Config        | modbus slave swap registers                                                         |
| data       | R          | string                       | Status        | grafana token from cloud for app                                                    |
| dll        | R          | string                       | Status        | download link for app csv export                                                    |
| hai        | R/W        | bool                         | Config        | httpApiEnabled (allows /api/status and /api/set requests)                           |
| hla        | R/W        | bool                         | Config        | httpLegacyApiEnabled (allows /status and /mqtt requests)                            |
| mce        | R/W        | bool                         | Config        | MQTT enabled                                                                        |
| mcu        | R/W        | string                       | Config        | MQTT broker url                                                                     |
| mcr        | R/W        | bool                         | Config        | MQTT readonly (don't allow api writes from mqtt broker)                             |
| mtp        | R/W        | get: string set: optional<string> | Config        | MQTT topic prefix (set to null to reset back to the default)                        |
| mht        | R/W        | get: string set: optional<string> | Config        | MQTT homeassistant topic prefix (set to null to reset back to the default)          |
| mhe        | R/W        | bool                         | Config        | MQTT enable homeassistant discovery                                                 |
| mqg        | R/W        | bool                         | Config        | MQTT useGlobalCaStore                                                               |
| mqcn       | R/W        | bool                         | Config        | MQTT skipCertCommonNameCheck                                                        |
| mqss       | R/W        | bool                         | Config        | MQTT skipServerVerification                                                         |
| mcs        | R          | bool                         | Status        | MQTT started                                                                        |
| mcc        | R          | bool                         | Status        | MQTT connected                                                                      |
| mcca       | R          | optional<int64_t>            | Status        | MQTT connected (age)                                                                |
| mlr        | R          | optional<string>             | Status        | MQTT last error                                                                     |
| mlra       | R          | optional<int64_t>            | Status        | MQTT last error (age)                                                               |
| ocppe      | R/W        | bool                         | Config        | OCPP enabled                                                                        |
| ocppu      | R/W        | string                       | Config        | OCPP server url                                                                     |
| ocppf      | R/W        | optional<uint8_t>            | Config        | OCPP fallback current                                                               |
| ocppg      | R/W        | bool                         | Config        | OCPP useGlobalCaStore                                                               |
| ocppcn     | R/W        | bool                         | Config        | OCPP skipCertCommonNameCheck                                                        |
| ocppss     | R/W        | bool                         | Config        | OCPP skipServerVerification                                                         |
| ocpps      | R          | bool                         | Status        | OCPP started                                                                        |
| ocppc      | R          | bool                         | Status        | OCPP connected                                                                      |
| ocppca     | R          | optional<int64_t>            | Status        | OCPP connected (age)                                                                |
| ocppa      | R          | bool                         | Status        | OCPP connected and accepted                                                         |
| ocppaa     | R          | optional<int64_t>            | Status        | OCPP connected and accepted (age)                                                   |
| ocppti     | R/W        | optional<int>                | Config        | OCPP transaction id                                                                 |
| ocppte     | R          | optional<int64_t>            | Config        | OCPP transaction ended at (timestamp)                                               |
| ocppao     | R/W        | bool                         | Config        | OCPP AllowOfflineTxForUnknownId                                                     |
| ocpplo     | R/W        | bool                         | Config        | OCPP LocalAuthorizeOffline                                                          |
| ocppla     | R/W        | bool                         | Config        | OCPP LocalAuthListEnabled                                                           |
| orsch      | R/W        | bool                         | Config        | OCPP requires same card to halt transactions (as a compatibility mode for shitty backends that do not want to follow the ocpp standard) |
| ocpph      | R/W        | int32_t                      | Config        | ocppHeartbeatInterval                                                               |
| ocppi      | R/W        | int32_t                      | Config        | ocppMeterValueSampleInterval                                                        |
| ocppai     | R/W        | int32_t                      | Config        | ocppClockAlignedDataInterval                                                        |
| ocppd      | R/W        | string                       | Config        | OCPP dummy card id (used when no card has been used and charging is already allowed / starting) |
| ocppr      | R/W        | bool                         | Config        | OCPP rotate phases on charger                                                       |
| ocppcm     | R/W        | uint8_t                      | Status        | OCPP LocalAuthListEnabled                                                           |
| ocpplea    | R          | optional<int64_t>            | Status        | OCPP last error (age)                                                               |
| ocpple     | R          | optional<string>             | Status        | OCPP last error                                                                     |
| ocpprl     | R/W        | bool                         | Config        | OCPP remote log                                                                     |
| ocppcs     | R          | uint8_t                      | Status        | OCPP connector status (0=Available, 1=Preparing, 2=Charging, 3=SuspendedEVSE, 4=SuspendedEV, 5=Finishing, 6=Reserved, 7=Unavailable, 8=Faulted) |
| ocppmp     | R          | legacy                       | Status        | ocpp chargepoint max profiles                                                       |
| ocppdp     | R          | legacy                       | Status        | ocpp chargepoint default profiles                                                   |
| ocpptp     | R          | legacy                       | Status        | ocpp tx profiles                                                                    |
| rde        | R/W        | bool                         | Config        | send rfid serial to cloud/api/mqtt (enable lri api key to show rfid numbers)        |
| lri        | R          | optional<string>             | Status        | last rfid id (only available when sendRfid)                                         |
| tsi        | R          | optional<string>             | Status        | transaction start rfidid (only available when sendRfid)                             |
| lrc        | R          | optional<uint8_t>            | Status        | last rfid card index                                                                |
| lrr        | R          | optional<int64_t>            | Status        | last rfid read (milliseconds since boot)                                            |
| cmse       | R          | bool                         | Config        | controllerMdnsScanEnabled, set to false to completely disable any MDNS searches (debugging) |
| cmmr       | R          | uint16_t                     | Config        | controllerMdnsMaxResults                                                            |
| cms        | R          | string                       | Config        | controllerMdnsService                                                               |
| cmp        | R          | string                       | Config        | controllerMdnsProto                                                                 |
| pco        | R/W        | string                       | Config        | controllerCloudKey                                                                  |
| lcs        | R          | int64_t                      | Status        | last controller scan timestamp in milliseconds since boot time                      |
| csa        | R          | bool                         | Status        | controller scan active (set to true to start scan)                                  |
| ctrls      | R          | legacy                       | Status        | Controllers search result                                                           |
| ccd        | R          | legacy                       | Status        | Connected controller data                                                           |
