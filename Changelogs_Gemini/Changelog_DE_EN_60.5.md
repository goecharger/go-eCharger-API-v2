## Englisch

1. Added api key to override all LED colors

2. Add api keys to show mqtt client/server key/cert metadata

3. ocpp/mqtt key/cert are now verified when set

4. Add api keys to show ocpp key/cert metadata

5. add debugging api key ss for network debugging

6. Use "mfw" as API key for reporting "cellular modem firmware version"

7. Fixes invaild GetCofiguration response when the payload is larger than internal memory, and adds optional pagination parameter: offset, limit.

8. Implements OCPP extension to set/change several API keys via GetConfiguration/ChangeConfiguration.


## German


1. API Key hinzugefügt um alle LED farben zu überschreiben

2. Api keys hinzugefügt um mqtt client/server key/cert metadata anzuzeigen

3. ocpp/mqtt key/cert werden nun beim Setzen verifiziert

4. Api keys hinzugefügt, um ocpp key/cert metadata anzuzeigen

5. api key ss hinzugefügt für besseres netzwerk debugging

6. Verwende "mfw" als API-Schlüssel für die Meldung der Firmwareversion des Mobilfunkmodems.

7. Behebt ungültige GetConfiguration Antwort wenn die Nutzdaten internen Speicher übersteigt, und fügt optionale Paginierungsparameter hinzu: offset, limit.

8. Implementiert OCPP Erweiterung um etliche API Keys mittels OCPP GetConfiguration/ChangeConfiguration zu lesen oder verändern.
