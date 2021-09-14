# HTTP Api

Die HTTP API (v2) muss in der App erst aktiviert werden:

<img src="screenshots/http-api-app-enable.png?raw=true" width="200" />

### Alle Werte auf einmal abfragen
<small>höhere Last am System, viel traffic, sollte nicht für den Dauerbetrieb benutzt werden</small>

`http://192.168.0.75/api/status`

<img src="screenshots/http-api-status.png?raw=true" />

### Vereinzelte Werte abfragen
Um die erhöhte Last zu reduzieren, kann die Status Anfrage so gefiltert werden, dass nur bestimmte Api Keys in der Response vor kommen.
Ab Firmware 051.4:

`http://192.168.0.75/api/status?filter=rfb,alw,acu,adi,amp`

Bis Firmware 051.3 (legacy):
<small>Achtung, beim filter json parsen ging häufig der Speicher aus und es waren nie mehr als ca. 10 parameter möglich</small>

`http://192.168.0.75/api/status?filter=["rfb","alw","acu","adi","amp"]`

<img src="screenshots/http-api-status-filtered.png?raw=true" />

### Werte setzen
Jeder zu setzende api wert muss als Url Query parameter (GET Parameter) mitgegeben werden. Der Wert muss dabei als JSON encodiert werden. Bei Strings zB dürfen die Anführungszeichen davor und danach nicht fehlen.

```
http://192.168.0.75/api/set?fna="mein charger"
http://192.168.0.75/api/set?amp=16
http://192.168.0.75/api/set?dwo=null
http://192.168.0.75/api/set?dwo=3.14
http://192.168.0.75/api/set?bac=false&sdp=true
```

TODO für go-e: erwarteter Response Inhalt
