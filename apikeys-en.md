[Deutsch](apikeys-de.md) &bull; English

# API Keys

| Key        | R/W        | Type                         | Category      | Description                                                                         |
| ---------- | ---------- | ---------------------------- | ------------- | ----------------------------------------------------------------------------------- |
rfb | R | TYPE | Status | relay feedback
rst | W | TYPE | Unknown | Reset the charger and chargectrl
alw | R | TYPE | Status | Is the car allowed to charge at all now?
acu | R | TYPE | Status | How many ampere is the car allowed to charge now?
cll | R | TYPE | Status | Current limits list
adi | R | TYPE | Status | Is the 16A adapter used? Limits the current to 16A
dwo | R/W | TYPE | Config | energy limit, measured in Wh, null means disabled, not the next trip energy
tpa | R | TYPE | Status | 30 seconds total power average (not used by next-trip, use mmp for next-trip related power)
sse | R | TYPE | Constant | serial number
eto | R | TYPE | Status | energy_total, measured in Wh
wifis | R/W | TYPE | Config | wifi configurations with ssids and keys, if you only want to change the second entry, send an array with 1 empty and 1 filled wifi config object: [{}, {"ssid":"","key":""}]
delw | W | TYPE | Unknown | set this to 0-9 to delete sta config (erases ssid, key, ...)
scan | R | TYPE | Status | wifi scan result (encryptionType: OPEN=0, WEP=1, WPA_PSK=2, WPA2_PSK=3, WPA_WPA2_PSK=4, WPA2_ENTERPRISE=5, WPA3_PSK=6, WPA2_WPA3_PSK=7)
lwf | R | TYPE | Status | last wifi connect failed (milliseconds since boot)
scaa | R | TYPE | Status | wifi scan age
wst | R | TYPE | Status | WiFi STA status (IDLE_STATUS=0, NO_SSID_AVAIL=1, SCAN_COMPLETED=2, CONNECTED=3, CONNECT_FAILED=4, CONNECTION_LOST=5, DISCONNECTED=6, CONNECTING=7, DISCONNECTING=8, NO_SHIELD=9, WAITING_FOR_IP=10 (for compatibility with WiFi Shield library))
wsc | R | TYPE | Status | WiFi STA error count
wsm | R | TYPE | Status | WiFi STA error message
wsl | R | TYPE | Status | WiFi STA error messages log
wsms | R | TYPE | Status | WiFi state machine state (None=0, Scanning=1, Connecting=2, Connected=3)
ccw | R | TYPE | Status | Currently connected WiFi
wfb | R | TYPE | Status | WiFi failed mac addresses (bssids)
wcb | R | TYPE | Status | WiFi current mac address (bssid connecting to)
wpb | R | TYPE | Status | WiFi planned mac addresses (future bssids)
nif | R | TYPE | Status | Default route
dns | R | TYPE | Status | dns servers
host | R | TYPE | Status | configured hostname
wbw | R | TYPE | Config | WiFi Bandwidth (for both AP and STA) WIFI_BW_HT20=1, WIFI_BW_HT40=2
rssi | R | TYPE | Status | RSSI signal strength
wda | R/W | TYPE | Config | disable AccessPoint when cloud is connected
tse | R/W | TYPE | Config | time server enabled
tsss | R | TYPE | Status | time server sync status (RESET=0, COMPLETED=1, IN_PROGRESS=2)
tof | R/W | TYPE | Config | timezone offset in minutes
tds | R/W | TYPE | Config | timezone daylight saving mode, None=0, EuropeanSummerTime=1, UsDaylightTime=2, AustralianDaylightTime=3
tzt | R/W | TYPE | Config | timezone type, freetext string for app selection
utc | R/W | TYPE | Status | utc time
loc | R | TYPE | Status | local time
tab | R | TYPE | Status | time at boot in utc in milliseconds, add rbt to get to current utc time
lto | R | TYPE | Status | local time offset in milliseconds, tab + rbt + lto = local time
led | R | TYPE | Status | LED animation
lbr | R/W | TYPE | Config | led_bright, 0-255
lmo | R/W | TYPE | Config | logic mode (Default=3, Awattar=4, NextTrip=5)
ama | R/W | TYPE | Config | ampere_max limit
tcl | R/W | TYPE | Config | temporary current limit (does not change the user current limit, will be reset after 10min if not updated regulary)
die | R/W | TYPE | Config | digital Input Enabled
dii | R/W | TYPE | Config | digital Input Inverted
la1 | R/W | TYPE | Config | limit adapter 1-phase (in A)
la3 | R/W | TYPE | Config | limit adapter 3-phase (in A)
di1 | R/W | TYPE | Config | digital Input 1-phase
pgr | R/W | TYPE | Config | protect Grid Requirements
pdi | R/W | TYPE | Config | protect Digital Input
ufe | R/W | TYPE | Config | Underfrequency Control enabled
ufm | R/W | TYPE | Config | Underfrequency Control mode (TypeNominal=0, TypeActual=1)
ufa | R/W | TYPE | Config | Underfrequency Control activation threshold
ufs | R/W | TYPE | Config | Underfrequency Control stop frequency
clp | R/W | TYPE | Config | current limit presets, max. 5 entries
bac | R/W | TYPE | Config | Button allow Current change (0=AlwaysLock, 1=LockWhenCarIsConnected, 2=LockWhenCarIsCharging, 3=NeverLock)
sdp | R/W | TYPE | Config | Button Allow Force change (0=AlwaysLock, 1=LockWhenCarIsConnected, 2=LockWhenCarIsCharging, 3=NeverLock)
bar | R/W | TYPE | Config | Button Allow WiFi AP reset (0=AlwaysLock, 1=LockWhenCarIsConnected, 2=LockWhenCarIsCharging, 3=NeverLock)
lbp | R | TYPE | Config | lastButtonPress
lbl | R | TYPE | Config | lastButtonHoldLong
amp | R/W | TYPE | Config | requestedCurrent, used for display on LED ring and logic calculations
fna | R/W | TYPE | Config | friendlyName
rdbs | R/W | TYPE | Config | randomDelayStartScheduledCharging in seconds
rdes | R/W | TYPE | Config | randomDelayStopScheduledCharging in seconds
rdbf | R/W | TYPE | Config | randomDelayStartFlexibleTariffCharging in seconds
rdef | R/W | TYPE | Config | randomDelayStopFlexibleTariffCharging in seconds
rdre | R/W | TYPE | Config | randomDelayReconnection in seconds
rdpl | R/W | TYPE | Config | randomDelayWhenPluggingCar in seconds
rdbse | R/W | TYPE | Config | randomDelayStartScheduledChargingEndsAt (set to null to abort current randomDelayStartScheduledCharging)
rdese | R/W | TYPE | Config | randomDelayStopScheduledChargingEndsAt (set to null to abort current randomDelayStopScheduledCharging)
rdbfe | R/W | TYPE | Config | randomDelayStartFlexibleTariffChargingEndsAt (set to null to abort current randomDelayStartFlexibleTariffCharging)
rdefe | R/W | TYPE | Config | randomDelayStopFlexibleTariffChargingEndsAt (set to null to abort current randomDelayStopFlexibleTariffCharging)
rdree | R/W | TYPE | Config | randomDelayReconnectionEndsAt (set to null to abort current randomDelayReconnection)
rdple | R/W | TYPE | Config | randomDelayWhenPluggingCarEndsAt (set to null to abort current randomDelayWhenPluggingCar)
gmtr | R/W | TYPE | Config | gridMonitoringTimeReconnection in seconds
gsa | R/W | TYPE | Status | gridMonitoring last failure
rsa | R/W | TYPE | Status | rampup started at
rmiv | R/W | TYPE | Config | reconnectionMinimumVoltage in Volt
rmav | R/W | TYPE | Config | reconnectionMaximumVoltage in Volt
rmif | R/W | TYPE | Config | reconnectionMinimumFrequency in Hz
rmaf | R/W | TYPE | Config | reconnectionMaximumFrequency in Hz
rsre | R/W | TYPE | Config | rampupAtStartAndReconnectionEnabled
rsrr | R/W | TYPE | Config | rampupAtStartAndReconnectionRate in %/s
cid | R/W | TYPE | Config | color_idle, format: #RRGGBB
cwc | R/W | TYPE | Config | color_waitcar, format: #RRGGBB
cch | R/W | TYPE | Config | color_charging, format: #RRGGBB
cfi | R/W | TYPE | Config | color_finished, format: #RRGGBB
ust | R/W | TYPE | Config | unlock_setting (Normal=0, AutoUnlock=1, AlwaysLock=2)
lck | R | TYPE | Status | Effective lock setting, as sent to Charge Ctrl (Normal=0, AutoUnlock=1, AlwaysLock=2, ForceUnlock=3)
sch_week | R/W | TYPE | Config | scheduler_weekday, control enum values: Disabled=0, Allow=1, Block=2, AllowFromGrid=3, BlockFromGrid=4
sch_satur | R/W | TYPE | Config | scheduler_saturday, control enum values: Disabled=0, Allow=1, Block=2, AllowFromGrid=3, BlockFromGrid=4
sch_sund | R/W | TYPE | Config | scheduler_sunday, control enum values: Disabled=0, Allow=1, Block=2, AllowFromGrid=3, BlockFromGrid=4
nmo | R/W | TYPE | Config | norway_mode / ground check enabled when norway mode is disabled
fsp | R/W | TYPE | Status | force_single_phase
lrn | W | TYPE | Config | set this to 0-9 to learn last read card id
del | W | TYPE | Unknown | set this to 0-9 to clear card (erases card name, energy and rfid id)
acs | R/W | TYPE | Config | access_control user setting (Open=0, Wait=1, EVCMS=2)
frc | R/W | TYPE | Config | forceState (Neutral=0, Off=1, On=2)
rbc | R | TYPE | Status | reboot_counter
rbt | R | TYPE | Status | time since boot in milliseconds
car | R | TYPE | Status | charge ctrl car state, null if no connection to chargectrl established (Unknown/Error=0, Idle=1, Charging=2, WaitCar=3, Complete=4, Error=5)
err | R | TYPE | Status | charge ctrl error, null if no connection to charge ctrl established (None=0, FiAc=1, FiDc=2, Phase=3, Overvolt=4, Overamp=5, Diode=6, PpInvalid=7, GndInvalid=8, ContactorStuck=9, ContactorMiss=10, StatusLockStuckOpen=12, StatusLockStuckLocked=13, FiUnknown=14, Unknown=15, Overtemp=16, NoComm=17, CpInvalid=18)
cbl | R | TYPE | Status | cable_current_limit in A
pha | R | TYPE | Status | phases
wh | R | TYPE | Status | energy in Wh since car connected
trx | R/W | TYPE | Status | transaction, null when no transaction, 0 when without card, otherwise cardIndex + 1 (1: 0. card, 2: 1. card, ...)
fwv | R | TYPE | Status | FW_VERSION
oem | R | TYPE | Constant | OEM manufacturer
typ | R | TYPE | Constant | Devicetype
lse | R/W | TYPE | Config | led_save_energy
t0h | R/W | TYPE | Config | led strip T0H
t1h | R/W | TYPE | Config | led strip T1H
t0l | R/W | TYPE | Config | led strip T0L
t1l | R/W | TYPE | Config | led strip T1L
cdi | R | TYPE | Status | charging duration info (null=no charging in progress, type=0 counter going up, type=1 duration in ms)
lccfi | R | TYPE | Status | lastCarStateChangedFromIdle (in ms)
lccfc | R | TYPE | Status | lastCarStateChangedFromCharging (in ms)
lcctc | R | TYPE | Status | lastCarStateChangedToCharging (in ms)
tma | R | TYPE | Status | temperature sensors
amt | R | TYPE | Status | temperatureCurrentLimit
nrg | R | TYPE | Status | energy array, U (L1, L2, L3, N), I (L1, L2, L3), P (L1, L2, L3, N, Total), pf (L1, L2, L3, N)
modelStatus | R | TYPE | Status | Reason why we allow charging or not right now (NotChargingBecauseNoChargeCtrlData=0, NotChargingBecauseOvertemperature=1, NotChargingBecauseAccessControl=2, ChargingBecauseForceStateOn=3, NotChargingBecauseForceStateOff=4, NotChargingBecauseScheduler=5, NotChargingBecauseEnergyLimit=6, ChargingBecauseAwattarPriceLow=7, ChargingBecauseAutomaticStopTestLadung=8, ChargingBecauseAutomaticStopNotEnoughTime=9, ChargingBecauseAutomaticStop=10, ChargingBecauseAutomaticStopNoClock=11, ChargingBecausePvSurplus=12, ChargingBecauseFallbackV2Default=13, ChargingBecauseFallbackV2Scheduler=14, ChargingBecauseFallbackDefault=15, NotChargingBecauseFallbackV2Awattar=16, NotChargingBecauseFallbackAwattar=17, NotChargingBecauseFallbackAutomaticStop=18, ChargingBecauseCarCompatibilityKeepAlive=19, ChargingBecauseChargePauseNotAllowed=20, NotChargingBecauseSimulateUnplugging=22, NotChargingBecausePhaseSwitch=23, NotChargingBecauseMinPauseDuration=24, NotChargingBecauseError=26, NotChargingBecauseLoadManagementDoesntWant=27, NotChargingBecauseOcppDoesntWant=28, NotChargingBecauseReconnectDelay=29, NotChargingBecauseAdapterBlocking=30, NotChargingBecauseUnderfrequencyControl=31, NotChargingBecauseUnbalancedLoad=32, ChargingBecauseDischargingPvBattery=33, NotChargingBecauseGridMonitoring=34, NotChargingBecauseOcppFallback=35)
lmsc | R | TYPE | Status | last model status change
mca | R/W | TYPE | Config | minChargingCurrent
awc | R/W | TYPE | Config | awattar country (Austria=0, Germany=1,...)
awp | R/W | TYPE | Config | awattarMaxPrice in ct
awcp | R | TYPE | Status | awattar current price
awpl | W | TYPE | Status | awattar price list, timestamps are measured in unix-time, seconds since 1970
frm | R/W | TYPE | Config | roundingMode PreferPowerFromGrid=0, Default=1, PreferPowerToGrid=2
fup | R/W | TYPE | Config | usePvSurplus
awe | R/W | TYPE | Config | useAwattar
fst | R/W | TYPE | Config | startingPower in watts
fmt | R/W | TYPE | Config | minChargeTime in milliseconds
att | R/W | TYPE | Config | automatic stop time in seconds since day begin, calculation: (hours*3600)+(minutes*60)+(seconds)
ate | R/W | TYPE | Config | nextTripEnergy in Wh
ara | R/W | TYPE | Config | automatic stop remain in aWATTar
acp | R/W | TYPE | Config | allowChargePause
cco | R/W | TYPE | Config | car consumption (for app)
esk | R/W | TYPE | Config | energy set kwh (for app)
fzf | R/W | TYPE | Config | zeroFeedin
pgt | R/W | TYPE | Config | pGridTarget in W
sh | R/W | TYPE | Config | stopHysteresis in W
psh | R/W | TYPE | Config | phaseSwitchHysteresis in W
po | R/W | TYPE | Config | prioOffset in W
zfo | R/W | TYPE | Config | zeroFeedinOffset in W
psmd | R/W | TYPE | Config | forceSinglePhaseDuration (in milliseconds)
sumd | R/W | TYPE | Config | simulate unpluging duration (in milliseconds)
mpwst | R/W | TYPE | Config | min phase wish switch time (in milliseconds)
mptwt | R/W | TYPE | Config | min phase toggle wait time (in milliseconds)
mmp | R | TYPE | Status | maximumMeasuredChargingPower
tlf | R | TYPE | Status | testLadungFinished
tls | R | TYPE | Status | testLadungStarted
atp | R | TYPE | Status | nextTripPlanData
lpsc | R | TYPE | Status | last pv surplus calcuation
ids | W | TYPE | Status | inverter data setter {"pGrid": 1000., "pPv": 1000., "pAkku": 1000.}
inva | R | TYPE | Status | age of inverter data
pgrid | R | TYPE | Status | pGrid in W
ppv | R | TYPE | Status | pPv in W
pakku | R | TYPE | Status | pAkku in W
dsrc | R | TYPE | Status | inverter data source
deltap | R | TYPE | Status | deltaP
pnp | R | TYPE | Status | numberOfPhases
deltaa | R | TYPE | Unknown | deltaA
pvopt_averagePGrid | R | TYPE | Status | averagePGrid
pvopt_averagePPv | R | TYPE | Status | averagePPv
pvopt_averagePAkku | R | TYPE | Status | averagePAkku
ct | R/W | TYPE | Config | car type, free text string (max. 64 characters)
mci | R/W | TYPE | Config | minimumChargingInterval in milliseconds (0 means disabled)
mcpd | R/W | TYPE | Config | minChargePauseDuration in milliseconds (0 means disabled)
mcpea | R/W | TYPE | Config | minChargePauseEndsAt (set to null to abort current minChargePauseDuration)
su | R/W | TYPE | Config | simulateUnpluggingShort
sua | R/W | TYPE | Config | simulateUnpluggingAlways
hsa | W | TYPE | Config | httpStaAuthentication
var | R | TYPE | Constant | variant: max Ampere value of unit (11: 11kW/16A, 22: 22kW/32A)
loe | R/W | TYPE | Config | Load balancing enabled
log | R/W | TYPE | Config | load_group_id
lop | R/W | TYPE | Config | load_priority
lopr | R/W | TYPE | Config | load balancing protected
lof | R/W | TYPE | Config | load_fallback
map | R/W | TYPE | Config | load_mapping (uint8_t[3])
upo | R/W | TYPE | Config | unlock_power_outage
pwm | R | TYPE | Status | phase wish mode for debugging / only for pv optimizing / used for timers later (Force_3=0, Wish_1=1, Wish_3=2)
lfspt | R | TYPE | Status | last force single phase toggle
fsptws | R | TYPE | Status | force single phase toggle wished since
spl3 | R/W | TYPE | Config | threePhaseSwitchLevel
oct | W | TYPE | Config | ota from cloud url trigger
ocu | R | TYPE | Config | ota from cloud url, url to download new firmware code from
cwe | R/W | TYPE | Config | cloud websocket enabled
clea | R | TYPE | Status | Cloud last error (age)
cle | R | TYPE | Status | Cloud last error
cus | R | TYPE | Status | Cable unlock status (Unknown=0, Unlocked=1, UnlockFailed=2, Locked=3, LockFailed=4, LockUnlockPowerout=5)
ffb | R | TYPE | Status | lock feedback (NoProblem=0, ProblemLock=1, ProblemUnlock=2)
fhz | R | TYPE | Status | Stromnetz frequency (~50Hz) or 0 if unknown
avgfhz | R | TYPE | Status | Stromnetz average frequency (~50Hz)
loa | R | TYPE | Status | load balancing ampere
lot | R/W | TYPE | Config | load balancing total amp
loty | R/W | TYPE | Config | load balancing type (Static=false, Dynamic=true)
cards | R/W | TYPE | Config | RFID cards array of objects, if you only want to change the second entry, send an array with 1 empty and 1 filled card config object: [{}, {"name":"","energy":"","rfid":""}]
smd | R | TYPE | Status | smart meter data
men | R/W | TYPE | Config | modbus slave enabled
msp | R/W | TYPE | Config | modbus slave port (requires off/on toggle)
msb | R/W | TYPE | Config | modbus slave swap bytes
msr | R/W | TYPE | Config | modbus slave swap registers
data | R | TYPE | Status | grafana token from cloud for app
dll | R | TYPE | Status | download link for app csv export
hai | R/W | TYPE | Config | httpApiEnabled (allows /api/status and /api/set requests)
hla | R/W | TYPE | Config | httpLegacyApiEnabled (allows /status and /mqtt requests)
mce | R/W | TYPE | Config | MQTT enabled
mcu | R/W | TYPE | Config | MQTT broker url
mcr | R/W | TYPE | Config | MQTT readonly (don't allow api writes from mqtt broker)
mtp | R/W | TYPE | Config | MQTT topic prefix (set to null to reset back to the default)
mht | R/W | TYPE | Config | MQTT homeassistant topic prefix (set to null to reset back to the default)
mhe | R/W | TYPE | Config | MQTT enable homeassistant discovery
mqg | R/W | TYPE | Config | MQTT useGlobalCaStore
mqcn | R/W | TYPE | Config | MQTT skipCertCommonNameCheck
mqss | R/W | TYPE | Config | MQTT skipServerVerification
mcs | R | TYPE | Status | MQTT started
mcc | R | TYPE | Status | MQTT connected
mcca | R | TYPE | Status | MQTT connected (age)
mlr | R | TYPE | Status | MQTT last error
mlra | R | TYPE | Status | MQTT last error (age)
ocppe | R/W | TYPE | Config | OCPP enabled
ocppu | R/W | TYPE | Config | OCPP server url
ocppf | R/W | TYPE | Config | OCPP fallback current
ocppg | R/W | TYPE | Config | OCPP useGlobalCaStore
ocppcn | R/W | TYPE | Config | OCPP skipCertCommonNameCheck
ocppss | R/W | TYPE | Config | OCPP skipServerVerification
ocpps | R | TYPE | Status | OCPP started
ocppc | R | TYPE | Status | OCPP connected
ocppca | R | TYPE | Status | OCPP connected (age)
ocppa | R | TYPE | Status | OCPP connected and accepted
ocppaa | R | TYPE | Status | OCPP connected and accepted (age)
ocppti | R/W | TYPE | Status | OCPP transaction id
ocppao | R/W | TYPE | Status | OCPP AllowOfflineTxForUnknownId
ocpplo | R/W | TYPE | Status | OCPP LocalAuthorizeOffline
ocppla | R/W | TYPE | Status | OCPP LocalAuthListEnabled
ocpph | R/W | TYPE | Config | ocppHeartbeatInterval
ocppi | R/W | TYPE | Config | ocppMeterValueSampleInterval
ocppai | R/W | TYPE | Config | ocppClockAlignedDataInterval
ocppd | R/W | TYPE | Config | OCPP dummy card id (used when no card has been used and charging is already allowed / starting)
ocppr | R/W | TYPE | Config | OCPP rotate phases on charger
ocppcm | R/W | TYPE | Status | OCPP LocalAuthListEnabled
ocpplea | R | TYPE | Status | OCPP last error (age)
ocpple | R | TYPE | Status | OCPP last error
ocpprl | R/W | TYPE | Config | OCPP remote log
ocppcs | R | TYPE | Status | OCPP connector status (0=Available, 1=Preparing, 2=Charging, 3=SuspendedEVSE, 4=SuspendedEV, 5=Finishing, 6=Reserved, 7=Unavailable, 8=Faulted)
rde | R/W | TYPE | Config | send rfid serial to cloud/api/mqtt (enable lri api key to show rfid numbers)
lri | R | TYPE | Status | last rfid id (only available when sendRfid)
tsi | R | TYPE | Status | transaction start rfidid (only available when sendRfid)
lrc | R | TYPE | Status | last rfid card index
lrr | R | TYPE | Status | last rfid read (milliseconds since boot)
cmse | R | TYPE | Config | controllerMdnsScanEnabled, set to false to completely disable any MDNS searches (debugging)
cmmr | R | TYPE | Config | controllerMdnsMaxResults
cms | R | TYPE | Config | controllerMdnsService
cmp | R | TYPE | Config | controllerMdnsProto
pco | R | TYPE | Config | controllerCloudKey
lcs | R | TYPE | Status | last controller scan timestamp in milliseconds since boot time
csa | R | TYPE | Status | controller scan active
ctrls | R | TYPE | Status | Controllers search result
ccd | R | TYPE | Status | Connected controller data