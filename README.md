# go-eCharger-API-v2
New API specification for go-eCharger Home+ with WiFi connection

Die API keys lassen sich via http-request und mqtt lesen/schreiben.

## HTTP Api

TODO erklärung wie http api einzuschalten und zu bedienen.

## MQTT

TODO erklärung wie mqtt einzuschalten und zu bedienen.

# API Keys

| Key           | R/W           | Type             | Category      | Description                                                                 |
| ------------- | ------------- | ---------------- | ------------- | --------------------------------------------------------------------------- |
| mod           | R             | uint8            | Constant      | Module hardware pcb version (0, 1, ...)                                     |
| rfb           | R             | int              | Status        | relay feedback                                                              |
| alw           | R             | bool             | Status        | Is the car allowed to charge at all now?                                    |
| acu           | R             | int              | Status        | How many ampere is the car allowed to charge now?                           |
| adi           | R             | bool             | Status        | Is the 16A adapter used? Limits the current to 16A                          |
| dwo           | R/W           | optional<double> | Config        | energy limit, measured in Wh, null means disabled, not the next trip energy |
| tpa           | R             | float            | Status        | 30 seconds total power average used to get better next-trip predictions     |
| sse           | R             | string           | Constant      | serial number                                                               |
