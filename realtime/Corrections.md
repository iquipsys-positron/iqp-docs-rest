## Get site corrections

# GET /sites/:site_id/corrections

Returns json array with data about all corrections on specified site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/corrections
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
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/corrections
`

# Example Responce

```
{
	"total": 4,
	"data": [
	{
		"time": "2017-11-13T12:39:31.398Z",
		"object_id": "2ff6d17cec174c0eafc81d6cdad95630",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"status": "requested",
		"create_time": "2017-11-13T12:37:56.936Z",
		"close_time": null,
		"changes": [
		{
			"value": 1990,
			"param_name": "distance"
		},
		{
			"value": 11110,
			"param_name": "online"
		},
		{
			"value": 9999,
			"param_name": "emergency"
		},
		{
			"value": 0,
			"param_name": "immobile"
		},
		{
			"value": 0,
			"rule_id": "29cce008fbba404b8917d22ff4676424"
		},
		{
			"value": 0,
			"rule_id": "0cf6a1ee5d16457b85373b84421fc9b7"
		},
		{
			"value": 0,
			"zone_id": "ae5a413ec4d04782bfeee2bfa0af07ff"
		},
		{
			"value": 0,
			"zone_id": "3634dd77893346d182f4ff2d049b3334"
		}
		],
		"affected_id": [],
		"id": "9ee807608d20408795be1501d08ce4ad"
	},
	{
		"time": "2017-11-13T12:39:07.937Z",
		"object_id": "b2dab7d007c14b20ba56f0353db786bc",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"status": "rejected",
		"create_time": "2017-11-13T12:37:35.640Z",
		"close_time": null,
		"changes": [
		{
			"value": 100,
			"param_name": "immobile"
		}
		],
		"affected_id": [],
		"id": "74e99f9a2b224c9a9c0f8303150bed19"
	},
	...
}
```

---

## Get correction info

# GET /sites/:site_id/corrections/:correction_id

Returns json data about one or all correction on specified site. If you don't set *correction_id* result will contain all site corrections. To get info only about one correction you should set *correction_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/corrections/:correction_id
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
| correction_id | No | correction ids can be retrieved from */sites/:site_id/corrections* Set correction id to get data for one correction. | | 74e99f9a2b224c9a9c0f8303150bed19 |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/corrections/74e99f9a2b224c9a9c0f8303150bed19
`

# Example Responce

```
{
	"time": "2017-11-13T12:39:07.937Z",
	"object_id": "b2dab7d007c14b20ba56f0353db786bc",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"status": "rejected",
	"create_time": "2017-11-13T12:37:35.640Z",
	"close_time": null,
	"changes": [
	{
		"value": 100,
		"param_name": "immobile"
	}
	],
	"affected_id": [],
	"id": "74e99f9a2b224c9a9c0f8303150bed19"
}
```

---

## Create correction

# POST /sites/:site_id/corrections

Creates new correction from json string for specified site. 

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/corrections
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
| time | Yes | Time of the creation manual correction Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:13:00.000Z | 
| object_id | Yes | Id of the related with correction object. Object ids can be retrieved from */sites/:site_id/control_objects/* | | e17172ad05d448d18450aca6f6fff653 |
| status | Yes | Status of the manual correction can take three values - *requested* for new corrections, *rejected*  for rejected correction and *approved* for approved corrections. | | requested |
| changes | Yes | Array of objects with fields *value* and *param_name*. *param_name* can take next values: *distance*, *online*, *emergency*, *immobile*. If changes related to rule or zone instead of *param_name* there is prorety *rule_id* or *zone_id*. | | { "value": 60, "param_name": "online" } |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/corrections
`

# Example Body

```
{
	"time": "2017-11-21T12:39:07.937Z",
	"object_id": "b2dab7d007c14b20ba56f0353db786bc",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"status": "requested",
	"changes": [
	{
		"value": 60,
		"param_name": "online"
	}
	]
}
```

# Example Responce

```
{
	"time": "2017-11-21T12:39:07.937Z",
	"object_id": "b2dab7d007c14b20ba56f0353db786bc",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"status": "requested",
	"create_time": "2017-11-21T16:54:30.679Z",
	"close_time": null,
	"changes": [
	{
		"value": 60,
		"param_name": "online"
	}
	],
	"affected_id": [],
	"id": "a3a6c6c4339045689ebd6fac9bc4cea1"
}
```

---

## Edit correction

# PUT /sites/:site_id/corrections/:correction_id

Edit existing correction.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/corrections/:correction_id
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
| time | Yes | Time of the creation manual correction Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:13:00.000Z | 
| object_id | Yes | Id of the related with correction object. Object ids can be retrieved from */sites/:site_id/control_objects/* | | e17172ad05d448d18450aca6f6fff653 |
| status | Yes | Status of the manual correction can take three values - *requested* for new corrections, *rejected*  for rejected correction and *approved* for approved corrections. | | requested |
| changes | Yes | Array of objects with fields *value* and *param_name*. *param_name* can take next values: *distance*, *online*, *emergency*, *immobile*. If changes related to rule or zone instead of *param_name* there is prorety *rule_id* or *zone_id*. | | { "value": 60, "param_name": "online" } |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| correction_id | No | correction ids can be retrieved from */sites/:site_id/corrections* | | a3a6c6c4339045689ebd6fac9bc4cea1 |

# Example Request

`
PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/corrections/a3a6c6c4339045689ebd6fac9bc4cea1
`

# Example Body

```
{
  	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
    "status": "rejected",
    "changes": [
    {
      "value": 50,
      "param_name": "online"
    }
  ]
}
```

# Example Responce

```
{
	"time": null,
	"object_id": "b2dab7d007c14b20ba56f0353db786bc",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"status": "rejected",
	"create_time": null,
	"close_time": null,
	"changes": [
	{
		"param_name": "online",
		"value": 50
	}
	],
	"affected_id": [],
	"id": "a3a6c6c4339045689ebd6fac9bc4cea1"
}
```

---

## Delete correction

# DELETE /sites/:site_id/corrections/:correction_id

Deletes existing correction.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/corrections/:correction_id
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
| correction_id | No | correction ids can be retrieved from */sites/:site_id/corrections* | | a3a6c6c4339045689ebd6fac9bc4cea1 |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/corrections/a3a6c6c4339045689ebd6fac9bc4cea1
`

# Example Responce

```
{
	"time": null,
	"object_id": "b2dab7d007c14b20ba56f0353db786bc",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"status": "rejected",
	"create_time": null,
	"close_time": null,
	"changes": [
	{
		"param_name": "online",
		"value": 50
	}
	],
	"affected_id": [],
	"id": "a3a6c6c4339045689ebd6fac9bc4cea1"
}
```