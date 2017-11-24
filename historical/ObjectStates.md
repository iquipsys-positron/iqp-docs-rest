# GET /sites/:site_id/object_states

Returns json data about worksite all object states.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_states
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |


### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_states
`

### Example response

```
{
	"total": 55,
	"data": [
	{
		"end_time": "2017-11-22T14:15:00.000Z",
		"site_id": "9958f0dd1faa494fbc48ba816a02fdd0",
		"start_time": "2017-11-22T14:00:00.000Z",
		"states": [
		{
			"site_id": "9958f0dd1faa494fbc48ba816a02fdd0",
			"time": "2017-11-22T14:00:19.052Z",
			"device_id": "08895262776344bfa33a60d201e9b29b",
			"object_id": "63b464dfdc084635856a52c557f9215e",
			"assign_id": null,
			"pos": {
				"coordinates": [
				37.640559,
				51.299172
				],
				"type": "Point"
			},
			"alt": 200,
			"speed": 10,
			"quality": 0,
			"angle": 45,
			"online": 274.592,
			"immobile": 0,
			"pressed": null,
			"long_pressed": null,
			"zone_ids": [
			"19d724c6f81a4053b7e442367a11fbd7"
			],
			"group_ids": [],
		},
		...
		],
		"id": "b83bfe5227a84ab19a83655bc6d7a6a2"
	},
	{
		"end_time": "2017-11-22T14:00:00.000Z",
		"site_id": "9958f0dd1faa494fbc48ba816a02fdd0",
		"start_time": "2017-11-22T13:45:00.000Z",
		"states": [
		...
		],
		"id": "baaf72050ddc4afe81c6d2afb2e7aad4"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Site id. These IDs can be retrieved from */sites.*|
| start_time | States stored for 15 minutes time interval. This variable stores time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| end_time | States stored for 15 minutes time interval. This variable stores time of the time interval ending. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| states | Array of the states. Structure of the object state described below. |
| device_id | No | Device ids can be retrieved from */sites/:site_id/devices* | | ff65253d71fc4e278d9e89013095c927 |
| object_id | Object ids can be retrieved from */sites/:site_id/control_objects/* | 
| time | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| online | Online object time, store in seconds |
| immobile | Immobile object time, store in seconds. If object not immobile value is 0. |
| assigned_id | Id of car or asset on wich object with object_id assigned for work. Object ids can be retrieved from */sites/:site_id/control_objects*. If object doesn't have assign value is *null* |
| pressed | Boolean indicator to store is button on tracker pressed |
| long_pressed | Boolean indicator to store is button on tracker pressed |
| pos | Position of the object, it stores in geoJSON point format - object with properties *type* and *coordinates* with array longtitude latitude pair |
| alt | Altitude of the object position. Stores in meters |
| angle | Object azimuth, displays moving direction. Stores in degrees |
| speed | Object speed, stores in kilometers per hour |
| quality | Displayes quality of signal from tracker |
| offline | Offline object time, stores in seconds. |
| zone_ids | Array of zone ids. If object position on any zone, zone id stores in *zones* array. Zone ids can be retrieved from */sites/:site_id/zones* |
| group_ids | Array of group ids. If object in any group, group id stores in *group* array. Group ids can be retrieved from */sites/:site_id/object_groups* |

---

# GET /sites/:site_id/object_states/timeline

Returns json data about worksite object states for current timeline. Current timeline is 15 minutes interval, in which included current time.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_states
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |


### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_states
`

### Example response

```
[
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"time": "2017-11-24T15:32:24.016Z",
	"device_id": "053a18a5a24a47d4b14392b75de4e0ea",
	"object_id": "4eef83ee351740699ce79639a4ae92a8",
	"assign_id": null,
	"pos": {
		"type": "Point",
		"coordinates": [
		30.682727694511414,
		64.68182288242792
		],
	},
	"alt": 200,
	"speed": 0,
	"quality": 2,
	"angle": 315,
	"online": 1236765.858000055,
	"immobile": 1821.7149999999992,
	"pressed": null,
	"long_pressed": null,
	"zone_ids": [
	"0ad7195fef7d4c64a8137f0d577460d6"
	],
	"group_ids": [],
},
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"time": "2017-11-24T15:32:24.041Z",
	"device_id": "423a9863a94d42e593f912269d9c31a5",
	"object_id": "1bab7b4b9109441e8ad6a9d58bf8ee29",
	"assign_id": null,
	"pos": {
		"type": "Point",
		"coordinates": [
		30.662037134170532,
		64.6611592517049
		],
	},
	"alt": 200,
	"speed": 0,
	"quality": 2,
	"angle": 45,
	"online": 1236765.8230001123,
	"immobile": 1175.2250000000006,
	"pressed": null,
	"long_pressed": null,
	"zone_ids": [
	"7fa504f7b9034d979c27697f0520fdde",
	"ae5a413ec4d04782bfeee2bfa0af07ff"
	],
	"group_ids": [
	"896ba1e245a248ccb52aaae57d522374"
	],
},
...
]
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Site id. These IDs can be retrieved from */sites.*|
| start_time | States stored for 15 minutes time interval. This variable stores time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| end_time | States stored for 15 minutes time interval. This variable stores time of the time interval ending. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| states | Array of the states. Structure of the object state described below. |
| device_id | No | Device ids can be retrieved from */sites/:site_id/devices* | | ff65253d71fc4e278d9e89013095c927 |
| object_id | Object ids can be retrieved from */sites/:site_id/control_objects/* | 
| time | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| online | Online object time, store in seconds |
| immobile | Immobile object time, store in seconds. If object not immobile value is 0. |
| assigned_id | Id of car or asset on wich object with object_id assigned for work. Object ids can be retrieved from */sites/:site_id/control_objects*. If object doesn't have assign value is *null* |
| pressed | Boolean indicator to store is button on tracker pressed |
| long_pressed | Boolean indicator to store is button on tracker pressed |
| pos | Position of the object, it stores in geoJSON point format - object with properties *type* and *coordinates* with array longtitude latitude pair |
| alt | Altitude of the object position. Stores in meters |
| angle | Object azimuth, displays moving direction. Stores in degrees |
| speed | Object speed, stores in kilometers per hour |
| quality | Displayes quality of signal from tracker |
| offline | Offline object time, stores in seconds. |
| zone_ids | Array of zone ids. If object position on any zone, zone id stores in *zones* array. Zone ids can be retrieved from */sites/:site_id/zones* |
| group_ids | Array of group ids. If object in any group, group id stores in *group* array. Group ids can be retrieved from */sites/:site_id/object_groups* |

---

# POST /sites/:site_id/object_states

Create new object state from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_states
`

### Request Information

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
| start_time | Yes | States stored for 15 minutes time interval. This variable stores time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:00:00.000Z |
| end_time | Yes | States stored for 15 minutes time interval. This variable stores time of the time interval ending. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:15:00.000Z |
| states | Yes | Array of the states. Structure of the object state described below. | | see example body below |
| device_id | Yes | No | Device ids can be retrieved from */sites/:site_id/devices* | | ff65253d71fc4e278d9e89013095c927 |
| object_id | Yes | No | Object ids can be retrieved from */sites/:site_id/control_objects/* | | e17172ad05d448d18450aca6f6fff653 |
| time | Yes | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T13:13:53.263Z | 
| online | Yes | Online object time, store in seconds | | 95656.4545 |
| immobile | Yes | Immobile object time, store in seconds. If object not immobile value is 0. | | 95656.4545 |
| assigned_id | Yes | Id of car or asset on wich object with object_id assigned for work. Object ids can be retrieved from */sites/:site_id/control_objects*. If object doesn't have assign value is *null* | | null, e892a72d6a2b4ca8899efb44a860f7d0 |
| pressed | Yes | Boolean indicator to store is button on tracker pressed | | null, true, false |
| long_pressed | Yes | Boolean indicator to store is button on tracker pressed | | null, true, false |
| pos | Yes | Position of the object, it stores in geoJSON point format - object with properties *type* and *coordinates* with array longtitude latitude pair.  | | { "type": "Point", "coordinates": [ 30.694127082824707, 64.69424468980802 ], } |
| alt | Yes | Altitude of the object position. Stores in meters | | 200 |
| angle | Yes | Object azimuth, displays moving direction. Stores in degrees | | 45 |
| speed | Yes | Object speed, stores in kilometers per hour | | 50 |
| quality | Yes | Displayes quality of signal from tracker | | 2 |
| offline | Yes | Offline object time, stores in seconds. | | 0 |
| zone_ids | Yes | Array of zone ids. If object position on any zone, zone id stores in *zones* array. Zone ids can be retrieved from */sites/:site_id/zones* | | [ "561154dd93154c9eb307d1f0569a67db" ] |
| group_ids | Yes | Array of group ids. If object in any group, group id stores in *group* array. Group ids can be retrieved from */sites/:site_id/object_groups* | | [ "ff65253d71fc4e278d9e89013095c927" ] |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_states
`

### Example Body

```
{
	"end_time": "2017-11-22T14:00:00.000Z",
	"site_id": "9958f0dd1faa494fbc48ba816a02fdd0",
	"start_time": "2017-11-22T13:45:00.000Z",
	"states": [
	{
		"site_id": "9958f0dd1faa494fbc48ba816a02fdd0",
		"time": "2017-11-22T14:00:19.052Z",
		"device_id": "08895262776344bfa33a60d201e9b29b",
		"object_id": "63b464dfdc084635856a52c557f9215e",
		"assign_id": null,
		"pos": {
			"coordinates": [
			37.640559,
			51.299172
			],
			"type": "Point"
		},
		"alt": 200,
		"speed": 10,
		"quality": 0,
		"angle": 45,
		"online": 274.592,
		"immobile": 0,
		"pressed": null,
		"long_pressed": null,
		"zone_ids": [
		"19d724c6f81a4053b7e442367a11fbd7"
		],
		"group_ids": []
	}
	]
}
```

### Example response

```
No content
```

---

# POST /sites/:site_id/object_states/batch

Batch insert for object states from json string for specified site. Create multple object states at one request for sended array of object states.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_states/batch
`

### Request Information

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
| start_time | Yes | States stored for 15 minutes time interval. This variable stores time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:00:00.000Z |
| end_time | Yes | States stored for 15 minutes time interval. This variable stores time of the time interval ending. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:15:00.000Z |
| states | Yes | Array of the states. Structure of the object state described below. | | see example body below |
| site_id | No | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| device_id | No | Device ids can be retrieved from */sites/:site_id/devices* | | ff65253d71fc4e278d9e89013095c927 |
| object_id | No | Object ids can be retrieved from */sites/:site_id/control_objects/* | | e17172ad05d448d18450aca6f6fff653 |
| time | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T13:13:53.263Z | 
| online | Online object time, store in seconds | | 95656.4545 |
| immobile | Immobile object time, store in seconds. If object not immobile value is 0. | | 95656.4545 |
| assigned_id | Id of car or asset on wich object with object_id assigned for work. Object ids can be retrieved from */sites/:site_id/control_objects*. If object doesn't have assign value is *null* | | null, e892a72d6a2b4ca8899efb44a860f7d0 |
| pressed | Boolean indicator to store is button on tracker pressed | | null, true, false |
| long_pressed | Boolean indicator to store is button on tracker pressed | | null, true, false |
| pos | No | Position of the object, it stores in geoJSON point format - object with properties *type* and *coordinates* with array longtitude latitude pair.  | | { "type": "Point", "coordinates": [ 30.694127082824707, 64.69424468980802 ], } |
| alt | No | Altitude of the object position. Stores in meters | | 200 |
| angle | No | Object azimuth, displays moving direction. Stores in degrees | | 45 |
| speed | No | Object speed, stores in kilometers per hour | | 50 |
| quality | No | Displayes quality of signal from tracker | | 2 |
| offline | No | Offline object time, stores in seconds. | | 0 |
| zone_ids | Array of zone ids. If object position on any zone, zone id stores in *zones* array. Zone ids can be retrieved from */sites/:site_id/zones* | | [ "561154dd93154c9eb307d1f0569a67db" ] |
| group_ids | Array of group ids. If object in any group, group id stores in *group* array. Group ids can be retrieved from */sites/:site_id/object_groups* | | [ "ff65253d71fc4e278d9e89013095c927" ] |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_states/batch
`

### Example Body

```
[
{
	"end_time": "2017-11-22T14:00:00.000Z",
	"site_id": "9958f0dd1faa494fbc48ba816a02fdd0",
	"start_time": "2017-11-22T13:45:00.000Z",
	"states": [
	{
		"site_id": "9958f0dd1faa494fbc48ba816a02fdd0",
		"time": "2017-11-22T14:00:19.052Z",
		"device_id": "08895262776344bfa33a60d201e9b29b",
		"object_id": "63b464dfdc084635856a52c557f9215e",
		"assign_id": null,
		"pos": {
			"coordinates": [
			37.640559,
			51.299172
			],
			"type": "Point"
		},
		"alt": 200,
		"speed": 10,
		"quality": 0,
		"angle": 45,
		"online": 274.592,
		"immobile": 0,
		"pressed": null,
		"long_pressed": null,
		"zone_ids": [
		"19d724c6f81a4053b7e442367a11fbd7"
		],
		"group_ids": []
	}
	]
},
{
	"end_time": "2017-11-22T14:15:00.000Z",
	"site_id": "9958f0dd1faa494fbc48ba816a02fdd0",
	"start_time": "2017-11-22T14:00:00.000Z",
	"states": [
	{
		"site_id": "9958f0dd1faa494fbc48ba816a02fdd0",
		"time": "2017-11-22T14:00:19.052Z",
		"device_id": "08895262776344bfa33a60d201e9b29b",
		"object_id": "63b464dfdc084635856a52c557f9215e",
		"assign_id": null,
		"pos": {
			"coordinates": [
			37.640559,
			51.299172
			],
			"type": "Point"
		},
		"alt": 200,
		"speed": 10,
		"quality": 0,
		"angle": 45,
		"online": 274.592,
		"immobile": 0,
		"pressed": null,
		"long_pressed": null,
		"zone_ids": [
		"19d724c6f81a4053b7e442367a11fbd7"
		],
		"group_ids": []
	}
	]
}
]
```

### Example response

```
No content
```

---

# DELETE /sites/:site_id/object_states

Delete all object states on specified worksite.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_states
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_states
`

### Example response

```
No content
```