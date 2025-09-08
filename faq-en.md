[Deutsch](faq-de.md) &bull; English

# FAQ

# OCPP

## [How to start the Connection](ocpp-en.md) 

## How start a Transaktion in OCPP with Authentication
To send a Start Transaction the Request used is RemoteStartTransaction.req. With this the Charging will start.

### RemoteStartTransaction

|FIELD NAME | FIELD TYPE | CARD | DESCRIPTION |
| ----------- | ------------- | ---------- | ------------------------------------- |
| connectorId | integer | 0..1 | Optional. Number of the connector on which to start the transaction connectorId SHALL be > 0 |
| idTag | IdToken | 1..1 | Required. The identifier that Charge Point must use to start a transaction.
| chargingProfile | ChargingProfile | 0..1 | Optional. Charging Profile to be used by the Charge Point for the requested transaction ChargingProfilePurpose MUST be set to TxProfile |

A Request via RemoteStartTransaction containing chargingProfile is not yet implementet and as such a seperate Request has to be send with set charging Profile.

### SetChargingProfile.req

| FIELD NAME | FIELD TYPE | CARD | DESCRIPTION |
| ----------- | ------------- | ---------- | ------------------------------------- |
| connectorId | integer | 1..1 | Required. The connector to which the charging profile applies. If connectorId = 0, the message contains an overall limit for the Charge Point. |
| csChargingProfiles | ChargingProfile | 1..1 | Required. The charging profile to be set at the Charge Point.|

To send a Stop Transaction the Request used ist RemoteStopTransaction.req. With this the Chargin will Stop
|FIELD NAME | FIELD TYPE | CARD | DESCRIPTION |
| ----------- | ------------- | ---------- | ------------------------------------- |
| transactionId | integer |  1..1 | Required. The identifier of the transaction which Charge Point is requested to |


# API 











