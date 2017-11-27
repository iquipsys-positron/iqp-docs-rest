Page navigation

* [Get worksite shifts](#shifts)
* [Get shift info](#shift)
* [Create shift](#new-shift)
* [Update shift](#edit-shift)
* [Delete shift](#delete-shift)

---

# <a name="shifts">GET /sites/:site_id/shifts</a>

Returns json array with data about all shifts on specified site.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/shifts
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
| site_id | Yes | Shift site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/shifts
`

### Example response

```
{
	"total": 3,
	"data": [
	{
		"duration": -960,
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"name": "Third shift",
		"start": 1380,
		"id": "3a647c771c664486b981533520dfa2e3"
	},
	{
		"duration": 480,
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"name": "First shift",
		"start": 420,
		"id": "d5da284f89c74bc2adea6adb4b799ab0"
	},
	{
		"duration": 480,
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"name": "Second shift",
		"start": 900,
		"id": "4169f50cea904a43b46db8c41f0283d9"
	}
	],
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| duration | Shift duration in munutes from shift start |
| site_id |  Shift site id. These IDs can be retrieved from */sites.* |
| name | Name of the shift |
| start | Shift start time in minutes from 00:00. For example 8:00 equals 480 |
| id | Inuque identifier of the shift |

---

# <a name="shift">GET /sites/:site_id/shifts/:shift_id</a>

Returns json data about one or all shifts on specified site. If you don't set *shift_id* result will contain all site shifts. To get info only about one shift you should set *shift_id* in request url.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/shifts/:shift_id
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
| site_id | Yes | Shift site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| shift_id | No | shift ids can be retrieved from */sites/:site_id/shifts/* Set shift id to get data for one shift. | | 4169f50cea904a43b46db8c41f0283d9 |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/shifts/4169f50cea904a43b46db8c41f0283d9
`

### Example response

```
{
	"duration": 480,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "Second shift",
	"start": 900,
	"id": "4169f50cea904a43b46db8c41f0283d9"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| duration | Shift duration in munutes from shift start |
| site_id |  Shift site id. These IDs can be retrieved from */sites.* |
| name | Name of the shift |
| start | Shift start time in minutes from 00:00. For example 8:00 equals 480 |
| id | Inuque identifier of the shift |

---

# <a name="new-shift">POST /sites/:site_id/shifts</a>

Create new shift from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/shifts
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
| site_id | Yes | Shift site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the shift | | First shift |
| start | Yes | Shift start time in minutes from 00:00. For example 8:00 equals 480 | | 480 |
| duration | Yes | Shift duration in munutes from shift start | | 480 |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Shift site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/shifts
`

### Example Body

```
{
	"duration": 480,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "New shift",
	"start": 900
}
```

### Example response

```
{
	"duration": 480,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "New shift",
	"start": 900,
	"id": "de9084d0994d4483a78213de0753baa4"
}
```

### Response explanation

The result is json data of the new created object.

---

# <a name="edit-shift">PUT /sites/:site_id/shifts/:shift_id</a>

Edit existing shift.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/shifts/:shift_id
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
| site_id | No | Shift site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the shift | | First shift |
| start | Yes | Shift start time in minutes from 00:00. For example 8:00 equals 480 | | 480 |
| duration | Yes | Shift duration in munutes from shift start | | 480 |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Shift site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| shift_id | No | shift ids can be retrieved from */sites/:site_id/shifts/* | | de9084d0994d4483a78213de0753baa4 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/shifts/de9084d0994d4483a78213de0753baa4
`

### Example Body

```
{
    "name": "New shift1",
    "start": 930
}
```

### Example response

```
{
	"duration": 480,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "New shift1",
	"start": 930,
	"id": "de9084d0994d4483a78213de0753baa4"
}
```

### Response explanation

The result is json data of the edited object.

---

# <a name="delete-shift">DELETE /sites/:site_id/shifts/:shift_id</a>

Deletes existing shift.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/shifts/:shift_id
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
| site_id | Yes | Shift site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| shift_id | No | shift ids can be retrieved from */sites/:site_id/shifts/* | | de9084d0994d4483a78213de0753baa4 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/shifts/de9084d0994d4483a78213de0753baa4
`

### Example response

```
{
	"duration": 480,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "New shift1",
	"start": 930,
	"deleted": true,
	"id": "de9084d0994d4483a78213de0753baa4"
}
```

### Response explanation

The result is json data of the deleted object.