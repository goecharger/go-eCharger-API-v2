# go-eCharger-API-v2
New API specification for go-eCharger Home+ with WiFi connection

Die API keys lassen sich via http-request und mqtt lesen/schreiben.

## HTTP Api

Die API v2 muss in der App erst aktiviert werden:

<img src="screenshots/http-api-app-enable.png?raw=true" width="200" />

### Alle Werte auf einmal abfragen
<small>höhere Last am System, viel traffic, sollte nicht für den Dauerbetrieb benutzt werden</small>

`http://192.168.0.75/api/status`

<img src="screenshots/http-api-status.png?raw=true" />

### Vereinzelte Werte abfragen​
Ab 051.4:

`http://192.168.0.75/api/status?filter=rfb,alw,acu,adi,amp`

Bis 051.3 (legacy):
<small>Achtung, beim JSON parsen ging häufig der Speicher aus und es waren nie mehr als ca. 10 parameter möglich</small>

`http://192.168.0.75/api/status?filter=["rfb","alw","acu","adi","amp"]`

<img src="screenshots/http-api-status-filtered.png?raw=true" />

### Werte setzen

```
http://192.168.0.75/api/set?fna="mein charger"
http://192.168.0.75/api/set?amp=16
http://192.168.0.75/api/set?dwo=null
http://192.168.0.75/api/set?dwo=3.14
http://192.168.0.75/api/set?bac=false&sdp=true
```

TODO genauere beschreibung

## MQTT

TODO erklärung wie mqtt einzuschalten und zu bedienen.

# API Keys

| Key        | R/W        | Type                         | Category      | Description                                                                         |
| ---------- | ---------- | ---------------------------- | ------------- | ----------------------------------------------------------------------------------- |
| mod        | R          | uint8                        | Constant      | Module hardware pcb version (0, 1, ...)                                             |
| rfb        | R          | int                          | Status        | relay feedback                                                                      |
| alw        | R          | bool                         | Status        | Is the car allowed to charge at all now?                                            |
| acu        | R          | int                          | Status        | How many ampere is the car allowed to charge now?                                   |
| adi        | R          | bool                         | Status        | Is the 16A adapter used? Limits the current to 16A                                  |
| dwo        | R/W        | optional&lt;double&gt;       | Config        | energy limit, measured in Wh, null means disabled, not the next trip energy         |
| tpa        | R          | float                        | Status        | 30 seconds total power average used to get better next-trip predictions             |
| sse        | R          | string                       | Constant      | serial number                                                                       |
| eto        | R          | uint64                       | Status        | energy_total, measured in Wh                                                        |
| etop       | R          | uint64                       | Status        | energy_total persisted, measured in Wh, without the extra magic to have live values |
| wifis      | R/W        | array                        | Config        | wifi configurations with ssids and keys, if you only want to change the second entry, send an array with 1 empty and 1 filled wifi config object: `[{}, {"ssid":"","key":""}]` |
| delw       | W          | uint8                        | Other         | set this to 0-9 to delete sta config (erases ssid, key, ...)                        |
| scas       | R          | uint8                        | Status        | wifi scan status (None=0, Scanning=1, Finished=2, Failed=3)                         |
| scan       | R          | array                        | Status        | wifi scan result (encryptionType: OPEN=0, WEP=1, WPA_PSK=2, WPA2_PSK=3, WPA_WPA2_PSK=4, WPA2_ENTERPRISE=5, WPA3_PSK=6, WPA2_WPA3_PSK=7) |
| scaa       | R          | milliseconds                 | Status        | wifi scan age                                                                       |
| wst        | R          | uint8                        | Status        | WiFi STA status (IDLE_STATUS=0, NO_SSID_AVAIL=1, SCAN_COMPLETED=2, CONNECTED=3, CONNECT_FAILED=4, CONNECTION_LOST=5, DISCONNECTED=6, CONNECTING=8, DISCONNECTING=9, NO_SHIELD=10 (for compatibility with WiFi Shield library)) |
| wsms       | R          | uint8                        | Status        | WiFi state machine state (None=0, Scanning=1, Connecting=2, Connected=3)            |
| ccw        | R          | optional&lt;object&gt;       | Status        | Currently connected WiFi                                                            |
| host       | R          | optional&lt;string&gt;       | Status        | hostname used on STA interface                                                      |
| lwcf       | R          | bool                         | Status        | last wifi connect failed                                                            |
| rssi       | R          | optional&lt;int8&gt;         | Status        | RSSI signal strength                                                                |
| lssfc      | R          | optional&lt;milliseconds&gt; | Status        | lastStaSwitchedFromConnected (in milliseconds)                                      |
| lsstc      | R          | optional&lt;milliseconds&gt; | Status        | lastStaSwitchedToConnected (in milliseconds)                                        |
| ehs        | R          | size_t                       | Status        | ESP heap size                                                                       |
| efh        | R          | size_t                       | Status        | ESP free heap                                                                       |
| efh32      | R          | size_t                       | Status        | ESP free heap 32bit aligned                                                         |
| efh8       | R          | size_t                       | Status        | ESP free heap 8bit aligned                                                          |
| fem        | R          | uint8                        | Constant      | Flash Encryption Mode (Disabled=0, Development=1, Release=2)                        |
| sbe        | R          | bool                         | Constant      | Secure boot enabled                                                                 |
| emfh       | R          | size_t                       | Status        | ESP minimum free heap since boot                                                    |
| emhb       | R          | size_t                       | Status        | ESP max size of allocated heap block since boot                                     |
| eci        | R          | object                       | Constant      | ESP chip info (model: ESP32=1, ESP32S2=2, ESP32S3=4, ESP32C3=5; features: EMB_FLASH=bit0, WIFI_BGN=bit1, BLE=bit4, BT=bit5) |
| ecf        | R          | object                       | Constant      | ESP CPU freq (source: XTAL=0, PLL=1, 8M=2, APLL=3)                                  |
| efi        | R          | object                       | Constant      | ESP Flash info (spi_mode: QIO=0, QOUT=1, DIO=2, DOUT=3, FAST_READ=4, SLOW_READ=5; spi_speed: 40M=0, 26M=1, 20M=2, 80M=15; spi_size: 1MB=0, 2MB=1, 4MB=2, 8MB=3, 16MB=4, MAX=5) |
| eem        | R          | optional&lt;string&gt;       | Constant      | ESP CPU freq (source: XTAL=0, PLL=1, 8M=2, APLL=3)                                  |
| esr        | R          | array                        | Status        | rtc_get_reset_reason for core 0 and 1 (NO_MEAN=0, POWERON_RESET=1, SW_RESET=3, OWDT_RESET=4, DEEPSLEEP_RESET=5, SDIO_RESET=6, TG0WDT_SYS_RESET=7, TG1WDT_SYS_RESET=8, RTCWDT_SYS_RESET=9, INTRUSION_RESET=10, TGWDT_CPU_RESET=11, SW_CPU_RESET=12, RTCWDT_CPU_RESET=13, EXT_CPU_RESET=14, RTCWDT_BROWN_OUT_RESET=15, RTCWDT_RTC_RESET=16) |
| rr         | R          | uint8                        | Status        | esp_reset_reason (UNKNOWN=0, POWERON=1, EXT=2, SW=3, PANIC=4, INT_WDT=5, TASK_WDT=6, WDT=7, DEEPSLEEP=8, BROWNOUT=9, SDIO=10) |
| fwan       | R          | string                       | Constant      | factoryWifiApName                                                                   |
| wan        | R/W        | string                       | Config        | wifiApName                                                                          |
| facwak     | R          | string                       | Constant      | WiFi AccessPoint Key RESET VALUE (factory)                                          |
| wak        | R/W        | string                       | Config        | WiFi AccessPoint Key (read/write from http)                                         |
| wen        | R/W        | bool                         | Config        | wifiEnabled (bool), turns off/on the WiFi (not the AccessPoint)                     |
| pass       | W          | string                       | Config        | userPassword                                                                        |
| tse        | R/W        | bool                         | Config        | time server enabled (NTP)                                                           |
| ts         | R          | string                       | Config        | time server                                                                         |
| tssm       | R          | uint8                        | Config        | time server sync mode (IMMED=0, SMOOTH=1)                                           |
| tssi       | R          | milliseconds                 | Config        | time server sync interval (in ms, 15s minimum)                                      |
| tsss       | R          | uint8                        | Config        | time server sync status (RESET=0, COMPLETED=1, IN_PROGRESS=2)                       |
| tsom       | R          | uint8                        | Status        | time server operating mode (POLL=0, LISTENONLY=1)                                   |
| tof        | R/W        | minutes                      | Config        | timezone offset in minutes                                                          |
| tds        | R/W        | uint8                        | Config        | timezone daylight saving mode, None=0, EuropeanSummerTime=1, UsDaylightTime=2       |
| utc        | R/W        | string                       | Status        | utc time                                                                            |
| loc        | R          | string                       | Status        | local time                                                                          |
| led        | R          | object                       | Status        | internal infos about currently running led animation                                |
| lbr        | R          | uint8                        | Config        | led_bright, 0-255                                                                   |
| lmo        | R/W        | uint8                        | Config        | logic mode (Default=3, Awattar=4, AutomaticStop=5)                                  |
| ama        | R/W        | uint8                        | Config        | ampere_max limit                                                                    |
| clp        | R/W        | array                        | Config        | current limit presets, max. 5 entries                                               |
| bac        | R/W        | bool                         | Config        | Button allow Current change                                                         |
| sdp        | R/W        | bool                         | Config        | Button Allow Force change                                                           |
| lbp        | R          | milliseconds                 | Status        | lastButtonPress in milliseconds                                                     |
| amp        | R/W        | uint8                        | Config        | requestedCurrent in Ampere, used for display on LED ring and logic calculations     |
| ffna       | R          | string                       | Constant      | factoryFriendlyName                                                                 |
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
| fsp        | R          | bool                         | Status        | force_single_phase (shows if currently single phase charge is enforced              |
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
| trx        | R          | optional&lt;uint8&gt;        | Status        | transaction, null when no transaction, 0 when without card, otherwise cardIndex + 1 (1: 0. card, 2: 1. card, ...) |
| fwv        | R          | string                       | Constant      | FW_VERSION                                                                          |
| arv        | R          | string                       | Constant      | app recommended version (used to show in the app that the app is outdated)          |
| ccu        | R          | optional&lt;object&gt;       | Status        | charge controller update progress (null if no update is in progress)                |
| oem        | R          | string                       | Constant      | OEM manufacturer                                                                    |
| typ        | R          | string                       | Constant      | Devicetype                                                                          |
| fwc        | R          | string                       | Constant      | firmware from CarControl                                                            |
| apd        | R          | object                       | Constant      | firmware description                                                                |
| otap       | R          | optional&lt;object&gt;       | Constant      | currently used OTA partition                                                        |
| part       | R          | array                        | Constant      | partition table                                                                     |
| pto        | R          | uint32                       | Constant      | partition table offset in flash                                                     |
| lse        | R/W        | bool                         | Config        | led_save_energy                                                                     |
| cdi        | R          | object                       | Status        | charging duration info (null=no charging in progress, type=0 counter going up, type=1 duration in ms) |
