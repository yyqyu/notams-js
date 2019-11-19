# Notams
Retrieve NOTAMs (Notices to Airmen) from https://pilotweb.nas.faa.gov using a regular XMLHttpRequest.
## Javascript:
```js
function getNotamData(icao, callback){
	var notams = new XMLHttpRequest();
	notams.open("GET", "https://superananas.de/runways/retrieveNotam.php?icao=" + icao ,true);
	notams.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
	notams.onreadystatechange = function () {
		if (notams.readyState != 4 ) {
			return;
		}
		if(notams.status != 400){
			callback(JSON.parse(notams.responseText));
			return;
		}
		callback(notams.status);
	}
    notams.send(); 
}
```
## Callback:
```js
getNotamData(icao, function(array){
	console.log(array);
})
```

## Output:
This Example shows one Notam for "EHAM" (Amsterdam Airport Schiphol).
```json
    {
        "id": 0,
        "notam": "A1732\/19 NOTAMR A1702\/19\nQ) EHAA\/QMXLT\/IV\/M  \/A \/000\/999\/5218N00446E005\nA) EHAM B) 1911151354 C) 1912050500 EST\nE) TWY R: DO NOT EXCEED MINIMUM REQUIRED POWER SETTING WHILE\nTAXIING.\nCREATED: 15 Nov 2019 13:55:00 \nSOURCE: EUECYIYN",
        "series": "A",
        "number": "1732",
        "year": "19",
        "suffix": "Replacing Notam",
        "fir": "EHAA",
        "qcode": {
            "object": "TAXIWAY",
            "attribute": "LIMITED TO",
            "rawObject": "MX",
            "rawAttribute": "LT",
            "category": "AERODROME"
        },
        "traffic": "IFR & VFR",
        "purpose": [
            "(M)NOTAM contains miscellaneous information and will not appear in PIB, unless specifically requested."
        ],
        "scope": "Aerodrome",
        "flightLevelBottom": "000",
        "flightLevelTop": "999",
        "coordinates": {
            "north": "5218N",
            "west": "00446E",
            "radius": "005"
        },
        "where": "EHAM",
        "start": {
            "year": "19",
            "month": "11",
            "day": "15",
            "hour": "13",
            "minute": "54",
            "rawTime": 1573772400
        },
        "end": {
            "year": "19",
            "month": "12",
            "day": "05",
            "hour": "05",
            "minute": "00",
            "rawTime": 1575500400
        },
        "specifics": null,
        "text": "TWY R: DO NOT EXCEED MINIMUM REQUIRED POWER SETTING WHILE\nTAXIING.\n",
        "lowerLimit": null,
        "upperLimit": null,
        "codes": "IV\/A\/M"
    }
```
    
# API
most useful values

`notams.notam`

`notams.series`

`notams.number`

`notams.qcode`

`notams.text`

Input Type: 

- `string`

Valid values:

- `a single ICAO code`

## Contributing

Visit my Aviation Tools related website https://atccom.de/

Contributions welcome!

## License

No License available yet
