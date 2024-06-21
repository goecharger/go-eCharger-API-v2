[Deutsch](ocpp-de.md) &bull; English

# OCPP

Recent go-eCharger firmwares support connecting to an OCPP backend. Most of our development and testing was done with [Steve](https://github.com/steve-community/steve), which was very easy to run containerized and bare-metal on raspberry pies and big servers. OCPP can be enabled using the App or the [http API](http-en.md).

## Using the App to enable and verify the MQTT connection

Tap the tab "Internet" at the bottom, then click on OCPP in the menu

<img src="screenshots/ocpp-app-enable.png?raw=true" width="200" />

## Using the http API to enable and verify the OCPP connection

The chargers provide api keys to configure and verify the ocpp connection. These api keys can be used with the http api.

Example: http://192.168.0.77/api/set?ocppe=true&ocppu=ws://ocpp.server:1234/chargers/201564

| api key | description                  | datatype | R?W? | Category |
| ------- | ---------------------------- | -------- | ---- | -------- |
| ocppe   | OCPP enabled                 | bool     | R/W  | Config   |
| ocppu   | OCPP server url              | string   | R/W  | Config   |
| ocppg   | OCPP use global CA Store     | bool     | R/W  | Config   |
| ocppcn  | OCPP skipCertCommonNameCheck | bool     | R/W  | Config   |
| ocppss  | OCPP skipServerVerification  | bool     | R/W  | Config   |
| ocpps   | OCPP started                 | bool     | R    | Status   |
| ocppc   | OCPP connected               | bool     | R    | Status   |
| ocppca  | OCPP connected (timestamp in milliseconds since reboot) Subtract from reboot time (rbt) to get number of milliseconds since connected | null or milliseconds | R | Status |
| ocppa   | OCPP connected and accepted | bool      | R    | Status   |
| ocppaa  | OCPP connected and accepted (timestamp in milliseconds since reboot) Subtract from reboot time (rbt) to get number of milliseconds since connected and accepted | null or milliseconds | R | Status |
| ocpph   | OCPP heartbeat interval (can also be read/written with `GetConfiguration` and `ChangeConfiguration`) | seconds | R/W | Config |
| ocppi   | OCPP meter values sample interval (can also be read/written with `GetConfiguration` and `ChangeConfiguration`) | seconds | R/W | Config |
| ocppai   | OCPP clock aligned data interval (can also be read/written with `GetConfiguration` and `ChangeConfiguration`) | seconds | R/W | Config |
| ocppd   | OCPP dummy card id (used when no card has been used and charging is already allowed / starting) | string | R/W | Config |
| ocppr   | OCPP rotate phases on charger | bool    | R/W  | Config   |
| ocpple  | OCPP last error               | string or null | R | Status |
| ocpplea | OCPP last error (timestamp in milliseconds since reboot) Subtract from reboot time (rbt) to get number of milliseconds since error occured | null or milliseconds | R | Status |
| ocpprl  | OCPP remote logging (usually only enabled by go-e support to allow debugging) | bool | R/W | Config |
| ocppck  | OCPP client key              | string   | R/W  | Config   |
| ocppcc  | OCPP client cert             | string   | R/W  | Config   |
| ocppsc  | OCPP server cert             | string   | R/W  | Config   |

## Supported Feature Profiles
| Feature Profile         | Support   |
| ----------------------- | --------- |
| Core                    | Supported |
| FirmwareManagement      | Supported |
| LocalAuthListManagement |           |
| Reservation             |           |
| SmartCharging           | Supported (YES we also support numberOfPhases=1 for phase switching) |
| RemoteTrigger           | Supported |

## Supported Messages

| Message                       | Profile                    | Support on go-eCharger |
| ----------------------------- | -------------------------- | ----------- |
| Authorize                     | Core                       | Implemented |
| BootNotification              | Core                       | Implemented |
| ChangeAvailability            | Core                       | |
| ChangeConfiguration           | Core                       | Implemented (see supported config keys below) |
| ClearCache                    | Core                       | |
| DataTransfer                  | Core                       | |
| GetConfiguration              | Core                       | Implemented (see supported config keys below) |
| Heartbeat                     | Core                       | Implemented |
| MeterValues                   | Core                       | Implemented |
| RemoteStartTransaction        | Core                       | Implemented |
| RemoteStopTransaction         | Core                       | Implemented |
| Reset                         | Core                       | Implemented |
| StartTransaction              | Core                       | Implemented |
| StatusNotification            | Core                       | Implemented |
| StopTransaction               | Core                       | Implemented |
| UnlockConnector               | Core                       | Implemented |
| GetDiagnostics                | Firmware Management        | |
| DiagnosticsStatusNotification | Firmware Management        | |
| FirmwareStatusNotification    | Firmware Management        | Implemented |
| UpdateFirmware                | Firmware Management        | Implemented |
| GetLocalListVersion           | Local Auth List Management | |
| SendLocalList                 | Local Auth List Management | |
| CancelReservation             | Reservation                | |
| ReserveNow                    | Reservation                | |
| ClearChargingProfile          | Smart Charging             | Implemented |
| GetCompositeSchedule          | Smart Charging             | |
| SetChargingProfile            | Smart Charging             | Implemented |
| TriggerMessage                | Remote Trigger             | Implemented |

## Supported config keys in GetConfiguration and ChangeConfiguration

The OCPP message `GetConfiguration` is used to retrieve a single or multiple config values from the charger. The OCPP message `ChangeConfiguration` is used to set or change a single or multiple config values on the charger.

| Configuration Key | Protocol Specification Chapter | go-eCharger support |
| --- | --- | --- |
| AllowOfflineTxForUnknownId | 9.1.1 | R/W |
| AuthorizationCacheEnabled | 9.1.2 |  |
| AuthorizeRemoteTxRequests | 9.1.3 | R |
| BlinkRepeat | 9.1.4 |  |
| ClockAlignedDataInterval | 9.1.5 | R/W |
| ConnectionTimeOut | 9.1.6 |  |
| ConnectorPhaseRotation | 9.1.7 | R |
| ConnectorPhaseRotationMaxLength | 9.1.8 | R |
| GetConfigurationMaxKeys | 9.1.9 | R |
| HeartbeatInterval | 9.1.10 | R/W |
| LightIntensity | 9.1.11 | R/W |
| LocalAuthorizeOffline | 9.1.12 | R/W |
| LocalPreAuthorize | 9.1.13 |  |
| MaxEnergyOnInvalidId | 9.1.14 |  |
| MeterValuesAlignedData | 9.1.15 |  |
| MeterValuesAlignedDataMaxLength | 9.1.16 |  |
| MeterValuesSampledData | 9.1.17 | R |
| MeterValuesSampledDataMaxLength | 9.1.18 | R |
| MeterValueSampleInterval | 9.1.19 | R/W |
| MinimumStatusDuration | 9.1.20 |  |
| NumberOfConnectors | 9.1.21 | R |
| ResetRetries | 9.1.22 |  |
| StopTransactionOnEVSideDisconnect | 9.1.23 |  |
| StopTransactionOnInvalidId | 9.1.24 |  |
| StopTxnAlignedData | 9.1.25 |  |
| StopTxnAlignedDataMaxLength | 9.1.26 |  |
| StopTxnSampledData | 9.1.27 |  |
| StopTxnSampledDataMaxLength | 9.1.28 |  |
| SupportedFeatureProfiles | 9.1.29 | R |
| SupportedFeatureProfilesMaxLength | 9.1.30 | R |
| TransactionMessageAttempts | 9.1.31 |  |
| TransactionMessageRetryInterval | 9.1.32 |  |
| UnlockConnectorOnEVSideDisconnect | 9.1.33 | R/W |
| WebSocketPingInterval | 9.1.34 | R/W |
| LocalAuthListEnabled | 9.2.1 | R/W |
| LocalAuthListMaxLength | 9.2.2 |  |
| SendLocalListMaxLength | 9.2.3 |  |
| ReserveConnectorZeroSupported | 9.3.1 |  |
| ChargeProfileMaxStackLevel | 9.4.1 | R |
| ChargingScheduleAllowedChargingRateUnit | 9.4.2 | R |
| ChargingScheduleMaxPeriods | 9.4.3 | R |
| ConnectorSwitch3to1PhaseSupported | 9.4.4 | R |
| MaxChargingProfilesInstalled | 9.4.5 | R |