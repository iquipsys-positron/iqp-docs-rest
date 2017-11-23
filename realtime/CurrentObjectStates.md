## Get current object states

# GET /sites/:site_id/curr_object_states

Returns json data about worksite all current object states.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/curr_object_states
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
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/curr_object_states
`

# Example Responce

```
"total": 41,
"data": [
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"device_id": "ff65253d71fc4e278d9e89013095c927",
	"object_id": "e17172ad05d448d18450aca6f6fff653",
	"time": "2017-11-21T12:38:00.694Z",
	"online": 967114.3030001143,
	"immobile": 0,
	"assign_id": null,
	"pressed": null,
	"long_pressed": null,
	"pos_time": "2017-11-21T12:37:58.214Z",
	"state_time": "2017-11-21T12:37:16.861Z",
	"rules": [],
	"pos": {
		"type": "Point",
		"coordinates": [
		30.65763957576943,
		64.67295468254318
		],
	},
	"alt": 200,
	"angle": 225,
	"speed": 5,
	"quality": 2,
	"attend_time": "2017-11-10T07:59:27.391Z",
	"expected": true,
	"connected": false,
	"offline": 0,
	"rule_time": null,
	"attend_start": "2017-11-21T00:00:00.000Z",
	"zones": [
	{
		"exited": false,
		"entered": false,
		"duration": 1564.2050000000002,
		"state_id": "d290e04542364648b058e252baebb4cf"
	}
	],
	"group_ids": [
	"e892a72d6a2b4ca8899efb44a860f7d0",
	"561154dd93154c9eb307d1f0569a67db"
	],
	"id": "ff65253d71fc4e278d9e89013095c927"
},
...
}
```

---

## Get current object state info

# GET /sites/:site_id/curr_object_states/:state_id

Returns json data about one or all current object state on specified site. If you don't set *state_id* result will contain all site curr_object_states. To get info only about one current object state you should set *state_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/curr_object_states/:state_id
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
| state_id | No | current object state ids can be retrieved from */sites/:site_id/curr_object_states* Set current object state id to get data for one current object state. | | a889326f2b6b48bbbea388dfdeb7245b |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/curr_object_states/a889326f2b6b48bbbea388dfdeb7245b
`

# Example Responce

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"device_id": "a889326f2b6b48bbbea388dfdeb7245b",
	"object_id": "6fb41f9479024da79b9f76a2daba053c",
	"time": "2017-11-21T13:07:10.676Z",
	"online": 968864.3100001229,
	"immobile": 1060.8820000000007,
	"assign_id": null,
	"pressed": null,
	"long_pressed": null,
	"pos_time": "2017-11-21T13:07:06.669Z",
	"state_time": "2017-11-21T13:06:54.620Z",
	"pos": {
		"type": "Point",
		"coordinates": [
		30.66050963280091,
		64.67386138083894
		],
	},
	"alt": 200,
	"angle": 135,
	"speed": 0,
	"quality": 2,
	"rules": [],
	"attend_time": "2017-11-10T07:59:27.366Z",
	"expected": true,
	"connected": false,
	"offline": 0,
	"rule_time": null,
	"attend_start": "2017-11-21T00:00:00.000Z",
	"zones": [
	{
		"exited": false,
		"entered": false,
		"duration": 3314.2050000000036,
		"zone_id": "d290e04542364648b058e252baebb4cf"
	}
	],
	"group_ids": [
	"561154dd93154c9eb307d1f0569a67db"
	],
	"id": "a889326f2b6b48bbbea388dfdeb7245b"
}
```

---

## Edit current object state

# PUT /sites/:site_id/curr_object_states/:state_id

Edit existing current object state. As a result returns all current object states.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/zones/:zone_id
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
| device_id | No | Device ids can be retrieved from */sites/:site_id/devices* | | ff65253d71fc4e278d9e89013095c927 |
| object_id | No | Object ids can be retrieved from */sites/:site_id/control_objects/* | | e17172ad05d448d18450aca6f6fff653 |
| time | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T13:13:53.263Z | 
| online | Online object time, store in seconds | | 95656.4545 |
| immobile | Immobile object time, store in seconds. If object not immobile value is 0. | | 95656.4545 |
| assigned_id | Id of car or asset on wich object with object_id assigned for work. Object ids can be retrieved from */sites/:site_id/control_objects*. If object doesn't have assign value is *null* | | null, e892a72d6a2b4ca8899efb44a860f7d0 |
| pressed | Boolean indicator to store is button on tracker pressed | | null, true, false |
| long_pressed | Boolean indicator to store is button on tracker pressed | | null, true, false |
| pos_time | Object position time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T13:13:53.263Z | 
| state_time | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T13:13:53.263Z | 
| rules | Activated rules for object state. If rule is triggered it stores in *rules* array. Rule ids can be retrieved from */sites/:site_id/rules* | | [ "e892a72d6a2b4ca8899efb44a860f7d0" ] |
| pos | No | Position of the object, it stores in geoJSON point format - object with properties *type* and *coordinates* with array longtitude latitude pair.  | | { "type": "Point", "coordinates": [ 30.694127082824707, 64.69424468980802 ], } |
| alt | No | Altitude of the object position. Stores in meters | | 200 |
| angle | No | Object azimuth, displays moving direction. Stores in degrees | | 45 |
| speed | No | Object speed, stores in kilometers per hour | | 50 |
| quality | No | Displayes quality of signal from tracker | | 2 |
| offline | No | Offline object time, stores in seconds. | | 0 |
| zones | Array of zone ids. If object position on any zone, zone id stores in *zones* array. Zone ids can be retrieved from */sites/:site_id/zones* | | [ "561154dd93154c9eb307d1f0569a67db" ] |
| groups | Array of group ids. If object in any group, group id stores in *group* array. Group ids can be retrieved from */sites/:site_id/object_groups* | | [ "ff65253d71fc4e278d9e89013095c927" ] |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| state_id | No | state ids can be retrieved from */sites/:site_id/curr_object_states* | | ff65253d71fc4e278d9e89013095c927 |

# Example Request

`
PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/curr_object_states/ff65253d71fc4e278d9e89013095c927
`

# Example Body

```
{
    "speed": "55"
}
```

# Example Responce

```
{
	"total": 41,
	"data": [
	{
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"device_id": "ff65253d71fc4e278d9e89013095c927",
		"object_id": "e17172ad05d448d18450aca6f6fff653",
		"time": "2017-11-21T13:13:53.263Z",
		"online": 969266.8720001134,
		"immobile": 0,
		"assign_id": null,
		"pressed": null,
		"long_pressed": null,
		"pos_time": "2017-11-21T13:13:50.799Z",
		"state_time": "2017-11-21T13:12:59.242Z",
		"rules": [],
		"pos": {
			"type": "Point",
			"coordinates": [
			30.662765681988713,
			64.67516617768769
			],
		},
		"alt": 200,
		"angle": 135,
		"speed": 55,
		"quality": 2,
		"attend_time": "2017-11-10T07:59:27.391Z",
		"expected": true,
		"connected": false,
		"offline": 0,
		"rule_time": null,
		"attend_start": "2017-11-21T00:00:00.000Z",
		"zones": [
		{
			"exited": false,
			"entered": false,
			"duration": 76.67699999999999,
			"zone_id": "7fa504f7b9034d979c27697f0520fdde"
		}
		],
		"group_ids": [
		"e892a72d6a2b4ca8899efb44a860f7d0",
		"561154dd93154c9eb307d1f0569a67db"
		],
		"id": "ff65253d71fc4e278d9e89013095c927"
	},
	...
}
```

---

## Delete all current object states

# DELETE /sites/:site_id/curr_object_states/:state_id

Delete all existing current object state by state id. As result return all deleted states.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/curr_object_states/:state_id
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
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/curr_object_states
`

# Example Responce

```
{
	"total": 41,
	"data": [
	{
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"device_id": "ff65253d71fc4e278d9e89013095c927",
		"object_id": "e17172ad05d448d18450aca6f6fff653",
		"time": "2017-11-21T13:13:53.263Z",
		"online": 969266.8720001134,
		"immobile": 0,
		"assign_id": null,
		"pressed": null,
		"long_pressed": null,
		"pos_time": "2017-11-21T13:13:50.799Z",
		"state_time": "2017-11-21T13:12:59.242Z",
		"rules": [],
		"pos": {
			"type": "Point",
			"coordinates": [
			30.662765681988713,
			64.67516617768769
			],
		},
		"alt": 200,
		"angle": 135,
		"speed": 55,
		"quality": 2,
		"attend_time": "2017-11-10T07:59:27.391Z",
		"expected": true,
		"connected": false,
		"offline": 0,
		"rule_time": null,
		"attend_start": "2017-11-21T00:00:00.000Z",
		"zones": [
		{
			"exited": false,
			"entered": false,
			"duration": 76.67699999999999,
			"zone_id": "7fa504f7b9034d979c27697f0520fdde"
		}
		],
		"group_ids": [
		"e892a72d6a2b4ca8899efb44a860f7d0",
		"561154dd93154c9eb307d1f0569a67db"
		],
		"id": "ff65253d71fc4e278d9e89013095c927"
	},
	...
}
```

---

## Delete current object state

# DELETE /sites/:site_id/curr_object_states/:state_id

Delete existing current object state by state id.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/curr_object_states/:state_id
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
| state_id | No | state ids can be retrieved from */sites/:site_id/curr_object_states* | | ff65253d71fc4e278d9e89013095c927 |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/curr_object_states/ff65253d71fc4e278d9e89013095c927
`

# Example Responce

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"device_id": "ff65253d71fc4e278d9e89013095c927",
	"object_id": "e17172ad05d448d18450aca6f6fff653",
	"time": "2017-11-21T13:41:26.526Z",
	"online": 970920.1350001132,
	"immobile": 0,
	"assign_id": null,
	"pressed": null,
	"long_pressed": null,
	"pos_time": "2017-11-21T13:41:20.812Z",
	"state_time": "2017-11-21T13:40:37.439Z",
	"rules": [],
	"pos": {
		"type": "Point",
		"coordinates": [
		30.66152257116668,
		64.65992657690555
		],
	},
	"alt": 200,
	"angle": 315,
	"speed": 5,
	"quality": 2,
	"attend_time": "2017-11-10T07:59:27.391Z",
	"expected": true,
	"connected": false,
	"offline": 0,
	"rule_time": null,
	"attend_start": "2017-11-21T00:00:00.000Z",
	"zones": [
	{
		"exited": false,
		"entered": false,
		"duration": 1442.227999999999,
		"zone_id": "ae5a413ec4d04782bfeee2bfa0af07ff"
	}
	],
	"group_ids": [
	"e892a72d6a2b4ca8899efb44a860f7d0",
	"561154dd93154c9eb307d1f0569a67db"
	],
	"id": "ff65253d71fc4e278d9e89013095c927"
}
```