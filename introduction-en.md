# go-eCharger-API-v2
New API specification for go-eCharger Home+ with WiFi connection

Basics: There is a [set of api keys](apikeys-en.md), which can be read/written over [the HTTP Api](http-en.md) and [MQTT](mqtt-en.md).

The Charging-logic will be executed once everey second. The settings parameters and the last logic result are part of the api keys. If settings are changed, it takes around another second until the new expected result is visible in the status.

## [HTTP Api](http-en.md)

## [MQTT](mqtt-en.md)
