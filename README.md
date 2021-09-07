# go-eCharger-API-v2
New API specification for go-eCharger Home+ with WiFi connection

Die API keys lassen sich via http-request und mqtt lesen/schreiben.

## HTTP Api
Die API v2 muss in der App erst aktiviert werden:

<img src="screenshots/http-api-app-enable.png?raw=true" width="200" />

Danach können vereinzelte API keys abgefragt werden:

`http://192.168.0.75/api/status?filter=["rfb","alw","acu","adi","amp"]`

<img src="screenshots/http-api-status-filtered.png?raw=true" />

Oder gleich alle API keys auf einmal (höhere Last am System, viel traffic, sollte nicht für den Dauerbetrieb benutzt werden):

`http://192.168.0.75/api/status`

<img src="screenshots/http-api-status.png?raw=true" />

Mehrere API Werte setzen:

TODO

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
| amp        | R/W        | uint8                        | Config        | requestedCurrent in Ampere, used for display on LED ring and logic calculations     |
