[Deutsch](apikeys-de.md) &bull; English

# API Keys

| Key        | R/W        | Type                         | Category      | Description                                                                         |
| ---------- | ---------- | ---------------------------- | ------------- | ----------------------------------------------------------------------------------- |
| acp | R/W | TYPE | Config | allowChargePause |
| acs | R/W | TYPE | Config | access_control user setting (Open=0, Wait=1, EVCMS=2) |
| acu | R | TYPE | Status | How many ampere is the car allowed to charge now? |
| adi | R | TYPE | Status | Is the 16A adapter used? Limits the current to 16A |
| alw | R | TYPE | Status | Is the car allowed to charge at all now? |
| ama | R/W | TYPE | Config | ampere_max limit |
| amp | R/W | TYPE | Config | requestedCurrent, used for display on LED ring and logic calculations |
| amt | R | TYPE | Status | temperatureCurrentLimit |
| ara | R/W | TYPE | Config | automatic stop remain in aWATTar |
| ate | R/W | TYPE | Config | nextTripEnergy in Wh |
| atp | R | TYPE | Status | nextTripPlanData |
| att | R/W | TYPE | Config | automatic stop time in seconds since day begin, calculation: (hours*3600)+(minutes*60)+(seconds) |
| avgfhz | R | TYPE | Status | Stromnetz average frequency (~50Hz) |
| awc | R/W | TYPE | Config | awattar country (Austria=0, Germany=1,...) |
| awcp | R | TYPE | Status | awattar current price |
| awe | R/W | TYPE | Config | useAwattar |
| awp | R/W | TYPE | Config | awattarMaxPrice in ct |
| awpl | W | TYPE | Status | awattar price list, timestamps are measured in unix-time, seconds since 1970 |
| bac | R/W | TYPE | Config | Button allow Current change (0=AlwaysLock, 1=LockWhenCarIsConnected, 2=LockWhenCarIsCharging, 3=NeverLock) |
| bar | R/W | TYPE | Config | Button Allow WiFi AP reset (0=AlwaysLock, 1=LockWhenCarIsConnected, 2=LockWhenCarIsCharging, 3=NeverLock) |
| car | R | TYPE | Status | charge ctrl car state, null if no connection to chargectrl established (Unknown/Error=0, Idle=1, Charging=2, WaitCar=3, Complete=4, Error=5) |
| cards | R/W | TYPE | Config | RFID cards array of objects, if you only want to change the second entry, send an array with 1 empty and 1 filled card config object: [{}, {"name":"","energy":"","rfid":""}] |
| cbl | R | TYPE | Status | cable_current_limit in A |
| ccd | R | TYPE | Status | Connected controller data || cch | R/W | TYPE | Config | color_charging, format: #RRGGBB |
| cco | R/W | TYPE | Config | car consumption (for app) |
| ccw | R | TYPE | Status | Currently connected WiFi |
| cdi | R | TYPE | Status | charging duration info (null=no charging in progress, type=0 counter going up, type=1 duration in ms) |
| cfi | R/W | TYPE | Config | color_finished, format: #RRGGBB |
| cid | R/W | TYPE | Config | color_idle, format: #RRGGBB |
| cle | R | TYPE | Status | Cloud last error |
| clea | R | TYPE | Status | Cloud last error (age) |
| cll | R | TYPE | Status | Current limits list |
| clp | R/W | TYPE | Config | current limit presets, max. 5 entries |
| cmmr | R | TYPE | Config | controllerMdnsMaxResults |
| cmp | R | TYPE | Config | controllerMdnsProto |
| cms | R | TYPE | Config | controllerMdnsService |
| cmse | R | TYPE | Config | controllerMdnsScanEnabled, set to false to completely disable any MDNS searches (debugging) |
| csa | R | TYPE | Status | controller scan active |
| ct | R/W | TYPE | Config | car type, free text string (max. 64 characters) |
| ctrls | R | TYPE | Status | Controllers search result |
| cus | R | TYPE | Status | Cable unlock status (Unknown=0, Unlocked=1, UnlockFailed=2, Locked=3, LockFailed=4, LockUnlockPowerout=5) |
| cwc | R/W | TYPE | Config | color_waitcar, format: #RRGGBB |
| cwe | R/W | TYPE | Config | cloud websocket enabled |
| data | R | TYPE | Status | grafana token from cloud for app |
| del | W | TYPE | Unknown | set this to 0-9 to clear card (erases card name, energy and rfid id) |
| deltaa | R | TYPE | Unknown | deltaA |
| deltap | R | TYPE | Status | deltaP |
| delw | W | TYPE | Unknown | set this to 0-9 to delete sta config (erases ssid, key, ...) |
| di1 | R/W | TYPE | Config | digital Input 1-phase |
| die | R/W | TYPE | Config | digital Input Enabled |
| dii | R/W | TYPE | Config | digital Input Inverted |
| dll | R | TYPE | Status | download link for app csv export |
| dns | R | TYPE | Status | dns servers |
| dsrc | R | TYPE | Status | inverter data source |
| dwo | R/W | TYPE | Config | energy limit, measured in Wh, null means disabled, not the next trip energy |
| err | R | TYPE | Status | charge ctrl error, null if no connection to charge ctrl established (None=0, FiAc=1, FiDc=2, Phase=3, Overvolt=4, Overamp=5, Diode=6, PpInvalid=7, GndInvalid=8, ContactorStuck=9, ContactorMiss=10, StatusLockStuckOpen=12, StatusLockStuckLocked=13, FiUnknown=14, Unknown=15, Overtemp=16, NoComm=17, CpInvalid=18) |
| esk | R/W | TYPE | Config | energy set kwh (for app) |
| eto | R | TYPE | Status | energy_total, measured in Wh |
| ffb | R | TYPE | Status | lock feedback (NoProblem=0, ProblemLock=1, ProblemUnlock=2) |
| fhz | R | TYPE | Status | Stromnetz frequency (~50Hz) or 0 if unknown |
| fmt | R/W | TYPE | Config | minChargeTime in milliseconds |
| fna | R/W | TYPE | Config | friendlyName |
| frc | R/W | TYPE | Config | forceState (Neutral=0, Off=1, On=2) |
| frm | R/W | TYPE | Config | roundingMode PreferPowerFromGrid=0, Default=1, PreferPowerToGrid=2 |
| fsp | R/W | TYPE | Status | force_single_phase |
| fsptws | R | TYPE | Status | force single phase toggle wished since |
| fst | R/W | TYPE | Config | startingPower in watts |
| fup | R/W | TYPE | Config | usePvSurplus |
| fwv | R | TYPE | Status | FW_VERSION |
| fzf | R/W | TYPE | Config | zeroFeedin |
| gmtr | R/W | TYPE | Config | gridMonitoringTimeReconnection in seconds |
| gsa | R/W | TYPE | Status | gridMonitoring last failure |
| hai | R/W | TYPE | Config | httpApiEnabled (allows /api/status and /api/set requests) |
| hla | R/W | TYPE | Config | httpLegacyApiEnabled (allows /status and /mqtt requests) |
| host | R | TYPE | Status | configured hostname |
| hsa | W | TYPE | Config | httpStaAuthentication |
| ids | W | TYPE | Status | inverter data setter {"pGrid": 1000., "pPv": 1000., "pAkku": 1000.} |
| inva | R | TYPE | Status | age of inverter data |
| la1 | R/W | TYPE | Config | limit adapter 1-phase (in A) |
| la3 | R/W | TYPE | Config | limit adapter 3-phase (in A) |
| lbl | R | TYPE | Config | lastButtonHoldLong |
| lbp | R | TYPE | Config | lastButtonPress |
| lbr | R/W | TYPE | Config | led_bright, 0-255 |
| lccfc | R | TYPE | Status | lastCarStateChangedFromCharging (in ms) |
| lccfi | R | TYPE | Status | lastCarStateChangedFromIdle (in ms) |
| lcctc | R | TYPE | Status | lastCarStateChangedToCharging (in ms) |
| lck | R | TYPE | Status | Effective lock setting, as sent to Charge Ctrl (Normal=0, AutoUnlock=1, AlwaysLock=2, ForceUnlock=3) |
| lcs | R | TYPE | Status | last controller scan timestamp in milliseconds since boot time |
| led | R | TYPE | Status | LED animation |
| lfspt | R | TYPE | Status | last force single phase toggle |
| lmo | R/W | TYPE | Config | logic mode (Default=3, Awattar=4, NextTrip=5) |
| lmsc | R | TYPE | Status | last model status change |
| loa | R | TYPE | Status | load balancing ampere |
| loc | R | TYPE | Status | local time |
| loe | R/W | TYPE | Config | Load balancing enabled |
| lof | R/W | TYPE | Config | load_fallback |
| log | R/W | TYPE | Config | load_group_id |
| lop | R/W | TYPE | Config | load_priority |
| lopr | R/W | TYPE | Config | load balancing protected |
| lot | R/W | TYPE | Config | load balancing total amp |
| loty | R/W | TYPE | Config | load balancing type (Static=false, Dynamic=true) |
| lpsc | R | TYPE | Status | last pv surplus calcuation |
| lrc | R | TYPE | Status | last rfid card index |
| lri | R | TYPE | Status | last rfid id (only available when sendRfid) |
| lrn | W | TYPE | Config | set this to 0-9 to learn last read card id |
| lrr | R | TYPE | Status | last rfid read (milliseconds since boot) |
| lse | R/W | TYPE | Config | led_save_energy |
| lto | R | TYPE | Status | local time offset in milliseconds, tab + rbt + lto = local time |
| lwf | R | TYPE | Status | last wifi connect failed (milliseconds since boot) |
| map | R/W | TYPE | Config | load_mapping (uint8_t[3]) |
| mca | R/W | TYPE | Config | minChargingCurrent |
| mcc | R | TYPE | Status | MQTT connected |
| mcca | R | TYPE | Status | MQTT connected (age) |
| mce | R/W | TYPE | Config | MQTT enabled |
| mci | R/W | TYPE | Config | minimumChargingInterval in milliseconds (0 means disabled) |
| mcpd | R/W | TYPE | Config | minChargePauseDuration in milliseconds (0 means disabled) |
| mcpea | R/W | TYPE | Config | minChargePauseEndsAt (set to null to abort current minChargePauseDuration) |
| mcr | R/W | TYPE | Config | MQTT readonly (don't allow api writes from mqtt broker) |
| mcs | R | TYPE | Status | MQTT started |
| mcu | R/W | TYPE | Config | MQTT broker url |
| men | R/W | TYPE | Config | modbus slave enabled |
| mhe | R/W | TYPE | Config | MQTT enable homeassistant discovery |
| mht | R/W | TYPE | Config | MQTT homeassistant topic prefix (set to null to reset back to the default) |
| mlr | R | TYPE | Status | MQTT last error |
| mlra | R | TYPE | Status | MQTT last error (age) |
| mmp | R | TYPE | Status | maximumMeasuredChargingPower |
| modelStatus | R | TYPE | Status | Reason why we allow charging or not right now (NotChargingBecauseNoChargeCtrlData=0, NotChargingBecauseOvertemperature=1, NotChargingBecauseAccessControl=2, ChargingBecauseForceStateOn=3, NotChargingBecauseForceStateOff=4, NotChargingBecauseScheduler=5, NotChargingBecauseEnergyLimit=6, ChargingBecauseAwattarPriceLow=7, ChargingBecauseAutomaticStopTestLadung=8, ChargingBecauseAutomaticStopNotEnoughTime=9, ChargingBecauseAutomaticStop=10, ChargingBecauseAutomaticStopNoClock=11, ChargingBecausePvSurplus=12, ChargingBecauseFallbackV2Default=13, ChargingBecauseFallbackV2Scheduler=14, ChargingBecauseFallbackDefault=15, NotChargingBecauseFallbackV2Awattar=16, NotChargingBecauseFallbackAwattar=17, NotChargingBecauseFallbackAutomaticStop=18, ChargingBecauseCarCompatibilityKeepAlive=19, ChargingBecauseChargePauseNotAllowed=20, NotChargingBecauseSimulateUnplugging=22, NotChargingBecausePhaseSwitch=23, NotChargingBecauseMinPauseDuration=24, NotChargingBecauseError=26, NotChargingBecauseLoadManagementDoesntWant=27, NotChargingBecauseOcppDoesntWant=28, NotChargingBecauseReconnectDelay=29, NotChargingBecauseAdapterBlocking=30, NotChargingBecauseUnderfrequencyControl=31, NotChargingBecauseUnbalancedLoad=32, ChargingBecauseDischargingPvBattery=33, NotChargingBecauseGridMonitoring=34, NotChargingBecauseOcppFallback=35) |
| mptwt | R/W | TYPE | Config | min phase toggle wait time (in milliseconds) |
| mpwst | R/W | TYPE | Config | min phase wish switch time (in milliseconds) |
| mqcn | R/W | TYPE | Config | MQTT skipCertCommonNameCheck |
| mqg | R/W | TYPE | Config | MQTT useGlobalCaStore |
| mqss | R/W | TYPE | Config | MQTT skipServerVerification |
| msb | R/W | TYPE | Config | modbus slave swap bytes |
| msp | R/W | TYPE | Config | modbus slave port (requires off/on toggle) |
| msr | R/W | TYPE | Config | modbus slave swap registers |
| mtp | R/W | TYPE | Config | MQTT topic prefix (set to null to reset back to the default) |
| nif | R | TYPE | Status | Default route |
| nmo | R/W | TYPE | Config | norway_mode / ground check enabled when norway mode is disabled |
| nrg | R | TYPE | Status | energy array, U (L1, L2, L3, N), I (L1, L2, L3), P (L1, L2, L3, N, Total), pf (L1, L2, L3, N) |
| ocppa | R | TYPE | Status | OCPP connected and accepted |
| ocppaa | R | TYPE | Status | OCPP connected and accepted (age) |
| ocppai | R/W | TYPE | Config | ocppClockAlignedDataInterval |
| ocppao | R/W | TYPE | Status | OCPP AllowOfflineTxForUnknownId |
| ocppc | R | TYPE | Status | OCPP connected |
| ocppca | R | TYPE | Status | OCPP connected (age) |
| ocppcm | R/W | TYPE | Status | OCPP LocalAuthListEnabled |
| ocppcn | R/W | TYPE | Config | OCPP skipCertCommonNameCheck |
| ocppcs | R | TYPE | Status | OCPP connector status (0=Available, 1=Preparing, 2=Charging, 3=SuspendedEVSE, 4=SuspendedEV, 5=Finishing, 6=Reserved, 7=Unavailable, 8=Faulted) |
| ocppd | R/W | TYPE | Config | OCPP dummy card id (used when no card has been used and charging is already allowed / starting) |
| ocppe | R/W | TYPE | Config | OCPP enabled |
| ocppf | R/W | TYPE | Config | OCPP fallback current |
| ocppg | R/W | TYPE | Config | OCPP useGlobalCaStore |
| ocpph | R/W | TYPE | Config | ocppHeartbeatInterval |
| ocppi | R/W | TYPE | Config | ocppMeterValueSampleInterval |
| ocppla | R/W | TYPE | Status | OCPP LocalAuthListEnabled |
| ocpple | R | TYPE | Status | OCPP last error |
| ocpplea | R | TYPE | Status | OCPP last error (age) |
| ocpplo | R/W | TYPE | Status | OCPP LocalAuthorizeOffline |
| ocppr | R/W | TYPE | Config | OCPP rotate phases on charger |
| ocpprl | R/W | TYPE | Config | OCPP remote log |
| ocpps | R | TYPE | Status | OCPP started |
| ocppss | R/W | TYPE | Config | OCPP skipServerVerification |
| ocppti | R/W | TYPE | Status | OCPP transaction id |
| ocppu | R/W | TYPE | Config | OCPP server url |
| oct | W | TYPE | Config | ota from cloud url trigger |
| ocu | R | TYPE | Config | ota from cloud url, url to download new firmware code from |
| oem | R | TYPE | Constant | OEM manufacturer |
| pakku | R | TYPE | Status | pAkku in W |
| pco | R | TYPE | Config | controllerCloudKey |
| pdi | R/W | TYPE | Config | protect Digital Input |
| pgr | R/W | TYPE | Config | protect Grid Requirements |
| pgrid | R | TYPE | Status | pGrid in W |
| pgt | R/W | TYPE | Config | pGridTarget in W |
| pha | R | TYPE | Status | phases |
| pnp | R | TYPE | Status | numberOfPhases |
| po | R/W | TYPE | Config | prioOffset in W |
| ppv | R | TYPE | Status | pPv in W |
| psh | R/W | TYPE | Config | phaseSwitchHysteresis in W |
| psmd | R/W | TYPE | Config | forceSinglePhaseDuration (in milliseconds) |
| pvopt_averagePAkku | R | TYPE | Status | averagePAkku |
| pvopt_averagePGrid | R | TYPE | Status | averagePGrid |
| pvopt_averagePPv | R | TYPE | Status | averagePPv |
| pwm | R | TYPE | Status | phase wish mode for debugging / only for pv optimizing / used for timers later (Force_3=0, Wish_1=1, Wish_3=2) |
| rbc | R | TYPE | Status | reboot_counter |
| rbt | R | TYPE | Status | time since boot in milliseconds |
| rdbf | R/W | TYPE | Config | randomDelayStartFlexibleTariffCharging in seconds |
| rdbfe | R/W | TYPE | Config | randomDelayStartFlexibleTariffChargingEndsAt (set to null to abort current randomDelayStartFlexibleTariffCharging) |
| rdbs | R/W | TYPE | Config | randomDelayStartScheduledCharging in seconds |
| rdbse | R/W | TYPE | Config | randomDelayStartScheduledChargingEndsAt (set to null to abort current randomDelayStartScheduledCharging) |
| rde | R/W | TYPE | Config | send rfid serial to cloud/api/mqtt (enable lri api key to show rfid numbers) |
| rdef | R/W | TYPE | Config | randomDelayStopFlexibleTariffCharging in seconds |
| rdefe | R/W | TYPE | Config | randomDelayStopFlexibleTariffChargingEndsAt (set to null to abort current randomDelayStopFlexibleTariffCharging) |
| rdes | R/W | TYPE | Config | randomDelayStopScheduledCharging in seconds |
| rdese | R/W | TYPE | Config | randomDelayStopScheduledChargingEndsAt (set to null to abort current randomDelayStopScheduledCharging) |
| rdpl | R/W | TYPE | Config | randomDelayWhenPluggingCar in seconds |
| rdple | R/W | TYPE | Config | randomDelayWhenPluggingCarEndsAt (set to null to abort current randomDelayWhenPluggingCar) |
| rdre | R/W | TYPE | Config | randomDelayReconnection in seconds |
| rdree | R/W | TYPE | Config | randomDelayReconnectionEndsAt (set to null to abort current randomDelayReconnection) |
| rfb | R | TYPE | Status | relay feedback |
| rmaf | R/W | TYPE | Config | reconnectionMaximumFrequency in Hz |
| rmav | R/W | TYPE | Config | reconnectionMaximumVoltage in Volt |
| rmif | R/W | TYPE | Config | reconnectionMinimumFrequency in Hz |
| rmiv | R/W | TYPE | Config | reconnectionMinimumVoltage in Volt |
| rsa | R/W | TYPE | Status | rampup started at |
| rsre | R/W | TYPE | Config | rampupAtStartAndReconnectionEnabled |
| rsrr | R/W | TYPE | Config | rampupAtStartAndReconnectionRate in %/s |
| rssi | R | TYPE | Status | RSSI signal strength |
| rst | W | TYPE | Unknown | Reset the charger and chargectrl |
| scaa | R | TYPE | Status | wifi scan age |
| scan | R | TYPE | Status | wifi scan result (encryptionType: OPEN=0, WEP=1, WPA_PSK=2, WPA2_PSK=3, WPA_WPA2_PSK=4, WPA2_ENTERPRISE=5, WPA3_PSK=6, WPA2_WPA3_PSK=7) |
| sch_satur | R/W | TYPE | Config | scheduler_saturday, control enum values: Disabled=0, Allow=1, Block=2, AllowFromGrid=3, BlockFromGrid=4 |
| sch_sund | R/W | TYPE | Config | scheduler_sunday, control enum values: Disabled=0, Allow=1, Block=2, AllowFromGrid=3, BlockFromGrid=4 |
| sch_week | R/W | TYPE | Config | scheduler_weekday, control enum values: Disabled=0, Allow=1, Block=2, AllowFromGrid=3, BlockFromGrid=4 |
| sdp | R/W | TYPE | Config | Button Allow Force change (0=AlwaysLock, 1=LockWhenCarIsConnected, 2=LockWhenCarIsCharging, 3=NeverLock) |
| sh | R/W | TYPE | Config | stopHysteresis in W |
| smd | R | TYPE | Status | smart meter data |
| spl3 | R/W | TYPE | Config | threePhaseSwitchLevel |
| sse | R | TYPE | Constant | serial number |
| su | R/W | TYPE | Config | simulateUnpluggingShort |
| sua | R/W | TYPE | Config | simulateUnpluggingAlways |
| sumd | R/W | TYPE | Config | simulate unpluging duration (in milliseconds) |
| t0h | R/W | TYPE | Config | led strip T0H |
| t0l | R/W | TYPE | Config | led strip T0L |
| t1h | R/W | TYPE | Config | led strip T1H |
| t1l | R/W | TYPE | Config | led strip T1L |
| tab | R | TYPE | Status | time at boot in utc in milliseconds, add rbt to get to current utc time |
| tcl | R/W | TYPE | Config | temporary current limit (does not change the user current limit, will be reset after 10min if not updated regulary) |
| tds | R/W | TYPE | Config | timezone daylight saving mode, None=0, EuropeanSummerTime=1, UsDaylightTime=2, AustralianDaylightTime=3 |
| tlf | R | TYPE | Status | testLadungFinished |
| tls | R | TYPE | Status | testLadungStarted |
| tma | R | TYPE | Status | temperature sensors |
| tof | R/W | TYPE | Config | timezone offset in minutes |
| tpa | R | TYPE | Status | 30 seconds total power average (not used by next-trip, use mmp for next-trip related power) |
| trx | R/W | TYPE | Status | transaction, null when no transaction, 0 when without card, otherwise cardIndex + 1 (1: 0. card, 2: 1. card, ...) |
| tse | R/W | TYPE | Config | time server enabled |
| tsi | R | TYPE | Status | transaction start rfidid (only available when sendRfid) |
| tsss | R | TYPE | Status | time server sync status (RESET=0, COMPLETED=1, IN_PROGRESS=2) |
| typ | R | TYPE | Constant | Devicetype |
| tzt | R/W | TYPE | Config | timezone type, freetext string for app selection |
| ufa | R/W | TYPE | Config | Underfrequency Control activation threshold |
| ufe | R/W | TYPE | Config | Underfrequency Control enabled |
| ufm | R/W | TYPE | Config | Underfrequency Control mode (TypeNominal=0, TypeActual=1) |
| ufs | R/W | TYPE | Config | Underfrequency Control stop frequency |
| upo | R/W | TYPE | Config | unlock_power_outage |
| ust | R/W | TYPE | Config | unlock_setting (Normal=0, AutoUnlock=1, AlwaysLock=2) |
| utc | R/W | TYPE | Status | utc time |
| var | R | TYPE | Constant | variant: max Ampere value of unit (11: 11kW/16A, 22: 22kW/32A) |
| wbw | R | TYPE | Config | WiFi Bandwidth (for both AP and STA) WIFI_BW_HT20=1, WIFI_BW_HT40=2 |
| wcb | R | TYPE | Status | WiFi current mac address (bssid connecting to) |
| wda | R/W | TYPE | Config | disable AccessPoint when cloud is connected |
| wfb | R | TYPE | Status | WiFi failed mac addresses (bssids) |
| wh | R | TYPE | Status | energy in Wh since car connected |
| wifis | R/W | TYPE | Config | wifi configurations with ssids and keys, if you only want to change the second entry, send an array with 1 empty and 1 filled wifi config object: [{}, {"ssid":"","key":""}] |
| wpb | R | TYPE | Status | WiFi planned mac addresses (future bssids) |
| wsc | R | TYPE | Status | WiFi STA error count |
| wsl | R | TYPE | Status | WiFi STA error messages log |
| wsm | R | TYPE | Status | WiFi STA error message |
| wsms | R | TYPE | Status | WiFi state machine state (None=0, Scanning=1, Connecting=2, Connected=3) |
| wst | R | TYPE | Status | WiFi STA status (IDLE_STATUS=0, NO_SSID_AVAIL=1, SCAN_COMPLETED=2, CONNECTED=3, CONNECT_FAILED=4, CONNECTION_LOST=5, DISCONNECTED=6, CONNECTING=7, DISCONNECTING=8, NO_SHIELD=9, WAITING_FOR_IP=10 (for compatibility with WiFi Shield library)) |
| zfo | R/W | TYPE | Config | zeroFeedinOffset in W |
