Page navigation

* [Update state](#update-state)
* [Invalidate state](#invalidate-state)

---

# <a name="update-state">POST /sites/:site_id/begin_update_state</a>

Initiate update of the current state, calculates all rules, generates events and logs historical records

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/begin_update_state
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
| device_id | Yes | Device id can be retrieved from */sites/:site_id/devices.* | | e0a31d48021e492c8c7d45b17ac36175 |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | invalidate_state site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/begin_update_state
`

### Example Body

```
{
	"device_id":"e0a31d48021e492c8c7d45b17ac36175"
}
```

### Example response

```
204 No content
```

### Response explanation

On successfull request execution result is 204.

---

# <a name="invalidate-state">POST /sites/:site_id/invalidate_states</a>

Invalidate device state on specified site. 

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/invalidate_states
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
| device_id | Yes | Device id can be retrieved from */sites/:site_id/devices.* | | e0a31d48021e492c8c7d45b17ac36175 |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | invalidate_state site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invalidate_states
`

### Example Body

```
{
	"device_id":"e0a31d48021e492c8c7d45b17ac36175"
}
```

### Example response

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"device_id": "e0a31d48021e492c8c7d45b17ac36175",
	"object_id": "60256da4ba014328ade33005b4687736",
	"time": "2017-11-28T12:45:15.768Z",
	"online": 0,
	"immobile": 0,
	"assign_id": null,
	"pressed": false,
	"long_pressed": false,
	"pos_time": "2017-11-28T12:45:11.751Z",
	"state_time": "2017-11-28T12:44:54.352Z",
	"pos": {
		"type": "Point",
		"coordinates": [
		"30.674168",
		"64.674468"
		],
	},
	"alt": 200,
	"angle": 0,
	"speed": 0,
	"quality": 2,
	"rules": [],
	"attend_time": "2017-11-10T07:59:26.623Z",
	"expected": true,
	"connected": false,
	"offline": 0,
	"rule_time": null,
	"attend_start": "2017-11-28T00:00:00.000Z",
	"assign_time": null,
	"assign_proc": true,
	"zones": [
	{
		"exited": false,
		"entered": false,
		"duration": 1572346.5690000479,
		"zone_id": "9372a17a191345a694e8d2a184a43a2c"
	},
	{
		"exited": false,
		"entered": false,
		"duration": 1112616.0830000106,
		"zone_id": "925b6c972b274baba4e45233c653e19d"
	}
	],
	"group_ids": [
	"5cc46f1f9705494d8184eab112ce2980"
	],
	"id": "e0a31d48021e492c8c7d45b17ac36175"
}
```

### Response explanation

The result is json data of the state.

| Name | Description | 
|------|----------|
| site_id | Current object state site id. These IDs can be retrieved from */sites.* |
| device_id | Device ids can be retrieved from */sites/:site_id/devices* |
| object_id | Object ids can be retrieved from */sites/:site_id/control_objects/* |
| time | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| online | Online object time, store in seconds |
| immobile | Immobile object time, store in seconds. If object not immobile value is 0. |
| assigned_id | Id of car or asset on wich object with object_id assigned for work. Object ids can be retrieved from */sites/:site_id/control_objects*. If object doesn't have assign value is *null* |
| pressed | Boolean indicator to store is button on tracker pressed |
| long_pressed | Boolean indicator to store is button on tracker pressed |
| pos_time | Object position time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| state_time | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| rules | Activated rules for object state. If rule is triggered it stores in *rules* array. Rule ids can be retrieved from */sites/:site_id/rules* |
| pos | Position of the object, it stores in geoJSON point format - object with properties *type* and *coordinates* with array longtitude latitude pair | 
| alt | Altitude of the object position. Stores in meters |
| angle | Object azimuth, displays moving direction. Stores in degrees |
| speed | Object speed, stores in kilometers per hour |
| quality | Displayes quality of signal from tracker |
| offline | Offline object time, stores in seconds |
| excpected | Boolean variable to store is an object expected on shift |
| rule_time | Time when rule was triggered. Can be null. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| attend_start | Time of the attendance start. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| assign_time | Time of the assignment. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| assign_proc | Boolean flag for assign processing. When people have assign to some equipment or asset. |
| zones | Array of zone ids. If object position on any zone, zone id stores in *zones* array. Zone ids can be retrieved from */sites/:site_id/zones* |
| group_ids | Array of group ids. If object in any group, group id stores in *group* array. Group ids can be retrieved from */sites/:site_id/object_groups* |
| id | Inuque identifier of the current object state |