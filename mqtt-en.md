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
| mcc     | MQTT connected (also used as Last Will / availability) | bool     | R    | Status   |
| mcca    | MQTT connected (timestamp in milliseconds since reboot) Subtract from reboot time (rbt) to get number of milliseconds since connected | null or milliseconds | R | Status |
| mlr     | MQTT last error               | string or null | R | Status |
| mlra    | MQTT last error (timestamp in milliseconds since reboot) Subtract from reboot time (rbt) to get number of milliseconds since error occured | null or milliseconds | R | Status |
| mck     | MQTT client key              | string   | R/W  | Config   |
| mqcc    | MQTT client cert             | string   | R/W  | Config   |
| msc     | MQTT server cert             | string   | R/W  | Config   |

## Topics

For each [API key](apikeys-en.md) the charger publishes a retained topic. The topic is built from a shared prefix, the serial number and the api key. Payloads are always JSON encoded. Strings for example are wrapped in quotation marks.

Examples:

```
go-eCharger/00000001/alw
go-eCharger/00000001/acu
go-eCharger/00000001/frc
```

If several go-e Chargers share the same MQTT broker, wildcard subscriptions make it easy to list the latest status of all chargers:

```
$ mosquitto_sub -v -t 'go-eCharger/#' | grep -P '/(?:alw|acu|fwv|rbt) '
go-eCharger/00000001/alw true
go-eCharger/00000001/acu 16
go-eCharger/00000001/rbt 498429772
go-eCharger/00000001/fwv "35.6-1-ga0d44e5"
go-eCharger/00000004/alw true
go-eCharger/00000004/acu 16
go-eCharger/00000004/rbt 498008264
go-eCharger/00000004/fwv "35.6-2-g99a02ad"
go-eCharger/00000004/rbt 498009263
go-eCharger/00000001/rbt 498430770
go-eCharger/00000004/rbt 498010263
go-eCharger/00000001/rbt 498431770
go-eCharger/00000004/rbt 498011263
go-eCharger/00000001/rbt 498432770
go-eCharger/00000004/rbt 498012264
^C
```

## Last Will (connection status)

Because api key topics are retained, subscribers would otherwise keep seeing the last values after the charger disappears from the broker — including `mcc` still being `true`.

On every MQTT CONNECT the charger registers a Last Will and Testament (LWT) on the existing `mcc` topic, so the connection status stays consistent with the rest of the API:

- **Topic:** `{prefix}{serial}/mcc` (same topic as the `mcc` api key, default `go-eCharger/{serial}/mcc`)
- **Payload:** `false` (JSON boolean, same encoding as other keys)
- **Retained:** yes
- **QoS:** 1

After a successful connection the charger publishes retained `true` on that topic, as it does for other status keys.

On an unexpected disconnect the broker publishes the last will, so `mcc` becomes `false`. On a clean disconnect (MQTT disabled, reboot, …) the charger publishes `false` itself before disconnecting, so clients see the same status either way.

Example:

```
$ mosquitto_sub -v -t 'go-eCharger/00000001/mcc'
go-eCharger/00000001/mcc true
# charger loses WiFi / power
go-eCharger/00000001/mcc false
```

Clients can treat `mcc` as the availability flag (for example Home Assistant `availability_topic` with `payload_available: true` and `payload_not_available: false`). If Home Assistant discovery is enabled (`mhe`), discovery payloads should use this topic as `availability_topic`.

## Setting values

**Attention:** Since firmware 051.5, writing values via MQTT has to be enabled explicitly (see screenshot above).

Append `/set` to the topic so other MQTT clients cannot confuse a write request with the actual value published by the charger. **Since firmware 051.5**, after the charger has received the command it sends a (non-retained) reply on the topic with `/result` appended.

Examples:

```
go-eCharger/00000001/frc/set
go-eCharger/00000001/frc/result
```

If the `/set` topic is set to 1, charging is stopped immediately. If it is set to 2, charging is allowed immediately. 0 restores the original logic with scheduler, Awattar, surplus charging and NextTrip.

More examples:

```
$ mosquitto_pub -t "go-eCharger/00000002/fna/set" -m "new_name"
$ mosquitto_pub -t "go-eCharger/00000002/fna/set" -m "0"
$ mosquitto_pub -t "go-eCharger/00000002/fna/set" -m "\"my charger\""
```

With the corresponding replies (since firmware 051.5):

```
$ mosquitto_sub -v -t "go-eCharger/00000002/#" | grep /fna
go-eCharger/00000002/fna "go-echarger_00000002"
go-eCharger/00000002/fna/set new_name
go-eCharger/00000002/fna/result invalid json IncompleteInput: new_name
go-eCharger/00000002/fna/set 0
go-eCharger/00000002/fna/result value must be string 0
go-eCharger/00000002/fna/set "my charger"
go-eCharger/00000002/fna/result success
go-eCharger/00000002/fna "my charger"
```

