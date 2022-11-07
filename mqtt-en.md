[Deutsch](mqtt-de.md) &bull; English

# MQTT

[The api keys](apikeys-en.md) can be read and written via MQTT. Since firmware 051.5 changing values via MQTT has to be enabled explicitly as it is not allowed by default anymore. MQTT can be enabled using the App or the [http API](http-en.md).

A mqtt topic prefix was implemented recently to change the topics that the chargers will emit and listen on.

## Using the App to enable and verify the MQTT connection

Tap the tab "Internet" at the bottom, then click on "Advanced Settings" in the menu, then at the very bottom "MQTT"

<img src="screenshots/mqtt-app-enable.png?raw=true" width="200" />

**Warning:** Use the preconfigured test broker url only for short test sessions, as this opens an attack surface for strangers from the internet, who can also then delete wifi configs or restart the charger.

## Using the http API to enable and verify the MQTT connection

The chargers provide api keys to configure and verify the mqtt connection. These api keys can be used with the http api.

Example: http://192.168.0.77/api/set?mce=true&mcu=mqtt://mqtt.server:1234/

| api key | description                  | datatype | R?W? | Category |
| ------- | ---------------------------- | -------- | ---- | -------- |
| mce     | MQTT enabled                 | bool     | R/W  | Config   |
| mcu     | MQTT broker url              | string   | R/W  | Config   |
| mcr     | MQTT readonly (don't allow api writes from mqtt broker) | bool   | R/W  | Config   |
| mtp     | MQTT topic prefix (set to null to reset back to the default) | optional&lt;string&gt; | R/W  | Config   |
| mqg     | MQTT use global CA Store     | bool     | R/W  | Config   |
| mqcn    | MQTT skipCertCommonNameCheck | bool     | R/W  | Config   |
| mqss    | MQTT skipServerVerification  | bool     | R/W  | Config   |
| mcs     | MQTT started                 | bool     | R    | Status   |
| mcc     | MQTT connected               | bool     | R    | Status   |
| mcca    | MQTT connected (timestamp in milliseconds since reboot) Subtract from reboot time (rbt) to get number of milliseconds since connected | null or milliseconds | R | Status |
| mlr     | MQTT last error               | string or null | R | Status |
| mlra    | MQTT last error (timestamp in milliseconds since reboot) Subtract from reboot time (rbt) to get number of milliseconds since error occured | null or milliseconds | R | Status |
| mck     | MQTT client key              | string   | R/W  | Config   |
| mqcc    | MQTT client cert             | string   | R/W  | Config   |
| msc     | MQTT server cert             | string   | R/W  | Config   |

## Topics

TODO for go-e: Document the topics for reading/writing.
