[Deutsch](cloudapi-de.md) &bull; English

# go-eCharger Cloud HTTP API

[The API Keys](apikeys-en.md) of the go-eCharger V3 can be read and written via the Cloud HTTP Api.

The go-eCharger firmware version **052** is required for the Cloud API. The app can activate the API from version **2.3** on.

The Cloud HTTP API must first be activated in the app. The setting can be found in the app under Internet / Advanced Settings.
Alternatively, the api key **cae** (cloud api enabled) can be set to true.

An access token is required to access the HTTP API. This token is displayed in the app under Internet / Advanced Settings.
Alternatively, it can be read out using the api key **cak** (cloud api key). The API key is generated on the charger and cannot be changed arbitrarily.

A new API key can be generated in the app or by setting the api key **cak** with any value. The old API key is then invalid.

## Rate Limiting

Rate limiting is not used. However, it makes no sense to do more than one query per second on /api/status because the go-eCharger cannot deliver the data faster either.

## HTTP endpoint

The URLs for querying or setting the parameters on the go-eCharger are:
<pre>
https://<b>serial_number</b>.api.v3.go-e.io/api/status
https://<b>serial_number</b>.api.v3.go-e.io/api/set
</pre>

Whereby **serial_number** must be replaced by the respective 6-digit serial number of the charger - with leading 0s

### Authentication
The authentication cam be done either with a GET parameter or by sending the HTTP header **Authorization: Bearer**
<pre>
Authorization: Bearer <b>api-key</b>
</pre>

If the authentication is done by using the GET parameter, the authentication token must be specified as a **token** parameter:
<pre>
https://<b>serial_number</b>.api.v3.go-e.io/api/status?token=<b>api-token</b>
</pre>


## /api/status
Is used to query the status object of the go-eCharger.

The server replies with:
- **HTTP 403** (Forbidden) if the go-eCharger is offline or the Cloud API is not activated.
- **HTTP 404** (Not found) if the authentication was correct, but the go-eCharger is not currently sending any data.
- **HTTP 200** (Found) if current data is available. The server sends a JSON object with the status object with all (or filter-selected) api keys of the go-eCharger

In the case of a successful request (200), the **last-modified** HTTP header indicates when the data is from.

### age parameter
The GET parameter `age` can be used to specify how old the status object may be.

30 seconds are set by default, and if the go-eCharger has not sent any data within these 30 seconds, HTTP 404 are sent.

Any time period can be set by setting the GET parameter. However, there is no guarantee how long status objects will be kept on the server.

Example:
<pre>
https://000001.api.v3.go-e.io/api/status?token=myapitoken<b>&age=5</b>
</pre>

### filter parameter
The GET parameter `filter` can be used to select which api keys of the charger are to be sent. The api keys must be separated by commas.

Example:
<pre>
https://000001.api.v3.go-e.io/api/status?token=myapitoken&age=5<b>&filter=amp,acu,nrg</b>
</pre>

## /api/set
Is used to set values on the go-eCharger

The server replies with:
- **HTTP 403** (Forbidden)if the go-eCharger is offline or the Cloud API is not activated.
- **HTTP 404** (Not found) if the authentication was correct, but the go-eCharger is currently not online (or was online in the last 30 seconds).
- **HTTP 422** (Unprocessable Entity) if all api keys were rejected.
- **HTTP 202** (Accepted) if at least one api key was sent to the go-eCharger. However, there is no guarantee that it will receive or accept the command.

The values to be set can be specified as GET parameters. If the authentication via GET parameter is used, just in addition to the token parameter.

In order to be able to distinguish numerical values from strings, strings should be enclosed with "".

Example:
<pre>
https://000001.api.v3.go-e.io/api/set?<i>token=myapitoken</i>&<b>amp=3&fna="my go-eCharger"</b>
</pre>
