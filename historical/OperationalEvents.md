Page navigation

* [Get worksite operational events](#operational-events)
* [Create operational event](#new-operational-event)
* [Delete operational event](#delete-operational-event)

---

# <a name="operational-events">GET /sites/:site_id/operational_events</a>

Returns json data about all worksite operational events.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/operational_events
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
| site_id | Yes | Operational event site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/operational_events
`

### Example response

```
{
	"total": 66185,
	"data": [
	{
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"create_time": "2017-11-23T11:06:56.355Z",
		"creator_id": null,
		"type": "auto",
		"rule_id": "9f1ae9e227e14a8a9548a3c581816a08",
		"severity": 0,
		"time": "2017-11-23T11:06:56.336Z",
		"pos": {
			"type": "Point",
			"coordinates": [
			30.665888786315918,
			64.69739510699493
			],
		},
		"object_id": "45c29d02316e4320a036edd931f26673",
		"assign_id": null,
		"zone_id": "338c32dee6a04c468a479330ad1d7acf",
		"description": "Work zone exit",
		"expected_value": null,
		"actual_value": null,
		"value_units": null,
		"id": "8b0e8f7cf65348fd993b2d48af1b5e2b"
	},
	{
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"create_time": "2017-11-23T11:06:51.419Z",
		"creator_id": null,
		"type": "auto",
		"rule_id": "926c5041121a4e688cda52978d1c0782",
		"severity": 0,
		"time": "2017-11-23T11:06:51.403Z",
		"pos": {
			"type": "Point",
			"coordinates": [
			30.665888786315918,
			64.69739510699493
			],
		},
		"object_id": "45c29d02316e4320a036edd931f26673",
		"assign_id": null,
		"zone_id": "338c32dee6a04c468a479330ad1d7acf",
		"description": "Work zone Entry",
		"expected_value": null,
		"actual_value": null,
		"value_units": null,
		"id": "0f8b518ed8fa4ba1bccae92e58934f2f"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Operational event site id. These IDs can be retrieved from */sites.* |
| create_time |  Time of the event creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| creator_id | If operational event created manualy by manager or administrator this variable stores creator id. Account ids can be retrieved from */accounts*. If operational event created automaticaly by system value is *null* |
| type | Type of the opartional event displays the way it was created - manualy by site manager or admin or automaticaly by system when rule is triggered. Can take values *manual*, *auto* |
| rule_id | Defines what rule was triggered for this operational event. Rule ids can be retrieved from */sites/:site_id/rules/* |
| severity | Severity of the rulre, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. |
| time | Time of the event creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| pos | Position of the event. It stores in geoJSON point format - object with property *coordinates* with array longtitude latitude pair. |
| object_id | Object related to event. Object ids can be retrieved from */sites/:site_id/control_objects/* |
| assign_id | Equipment or asset id assigned to object. If object doesn't have assign value is null. These ids can be retrieved from */sites/:site_id/control_objects/* |
| zone_id | Zone where an event happens. Zone ids can be retrieved from */sites/:site_id/zones/* |
| description | The event name |
| expected_value | Parameter value from rule. For example rule is immobility for 15 mins - value will be 15. If not setted can be *null* |
| actual_value | Actual parameter value. If not setted can be *null* |
| value_units | Units of the parameter value. If not setted can be *null* |
| id | Inuque identifier of the operational event |

---

# <a name="new-operational-event">POST /sites/:site_id/operational_events</a>

Create new operational event from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/operational_events
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
| site_id | Yes | Operational event site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| creator_id | No | If operational event created manualy by manager or administrator this variable stores creator id. Account ids can be retrieved from */accounts*. If operational event created automaticaly by system value is *null* | null | null, e17172ad05d448d18450aca6f6fff653 |
| type | Yes | Type of the opartional event displays the way it was created - manualy by site manager or admin or automaticaly by system when rule is triggered | | auto, manual |
| rule_id | No | Defines what rule was triggered for this operational event. Rule ids can be retrieved from */sites/:site_id/rules/* | | c71278120b9c4e2a8773e1c09503e532 |
| severity | Yes | Severity of the rulre, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. | | 0, 50, 100 |
| time | No | Time of the event creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:13:00.000Z |
| pos | No | Position of the event. It stores in geoJSON point format - object with property *coordinates* with array longtitude latitude pair.  | | { "coordinates": [ 30.646963119506836, 64.68692440226665 ] } |
| object_id | Yes | Object related to event. Object ids can be retrieved from */sites/:site_id/control_objects/* | | e17172ad05d448d18450aca6f6fff653 |
| assign_id | No | Equipment or asset id assigned to object. If object doesn't have assign value is null. These ids can be retrieved from */sites/:site_id/control_objects/* | | null, e17172ad05d448d18450aca6f6fff653 |
| zone_id | No | Zone where an event happens. Zone ids can be retrieved from */sites/:site_id/zones/* | | 9f88b6307a3645f597bc4e48f7758ee1 |
| description | Yes | The event name | | Work zone entry |
| expected_value | No | Parameter value from rule. For example rule is immobility for 15 mins - value will be 15. If not setted can be *null*. | | 15 |
| actual_value | No | Actual parameter value. If not setted can be *null*. | | 15.01 |
| value_units | No | Units of the parameter value. If not setted can be *null*. | | min | 

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/operational_events
`

### Example Body

```
{		
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"creator_id": null,
	"type": "auto",
	"rule_id": "926c5041121a4e688cda52978d1c0782",
	"severity": 0,
	"time": "2017-11-23T11:06:51.403Z",
	"pos": {
		"type": "Point",
		"coordinates": [
		30.665888786315918,
		64.69739510699493
		]
	},
	"object_id": "45c29d02316e4320a036edd931f26673",
	"assign_id": null,
	"zone_id": "338c32dee6a04c468a479330ad1d7acf",
	"description": "Work zone Entry",
	"expected_value": null,
	"actual_value": null,
	"value_units": null
}
```

### Example response

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"creator_id": "cd65c2023be34e84b2e9529264d17d21",
	"type": "auto",
	"rule_id": "926c5041121a4e688cda52978d1c0782",
	"severity": 0,
	"time": "2017-11-23T11:06:51.403Z",
	"pos": {
		"coordinates": [
		30.665888786315918,
		64.69739510699493
		],
		"type": "Point"
	},
	"object_id": "45c29d02316e4320a036edd931f26673",
	"assign_id": null,
	"zone_id": "338c32dee6a04c468a479330ad1d7acf",
	"description": "Work zone Entry",
	"expected_value": null,
	"actual_value": null,
	"value_units": null,
	"create_time": "2017-11-23T11:21:01.989Z",
	"id": "5b99a941c17e4b63acda0bb083a4ad09"
}
```

### Response explanation

The result is json data of the new created event.

---

# <a name="delete-operational-event">DELETE /sites/:site_id/operational_events/:event_id</a>

Delete all existing current operational event by state id. As result return all deleted states.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/operational_events/:event_id
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
| site_id | Yes | Operational event site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| event_it | No | incident ids can be retrieved from */sites/:site_id/operational_events* | | 5b99a941c17e4b63acda0bb083a4ad09 |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/operational_events/5b99a941c17e4b63acda0bb083a4ad09
`

### Example response

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"creator_id": "cd65c2023be34e84b2e9529264d17d21",
	"type": "auto",
	"rule_id": "926c5041121a4e688cda52978d1c0782",
	"severity": 0,
	"time": "2017-11-23T11:06:51.403Z",
	"pos": {
		"type": "Point",
		"coordinates": [
		30.665888786315918,
		64.69739510699493
		],
	},
	"object_id": "45c29d02316e4320a036edd931f26673",
	"assign_id": null,
	"zone_id": "338c32dee6a04c468a479330ad1d7acf",
	"description": "Work zone Entry",
	"expected_value": null,
	"actual_value": null,
	"value_units": null,
	"create_time": "2017-11-23T11:21:01.989Z",
	"id": "5b99a941c17e4b63acda0bb083a4ad09"
}
```

### Response explanation

The result is json data of the deleted event.