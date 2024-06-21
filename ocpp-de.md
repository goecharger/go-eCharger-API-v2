Deutsch &bull; [English](ocpp-en.md)

# OCPP

Neuere go-eCharger Firmwares unterstützen das Verbinden mit OCPP Backends. Die Entwicklung und Tests wurden mit [Steve](https://github.com/steve-community/steve) durchgeführt, ein OCPP Backend, welches sehr einfach zum aufsetzen und betreiben war (containerized und bare-metal auf Raspberry Pies und große Server). OCPP kann über die App oder die [http API](http-de.md) aktiviert werden.

## Über die App die MQTT Verbindung aktivieren und prüfen

Unten im Tab "Internet", dann OCPP im Menü anwählen

<img src="screenshots/ocpp-app-enable.png?raw=true" width="200" />

## Über die http API die OCPP Verbindung aktivieren und prüfen

Die Chargers verfügen über API Keys zum Konfigurieren und Prüfen der OCPP Verbindung. Diese API Keys können mit der http api verwendet werden.

Beispiel: http://192.168.0.77/api/set?ocppe=true&ocppu=ws://ocpp.server:1234/chargers/201564

| api key | Beschreibung                  | Datentyp | R?W? | Kategorie |
| ------- | ----------------------------- | -------- | ---- | --------- |
| ocppe   | OCPP aktiviert                | bool     | R/W  | Config    |
| ocppu   | OCPP server url               | string   | R/W  | Config    |
| ocppg   | OCPP use global CA Store      | bool     | R/W  | Config    |
| ocppcn  | OCPP skipCertCommonNameCheck  | bool     | R/W  | Config    |
| ocppss  | OCPP skipServerVerification   | bool     | R/W  | Config    |
| ocpps   | OCPP gestartet                | bool     | R    | Status    |
| ocppc   | OCPP verbunden                | bool     | R    | Status    |
| ocppca  | OCPP verbunden (Zeitstempel in Millisekunden seit dem Hochfahren) Subtrahiere von der reboot-zeit (rbt) um die Dauer seit Verbunden zu erhalten | null or milliseconds | R | Status |
| ocppa   | OCPP verbunden und akzeptiert | bool      | R    | Status    |
| ocppaa  | OCPP verbunden und akzeptiert  (Zeitstempel in Millisekunden seit dem Hochfahren) Subtrahiere von der reboot-zeit (rbt) um die Dauer seit Verbunden und akzeptiert zu erhalten | null or milliseconds | R | Status |
| ocpph   | OCPP heartbeat interval (kann auch mit `GetConfiguration` und `ChangeConfiguration` gelesen/geschrieben werden) | seconds | R/W | Config |
| ocppi   | OCPP meter values sample interval (kann auch mit `GetConfiguration` und `ChangeConfiguration` gelesen/geschrieben werden) | seconds | R/W | Config |
| ocppai   | OCPP clock aligned data interval (kann auch mit `GetConfiguration` und `ChangeConfiguration` gelesen/geschrieben werden) | seconds | R/W | Config |
| ocppd   | OCPP dummy card id (wird benutzt wenn keine Karte hingehalten wird und es schon erlaubt ist. | string | R/W | Config |
| ocppr   | OCPP rotate phases on charger | bool    | R/W  | Config    |
| ocpple  | OCPP letzter error            | string or null | R | Status |
| ocpplea | OCPP letzter error (Zeitstempel in Millisekunden seit dem Hochfahren) Subtrahiere von der reboot-zeit (rbt) um die Dauer seit Error zu erhalten | null or milliseconds | R | Status |
| ocpprl  | OCPP remote logging (usually only enabled by go-e support to allow debugging) | bool | R/W | Config |
| ocppck  | OCPP client key               | string   | R/W  | Config    |
| ocppcc  | OCPP client cert              | string   | R/W  | Config    |
| ocppsc  | OCPP server cert              | string   | R/W  | Config    |

## Unterstützte Feature Profile
| Feature Profil          | Unterstützung |
| ----------------------- | ------------- |
| Core                    | Unterstützt   |
| FirmwareManagement      | Unterstützt   |
| LocalAuthListManagement |               |
| Reservation             |               |
| SmartCharging           | Unterstützt (JA, wir unterstützen auch numberOfPhases=1 für PhasenUmschaltung) |
| RemoteTrigger           | Unterstützt   |

## Unterstützte Nachrichten

| Message                       | Profil                     | Unterstützung am go-eCharger |
| ----------------------------- | -------------------------- | ------------- |
| Authorize                     | Core                       | Implementiert |
| BootNotification              | Core                       | Implementiert |
| ChangeAvailability            | Core                       |               |
| ChangeConfiguration           | Core                       | Implementiert (see supported config keys below) |
| ClearCache                    | Core                       |               |
| DataTransfer                  | Core                       |               |
| GetConfiguration              | Core                       | Implementiert (see supported config keys below) |
| Heartbeat                     | Core                       | Implementiert |
| MeterValues                   | Core                       | Implementiert |
| RemoteStartTransaction        | Core                       | Implementiert |
| RemoteStopTransaction         | Core                       | Implementiert |
| Reset                         | Core                       | Implementiert |
| StartTransaction              | Core                       | Implementiert |
| StatusNotification            | Core                       | Implementiert |
| StopTransaction               | Core                       | Implementiert |
| UnlockConnector               | Core                       | Implementiert |
| GetDiagnostics                | Firmware Management        |               |
| DiagnosticsStatusNotification | Firmware Management        |               |
| FirmwareStatusNotification    | Firmware Management        | Implementiert |
| UpdateFirmware                | Firmware Management        | Implementiert |
| GetLocalListVersion           | Local Auth List Management |               |
| SendLocalList                 | Local Auth List Management |               |
| CancelReservation             | Reservation                |               |
| ReserveNow                    | Reservation                |               |
| ClearChargingProfile          | Smart Charging             | Implementiert |
| GetCompositeSchedule          | Smart Charging             |               |
| SetChargingProfile            | Smart Charging             | Implementiert |
| TriggerMessage                | Remote Trigger             | Implementiert |

## Unterstützte config keys in GetConfiguration und ChangeConfiguration

Die OCPP Message `GetConfiguration` wird verwendet, um einzelne oder gleich mehrere config Werte vom Charger zu holen. Die OCPP message `ChangeConfiguration` kann einzelne oder auch mehrere config values am Charger setzen.

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