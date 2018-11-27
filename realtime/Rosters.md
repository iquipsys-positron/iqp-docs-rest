Page navigation

* [Get worksite all rosters](#rosters)
* [Get worksite roster](#roster)
* [Create roster](#new-roster)
* [Update rosters](#edit-rosters)
* [Delete roster](#delete-roster)

---

# <a name="rosters">GET /sites/:site_id/rosters</a>

Returns json array with data about all rosters on specified site.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/rosters
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
| site_id | Yes | Roster site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/rosters
`

### Example response

```
{
	"total": 116,
	"data": [
	{
		"end_time": "2017-11-21T21:00:00.000Z",
		"name": "Second shift",
		"shift_id": "4169f50cea904a43b46db8c41f0283d9",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"start_time": "2017-11-21T13:00:00.000Z",
		"objects": [
		{
			"object_id": "dfc175a4d12c47fda8684b7a762e91e0"
		},
		{
			"object_id": "1e4d7d227ca54d49a95b705e764ab4b4"
		},
		{
			"object_id": "36929eb1ee404aaa9de3114033c51386"
		},
		...
		],
		"id": "f0dd9869c9304ec9a4966ee7ee051b16"
	},
	{
		"end_time": "2017-11-21T13:00:00.000Z",
		"name": "First shift",
		"shift_id": "d5da284f89c74bc2adea6adb4b799ab0",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"start_time": "2017-11-21T05:00:00.000Z",
		"objects": [
		{
			"object_id": "dfc175a4d12c47fda8684b7a762e91e0"
		},
		{
			"object_id": "1e4d7d227ca54d49a95b705e764ab4b4"
		},
		...
		],
        "id": "6a613241f5a243a588346d1fc0459a41"
    },
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| end_time | Shift end time, if objects added for entire day start_time equals to end day. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| name | Shift name, if objects added for entire day- name can be empty  |
| shift_id | Shift id, if objects added for entire day - shift_id can be empty. Shift ids can be retrieved from */sites/:site_id/shifts* |
| site_id | Roster site id. These IDs can be retrieved from */sites.* |
| start_time | Shift start time, if objects added for entire day start_time equals to start day. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| objects |  Array of objects included in roster. Each array item have object id, which can be retrieved from */sites/:site_id/control_objects/*. Also to array object can be setted *assign_id*, this is object id of equipment or asset assigned to object. |

---

# <a name="roster">GET /sites/:site_id/rosters/:roster_id</a>

Returns json data about one or all roster on specified site. If you don't set *roster_id* result will contain all site rosters. To get info only about one roster you should set *roster_id* in request url.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/rosters/:roster_id
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
| site_id | Yes | Roster site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| roster_id | No | roster ids can be retrieved from */sites/:site_id/rosters* Set roster id to get data for one roster. | | 6a613241f5a243a588346d1fc0459a41 |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/rosters/6a613241f5a243a588346d1fc0459a41
`

### Example response

```
{
	"end_time": "2017-11-21T13:00:00.000Z",
	"name": "First shift",
	"shift_id": "d5da284f89c74bc2adea6adb4b799ab0",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"start_time": "2017-11-21T05:00:00.000Z",
	"objects": [
	{
		"object_id": "dfc175a4d12c47fda8684b7a762e91e0"
	},
	{
		"object_id": "1e4d7d227ca54d49a95b705e764ab4b4"
	},
	...
	],
	"id": "6a613241f5a243a588346d1fc0459a41"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| end_time | Shift end time, if objects added for entire day start_time equals to end day. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| name | Shift name, if objects added for entire day- name can be empty  |
| shift_id | Shift id, if objects added for entire day - shift_id can be empty. Shift ids can be retrieved from */sites/:site_id/shifts* |
| site_id | Roster site id. These IDs can be retrieved from */sites.* |
| start_time | Shift start time, if objects added for entire day start_time equals to start day. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| objects |  Array of objects included in roster. Each array item have object id, which can be retrieved from */sites/:site_id/control_objects/*. Also to array object can be setted *assign_id*, this is object id of equipment or asset assigned to object. |

---

# <a name="new-roster">POST /sites/:site_id/rosters</a>

Creates new roster from json string for specified site. 

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/rosters
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
| site_id | Yes | Roster site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| shift_id | No | Shift id, if objects added for entire day, can be empty. Shift ids can be retrieved from */sites/:site_id/shifts* | | d5da284f89c74bc2adea6adb4b799ab0 |
| name | No | Shift name, if objects added for entire day, can be empty | | First shift |
| start_time | Yes | Shift start time, if objects added for entire day start_time equals to start day. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T13:13:00.000Z | 
| end_time | Yes | Shift end time, if objects added for entire day start_time equals to end day. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:13:00.000Z | 
| objects | Yes | Array of objects included in roster. Each array item have object id, which can be retrieved from */sites/:site_id/control_objects/*. Also to array object can be setted *assign_id*, this is object id of equipment or asset assigned to object. | | [ { "object_id": "dfc175a4d12c47fda8684b7a762e91e0" }, ... ] |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/rosters
`

### Example Body

```
{
	"end_time": "2017-11-21T13:00:00.000Z",
	"name": "First shift",
	"shift_id": "d5da284f89c74bc2adea6adb4b799ab0",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"start_time": "2017-11-21T05:00:00.000Z",
	"objects": [
	{
		"object_id": "dfc175a4d12c47fda8684b7a762e91e0"
	},
	{
		"object_id": "1e4d7d227ca54d49a95b705e764ab4b4"
	}
	]
}
```

### Example response

```
{
	"end_time": "2017-11-21T13:00:00.000Z",
	"name": "First shift",
	"shift_id": "d5da284f89c74bc2adea6adb4b799ab0",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"start_time": "2017-11-21T05:00:00.000Z",
	"objects": [
	{
		"object_id": "dfc175a4d12c47fda8684b7a762e91e0"
	},
	{
		"object_id": "1e4d7d227ca54d49a95b705e764ab4b4"
	}
	],
	"id": "9f8e68b74cc84afd8ff1cd2c70187de8"
}
```

### Response explanation

The result is json data of the new created roster.

---

# <a name="edit-roster">PUT /sites/:site_id/rosters/:roster_id</a>

Edit existing roster.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/rosters/:roster_id
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
| site_id | No | Roster site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| shift_id | No | Shift id, if objects added for entire day, can be empty. Shift ids can be retrieved from */sites/:site_id/shifts* | | d5da284f89c74bc2adea6adb4b799ab0 |
| name | No | Shift name, if objects added for entire day, can be empty | | First shift |
| start_time | Yes | Shift start time, if objects added for entire day start_time equals to start day. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T13:13:00.000Z | 
| end_time | Yes | Shift end time, if objects added for entire day start_time equals to end day. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:13:00.000Z | 
| objects | Yes | Array of objects included in roster. Each array item have object id, which can be retrieved from */sites/:site_id/control_objects/*. Also to array object can be setted *assign_id*, this is object id of equipment or asset assigned to object. | | [ { "object_id": "dfc175a4d12c47fda8684b7a762e91e0" }, ... ] |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Roster site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| roster_id | No | roster ids can be retrieved from */sites/:site_id/rosters* | | 9f8e68b74cc84afd8ff1cd2c70187de8 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
PUT http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/rosters/9f8e68b74cc84afd8ff1cd2c70187de8
`

### Example Body

```
{
	"start_time": "2017-11-21T08:30:00.000Z",
	"objects": [
	{
		"object_id": "dfc175a4d12c47fda8684b7a762e91e0"
	}
	]
}
```

### Example response

```
{
	"end_time": null,
	"name": "First shift",
	"shift_id": "d5da284f89c74bc2adea6adb4b799ab0",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"start_time": "2017-11-21T08:30:00.000Z",
	"objects": [
	{
		"object_id": "dfc175a4d12c47fda8684b7a762e91e0"
	}
	],
	"id": "9f8e68b74cc84afd8ff1cd2c70187de8"
}
```

### Response explanation

The result is json data of the edited roster.
---

# <a name="delete-roster">DELETE /sites/:site_id/rosters/:roster_id</a>

Deletes existing roster.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/rosters/:roster_id
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
| site_id | Yes | Roster site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| roster_id | No | roster ids can be retrieved from */sites/:site_id/rosters* | | 9f8e68b74cc84afd8ff1cd2c70187de8 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 DELETE http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/rosters/9f8e68b74cc84afd8ff1cd2c70187de8
`

### Example response

```
{
	"end_time": null,
	"name": "First shift",
	"shift_id": "d5da284f89c74bc2adea6adb4b799ab0",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"start_time": "2017-11-21T08:30:00.000Z",
	"objects": [
	{
		"object_id": "dfc175a4d12c47fda8684b7a762e91e0"
	}
	],
	"id": "9f8e68b74cc84afd8ff1cd2c70187de8"
}
```

### Response explanation

The result is json data of the deleted roster.