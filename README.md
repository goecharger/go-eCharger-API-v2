# go-eCharger-API-v2
New API specification for go-eCharger Home+ with WiFi connection

Die API keys lassen sich via http-request und mqtt lesen/schreiben.

## HTTP Api

TODO erklärung wie http api einzuschalten und zu bedienen.

## MQTT

TODO erklärung wie mqtt einzuschalten und zu bedienen.

# API Keys

| Key           | R/W           | Type                         | Category      | Description                                                                         |
| ------------- | ------------- | ---------------------------- | ------------- | ----------------------------------------------------------------------------------- |
| mod           | R             | uint8                        | Constant      | Module hardware pcb version (0, 1, ...)                                             |
| rfb           | R             | int                          | Status        | relay feedback                                                                      |
| alw           | R             | bool                         | Status        | Is the car allowed to charge at all now?                                            |
| acu           | R             | int                          | Status        | How many ampere is the car allowed to charge now?                                   |
| adi           | R             | bool                         | Status        | Is the 16A adapter used? Limits the current to 16A                                  |
| dwo           | R/W           | optional&lt;double&gt;       | Config        | energy limit, measured in Wh, null means disabled, not the next trip energy         |
| tpa           | R             | float                        | Status        | 30 seconds total power average used to get better next-trip predictions             |
| sse           | R             | string                       | Constant      | serial number                                                                       |
| eto           | R             | uint64                       | Status        | energy_total, measured in Wh                                                        |
| etop          | R             | uint64                       | Status        | energy_total persisted, measured in Wh, without the extra magic to have live values |
| wifis         | R/W           | array                        | Config        | wifi configurations with ssids and keys, if you only want to change the second entry, send an array with 1 empty and 1 filled wifi config object: `[{}, {"ssid":"","key":""}]` |
| delw          | W             | uint8                        | Other         | set this to 0-9 to delete sta config (erases ssid, key, ...)                        |
| scas          | R             | uint8                        | Status        | wifi scan status (None=0, Scanning=1, Finished=2, Failed=3)                         |
| scan          | R             | array                        | Status        | wifi scan result (encryptionType: OPEN=0, WEP=1, WPA_PSK=2, WPA2_PSK=3, WPA_WPA2_PSK=4, WPA2_ENTERPRISE=5, WPA3_PSK=6, WPA2_WPA3_PSK=7) |
| scaa          | R             | milliseconds                 | Status        | wifi scan age                                                                       |
| wst           | R             | uint8                        | Status        | WiFi STA status (IDLE_STATUS=0, NO_SSID_AVAIL=1, SCAN_COMPLETED=2, CONNECTED=3, CONNECT_FAILED=4, CONNECTION_LOST=5, DISCONNECTED=6, CONNECTING=8, DISCONNECTING=9, NO_SHIELD=10 (for compatibility with WiFi Shield library)) |
| wsms          | R             | uint8                        | Status        | WiFi state machine state (None=0, Scanning=1, Connecting=2, Connected=3)            |
| ccw           | R             | optional&lt;object&gt;       | Status        | Currently connected WiFi                                                            |
| host          | R             | optional&lt;string&gt;       | Status        | hostname used on STA interface                                                      |
| lwcf          | R             | bool                         | Status        | last wifi connect failed                                                            |
| rssi          | R             | optional&lt;int8&gt;         | Status        | RSSI signal strength                                                                |
| lssfc         | R             | optional&lt;milliseconds&gt; | Status        | lastStaSwitchedFromConnected (in milliseconds)                                      |
| lsstc         | R             | optional&lt;milliseconds&gt; | Status        | lastStaSwitchedToConnected (in milliseconds)                                      |
