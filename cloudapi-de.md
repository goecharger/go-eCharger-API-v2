Deutsch &bull; [English](cloudapi-en.md)

# go-eCharger Cloud HTTP API

[Die API Keys](apikeys-de.md) des go-eCharger V3 können über die Cloud HTTP Api gelesen und geschrieben werden.

Für die Cloud API ist go-eCharger Firmware Version **052** notwendig. Die App kann ab Version **2.3** die API aktivieren.

Die Cloud HTTP API muss in der App erst aktiviert werden. In der App findet man die Einstellung findet man unter Internet / Erweiterte Einstellungen. 
Alternativ kann der api key **cae** (cloud api enabled) auf true gesetzt werden.

Für den Zugriff auf die HTTP API wird ein Zugangstoken benötigt. Dieser wird ebenfalls in der App unter Internet / Erweiterte Einstellungen angezeigt. 
Alternativ kann man ihn über den api key **cak** (cloud api key) auslesen. Der API key wird am Charger generiert und kann nicht verändert werden. 

Ein neuer API key kann in der App generiert werden, bzw. durch das Setzen des api keys **cak** mit einem beliebigen Wert.

## Rate Limiting

Rate limiting ist nicht vorgesehen. Es macht jedoch keinen Sinn mehr als eine Abfrage pro Sekunde auf /api/status zu machen da auch der go-eCharger die Daten nicht schneller liefern kann.

## HTTP Endpunkt

Die URLs zum Abfragen bzw Setzen der Parameter am go-eCharger lauten:
<pre>
https://<b>serial_number</b>.api.v3.go-e.io/api/status
https://<b>serial_number</b>.api.v3.go-e.io/api/set
</pre>

Wobei **serial_number** durch die jeweilige 6-stellige Seriennummer des Chargers ersetzt werden muss - mit führenden 0

### Authentifizierung
Die Authentifizierung erfolgt entweder mittels GET Parameter oder durch senden des HTTP Headers **Authorization: Bearer**
<pre>
Authorization: Bearer <b>myapitoken</b>
</pre>

Falls die Authentifizierung mittels GET Parameter erfolgen soll, ist der Authentifizierungstoken als **token** Parameter anzugeben:
<pre>
https://<b>serial_number</b>.api.v3.go-e.io/api/status?token=<b>myapitoken</b>
</pre>


## /api/status
Wird verwendet um das Status-Objekt des go-eCharger abzufragen.

Der Server antwortet mit:
- **HTTP 403** (Forbidden) wenn der go-eCharger offline ist bzw. die Cloud API nicht aktiviert hat.
- **HTTP 404** (Not found) wenn die Authentifizierung korrekt war, aber keine der go-eCharger gerade keine Daten sendet.
- **HTTP 200** (Found) wenn aktuelle Daten vorliegen. Der Server sendet ein JSON Objekt mit dem Status Objekt mit allen (bzw. durch filter selektierten) api-keys des go-eChargers

Im HTTP Header **last-modified** steht bei einer erfolgreichen Anfrage (200) von welchem Zeitpunkt die Daten sind.

### age Parameter
Mit dem GET Parameters `age` kann angegeben werden, wie alt das Status Objekt maximal sein darf. 

Standardmäßig sind 30 Sekunden eingestellt, wenn der go-eCharger innerhalb von diesen 30 Sekunden keine Daten gesendet hat, wird stattt HTTP 200, HTTP 404 ausgegeben.

Durch setzen des GET Parameters kann ein beliebiger Zeitraum eingestellt werden. Es gibt jedoch keine Garantie wie lange Status Objekte am Server aufbewahrt werden.

Beispiel:
<pre>
https://000001.api.v3.go-e.io/api/status?token=myapitoken<b>&age=5</b>
</pre>

### filter Parameter
Mit dem GET Parameter `filter` kann ausgewählt werden, welche api keys des Chargers mitgesendet werden. Die api keys müssen durch Beistriche getrennt werden.

Beispiel:
<pre>
https://000001.api.v3.go-e.io/api/status?token=myapitoken&age=5<b>&filter=amp,acu,nrg</b>
</pre>

## /api/set
Wird verwendet um Werte am go-eCharger zu setzen

Der Server antwortet mit:
- **HTTP 403** (Forbidden) wenn der go-eCharger offline ist bzw. die Cloud API nicht aktiviert hat.
- **HTTP 404** (Not found) wenn die Authentifizierung korrekt war, aber keine der go-eCharger gerade nicht online ist (bzw. in den letzten 30 Sekunden online war).
- **HTTP 422** (Unprocessable Entity) wenn alle api keys abgelehnt wurden.
- **HTTP 202** (Accepted) wenn mindestens ein api key an den go-eCharger gesendet wurde. Es gibt jedoch keine Garantie dass dieser den Befehl empfängt oder akzeptiert.

Die Werte die gesetzt werden sollen, können als GET Parameter angegeben werden. Wenn die Authentifizierung über GET Parameter gewählt wurde, zusätzlich zu dem token Paramter.

Um numerische Werte von Strings zu unterscheiden zu können, sollten Strings mit "" umschlossen werden.

Beispiel:
<pre>
https://000001.api.v3.go-e.io/api/set?<i>token=myapitoken</i>&<b>amp=3&fna="my go-eCharger"</b>
</pre>


