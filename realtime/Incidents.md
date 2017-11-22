## Get site incidents

# GET /sites/:site_id/incidents

Returns json array with data about all incidents on specified site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/incidents
`

# Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |


# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/incidents
`

# Example Responce

```
{
	"total": 17,
	"data": [
	{
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"create_time": "2017-11-21T13:10:07.880Z",
		"rule_id": "c71278120b9c4e2a8773e1c09503e532",
		"event_id": "1ae022db13d7479f98b04f92d711691a",
		"severity": 50,
		"time": "2017-11-21T13:10:07.849Z",
		"pos": {
			"type": "Point",
			"coordinates": [
			30.66118039733191,
			64.68878419507675
			],
		},
		"object_id": "7fd8fb30b9e44f2da9192b1e4a21ecf0",
		"assign_id": null,
		"zone_id": "799f183da6f347dbb876863726b1bd4b",
		"description": "Immobility in work zone",
		"expected_value": 15,
		"actual_value": 15.014683333333325,
		"value_units": "min",
		"closed": false,
		"id": "7318f275caca43dea0f20e1113c6f102"
	},
	...
}
```

---

## Get incident info

# GET /sites/:site_id/incidents/:incident_id

Returns json data about one or all incident on specified site. If you don't set *incident_id* result will contain all site incidents. To get info only about one incident you should set *incident_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/incidents/:incident_id
`

# Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |


# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| incident_id | No | incident ids can be retrieved from */sites/:site_id/incidents* Set incident id to get data for one incident. | | 7623803486e64b0a99dc8503e97a7058 |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/incidents/7623803486e64b0a99dc8503e97a7058
`

# Example Responce

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"create_time": "2017-11-21T11:56:25.953Z",
	"rule_id": "c71278120b9c4e2a8773e1c09503e532",
	"event_id": "8c7aa6a9a8d34e858638161a20e56fe8",
	"severity": 50,
	"time": "2017-11-21T11:56:25.920Z",
	"pos": {
		"type": "Point",
		"coordinates": [
		30.62629740638733,
		64.69652843487013
		],
	},
	"object_id": "dfc175a4d12c47fda8684b7a762e91e0",
	"assign_id": null,
	"zone_id": "9f88b6307a3645f597bc4e48f7758ee1",
	"description": "Immobility in work zone",
	"expected_value": 15,
	"actual_value": 15.015550000000003,
	"value_units": "min",
	"closed": false,
	"id": "7623803486e64b0a99dc8503e97a7058"
}
```

---

## Create incident

# POST /sites/:site_id/incidents

Creates new incident from json string for specified site. 

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/incidents
`

# Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |
| Requires body | YES |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

- ### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| rule_id | No | Defines what rule was triggered for this incident. Rule ids can be retrieved from */sites/:site_id/rules/* | | c71278120b9c4e2a8773e1c09503e532 |
| pos | Yes | Position of the incident. It stores in geoJSON point format - object with property *coordinates* with array longtitude latitude pair.  | | { "coordinates": [ 30.646963119506836, 64.68692440226665 ] } |
| severity | Yes | Severity of the rulre, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. | | 0, 50, 100 |
| object_id | Yes | Object registered in incident. Object ids can be retrieved from */sites/:site_id/control_objects/* | | e17172ad05d448d18450aca6f6fff653 |
| assign_id | No | Equipment or asset id assigned to object. If object doesn't have assign value is null. These ids can be retrieved from */sites/:site_id/control_objects/* | | null, e17172ad05d448d18450aca6f6fff653 |
| zone_id | No | Zone where incident happens. Zone ids can be retrieved from */sites/:site_id/zones/* | | 9f88b6307a3645f597bc4e48f7758ee1 |
| description | Yes | Name of the incident | | Immobility in work zone |
| expected_value | Yes | Parameter value from rule. For example rule is immobility for 15 mins - value will be 15 | | 15 |
| actual_value | Yes | Actual parameter value. | | 15.01 |
| value_units | Yes | Units of the parameter value | | min |
| closed | Yes | Boolean variable, which displays is incident closed | | true, false |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/incidents
`

# Example Body

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"rule_id": "c71278120b9c4e2a8773e1c09503e532",
	"event_id": "8c7aa6a9a8d34e858638161a20e56fe8",
  	"pos": {
		"type": "Point",
		"coordinates": [
		30.62629740638733,
		64.69652843487013
		]
	},
	"severity": 50,
	"object_id": "dfc175a4d12c47fda8684b7a762e91e0",
	"assign_id": null,
	"zone_id": "9f88b6307a3645f597bc4e48f7758ee1",
	"description": "Immobility in work zone",
	"expected_value": 15,
	"actual_value": 15.015550000000003,
	"value_units": "min",
	"closed": false
}
```

# Example Responce

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"rule_id": "c71278120b9c4e2a8773e1c09503e532",
	"event_id": "8c7aa6a9a8d34e858638161a20e56fe8",
	"pos": {
		"coordinates": [
		30.62629740638733,
		64.69652843487013
		],
		"type": "Point"
	},
	"severity": 50,
	"object_id": "dfc175a4d12c47fda8684b7a762e91e0",
	"assign_id": null,
	"zone_id": "9f88b6307a3645f597bc4e48f7758ee1",
	"description": "Immobility in work zone",
	"expected_value": 15,
	"actual_value": 15.015550000000003,
	"value_units": "min",
	"create_time": "2017-11-21T14:28:33.284Z",
	"time": "2017-11-21T14:28:33.284Z",
	"closed": false,
	"id": "2141085d65e94c3b83cf240dfdd4b40f"
}
```

---

## Edit incident

# PUT /sites/:site_id/incidents/:incident_id

Edit existing incident.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/incidents/:incident_id
`

# Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |
| Requires body | YES |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

- ### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | No | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| rule_id | No | Defines what rule was triggered for this incident. Rule ids can be retrieved from */sites/:site_id/rules/* | | c71278120b9c4e2a8773e1c09503e532 |
| pos | Yes | Position of the incident. It stores in geoJSON point format - object with property *coordinates* with array longtitude latitude pair.  | | { "coordinates": [ 30.646963119506836, 64.68692440226665 ] } |
| severity | Yes | Severity of the rulre, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. | | 0, 50, 100 |
| object_id | Yes | Object registered in incident. Object ids can be retrieved from */sites/:site_id/control_objects/* | | e17172ad05d448d18450aca6f6fff653 |
| assign_id | No | Equipment or asset id assigned to object. If object doesn't have assign value is null. These ids can be retrieved from */sites/:site_id/control_objects/* | | null, e17172ad05d448d18450aca6f6fff653 |
| zone_id | No | Zone where incident happens. Zone ids can be retrieved from */sites/:site_id/zones/* | | 9f88b6307a3645f597bc4e48f7758ee1 |
| description | Yes | Name of the incident | | Immobility in work zone |
| expected_value | Yes | Parameter value from rule. For example rule is immobility for 15 mins - value will be 15 | | 15 |
| actual_value | Yes | Actual parameter value. | | 15.01 |
| value_units | Yes | Units of the parameter value | | min |
| closed | Yes | Boolean variable, which displays is incident closed | | true, false |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| incident_id | No | incident ids can be retrieved from */sites/:site_id/incidents* | | 2141085d65e94c3b83cf240dfdd4b40f |

# Example Request

`
PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/incidents/2141085d65e94c3b83cf240dfdd4b40f
`

# Example Body

```
{
    "time": "2017-11-21T16:30:33.284Z",
    "severity": 100,
	"actual_value": 18.05
}
```

# Example Responce

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"rule_id": "c71278120b9c4e2a8773e1c09503e532",
	"event_id": "8c7aa6a9a8d34e858638161a20e56fe8",
	"pos": {
		"type": "Point",
		"coordinates": [
		30.62629740638733,
		64.69652843487013
		],
	},
	"severity": 50,
	"object_id": "dfc175a4d12c47fda8684b7a762e91e0",
	"assign_id": null,
	"zone_id": "9f88b6307a3645f597bc4e48f7758ee1",
	"description": "Immobility in work zone",
	"expected_value": 15,
	"actual_value": 15.015550000000003,
	"value_units": "min",
	"create_time": "2017-11-21T14:28:33.284Z",
	"time": "2017-11-21T14:28:33.284Z",
	"closed": false,
	"id": "2141085d65e94c3b83cf240dfdd4b40f"
}
```

---

## Delete incident

# DELETE /sites/:site_id/incidents/:incident_id

Deletes existing incident.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/incidents/:incident_id
`

# Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| incident_id | No | incident ids can be retrieved from */sites/:site_id/incidents* | | 2141085d65e94c3b83cf240dfdd4b40f |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/incidents/2141085d65e94c3b83cf240dfdd4b40f
`

# Example Responce

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"rule_id": "c71278120b9c4e2a8773e1c09503e532",
	"event_id": "8c7aa6a9a8d34e858638161a20e56fe8",
	"pos": {
		"type": "Point",
		"coordinates": [
		30.62629740638733,
		64.69652843487013
		],
	},
	"severity": 50,
	"object_id": "dfc175a4d12c47fda8684b7a762e91e0",
	"assign_id": null,
	"zone_id": "9f88b6307a3645f597bc4e48f7758ee1",
	"description": "Immobility in work zone",
	"expected_value": 15,
	"actual_value": 15.015550000000003,
	"value_units": "min",
	"create_time": "2017-11-21T14:28:33.284Z",
	"time": "2017-11-21T14:28:33.284Z",
	"closed": false,
	"id": "2141085d65e94c3b83cf240dfdd4b40f"
}
```