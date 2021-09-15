[Deutsch](mqtt-de.md) &bull; English

# MQTT

[The api keys](apikeys-en.md) can be read and written via MQTT. Since firmware 051.5 changing values via MQTT has to be enabled explicitly as it is not allowed by default anymore.

For that MQTT has to be enabled from the app:

<img src="screenshots/mqtt-app-enable.png?raw=true" width="200" />

**Warning:** Use the preconfigured test broker url only for short test sessions, as this opens an attack surface for strangers from the internet, who can also then delete wifi configs or restart the charger.

## Topics

TODO for go-e: Document the topics for reading/writing.
