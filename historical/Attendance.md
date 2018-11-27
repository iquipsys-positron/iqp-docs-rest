Page navigation

* [Get worksite attendances](#attendances)
* [Get worksite attendance within time](#attendance-wtime)
* [Create attendance](#new-attendance)
* [Create multiple attendances](#new-attendances)
* [Delete attendance](#delete-attendance)

---

# <a name="attendances">GET /sites/:site_id/attendance</a>

Returns json data about worksite all attendances.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/attendance
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
 GET http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/attendance
`

### Example response

```
{
	"total": 14,
	"data": [
	{
		"end_time": "2017-11-24T00:00:00.000Z",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"start_time": "2017-11-23T00:00:00.000Z",
		"objects": [
		{
			"end_time": "2017-11-22T23:59:59.738Z",
			"start_time": "2017-11-22T00:00:00.000Z",
			"object_id": "43118a2fb2d64ffe8b87c4703e9464e1"
		},
		{
			"end_time": "2017-11-22T23:59:59.963Z",
			"start_time": "2017-11-22T00:00:00.000Z",
			"object_id": "e17172ad05d448d18450aca6f6fff653"
		},
		{
			"end_time": "2017-11-22T23:59:59.939Z",
			"start_time": "2017-11-22T00:00:00.000Z",
			"object_id": "6fb41f9479024da79b9f76a2daba053c"
		},
		...
        ],
		"id": "5a160f85036f69ee0518b110"
	},
	{
		"end_time": "2017-11-23T00:00:00.000Z",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"start_time": "2017-11-22T00:00:00.000Z",
		"objects": [
		...
		]
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Site id. These IDs can be retrieved from */sites.*|
| start_time | Attendances stored in a day interval. This variable stores date time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| end_time|  Attendances stored in a day interval. This variable stores date time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| objects | Array of the objects with following structire: *start_time* - attendance start time, *end_time* - attendance end time, *object_id* - object related with attendance. Object ids can be retrieved from */sites/:site_id/control_objects/* |

---

# <a name="attendance-wtime">GET /sites/:site_id/attendance/within_time</a>

Returns json data about worksite within time attendances.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/attendance/within_time
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
 GET http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/attendance/within_time
`

### Example response

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"start_time": "2017-11-23T13:40:07.438Z",
	"end_time": "2017-11-23T13:40:07.438Z",
	"objects": [],
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| site_id | Site id. These IDs can be retrieved from */sites.*|
| start_time | Attendances stored in a day interval. This variable stores date time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| end_time|  Attendances stored in a day interval. This variable stores date time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| objects | Array of the objects with following structire: *start_time* - attendance start time, *end_time* - attendance end time, *object_id* - object related with attendance. Object ids can be retrieved from */sites/:site_id/control_objects/* |

---

# <a name="new-attendance">POST /sites/:site_id/attendance</a>

Create new attendance from json string for specified site. 

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/attendance
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
| start_time | Yes | Attendances stored in a day interval. This variable stores date time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T00:00:00.000Z |
| end_time | Yes |  Attendances stored in a day interval. This variable stores date time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-22T00:00:00.000Z |
| objects | Yes | Array of the objects with following structire: *start_time* - attendance start time, *end_time* - attendance end time, *object_id* - object related with attendance. Object ids can be retrieved from */sites/:site_id/control_objects/* | | see example body below |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/attendance
`

### Example Body

```
{
	"end_time": "2017-11-24T00:00:00.000Z",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"start_time": "2017-11-23T00:00:00.000Z",
	"objects": [
	{
		"end_time": "2017-11-22T23:59:59.738Z",
		"start_time": "2017-11-22T00:00:00.000Z",
		"object_id": "43118a2fb2d64ffe8b87c4703e9464e1"
	},
	{
		"end_time": "2017-11-22T23:59:59.963Z",
		"start_time": "2017-11-22T00:00:00.000Z",
		"object_id": "e17172ad05d448d18450aca6f6fff653"
	},
	{
		"end_time": "2017-11-22T23:59:59.939Z",
		"start_time": "2017-11-22T00:00:00.000Z",
		"object_id": "6fb41f9479024da79b9f76a2daba053c"
	}
	]
}
```

### Example response

```
No content
```

---

# <a name="new-attendances">POST /sites/:site_id/attendance/batch</a>

Batch insert for attendances from json string for specified site. Create multple attendances at one request for sended array of attendances.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/attendance/batch
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
| start_time | Yes | Attendances stored in a day interval. This variable stores date time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T00:00:00.000Z |
| end_time | Yes |  Attendances stored in a day interval. This variable stores date time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-22T00:00:00.000Z |
| objects | Yes | Array of the objects with following structire: *start_time* - attendance start time, *end_time* - attendance end time, *object_id* - object related with attendance. Object ids can be retrieved from */sites/:site_id/control_objects/* | | see example body below |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/attendance/batch
`

### Example Body

```
[
{
	"end_time": "2017-11-24T00:00:00.000Z",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"start_time": "2017-11-23T00:00:00.000Z",
	"objects": [
	{
		"end_time": "2017-11-22T23:59:59.738Z",
		"start_time": "2017-11-22T00:00:00.000Z",
		"object_id": "43118a2fb2d64ffe8b87c4703e9464e1"
	},
	{
		"end_time": "2017-11-22T23:59:59.963Z",
		"start_time": "2017-11-22T00:00:00.000Z",
		"object_id": "e17172ad05d448d18450aca6f6fff653"
	},
	{
		"end_time": "2017-11-22T23:59:59.939Z",
		"start_time": "2017-11-22T00:00:00.000Z",
		"object_id": "6fb41f9479024da79b9f76a2daba053c"
	}
	]
},

{
	"end_time": "2017-11-23T00:00:00.000Z",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"start_time": "2017-11-22T00:00:00.000Z",
	"objects": [
	{
		"end_time": "2017-11-22T23:59:59.738Z",
		"start_time": "2017-11-22T00:00:00.000Z",
		"object_id": "43118a2fb2d64ffe8b87c4703e9464e1"
	},
	{
		"end_time": "2017-11-22T23:59:59.963Z",
		"start_time": "2017-11-22T00:00:00.000Z",
		"object_id": "e17172ad05d448d18450aca6f6fff653"
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

# <a name="delete-attendance">DELETE /sites/:site_id/attendance</a>

Delete all attendances on specified worksite.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/attendance
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
 DELETE http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/attendance
`

### Example response

```
No content
```

---