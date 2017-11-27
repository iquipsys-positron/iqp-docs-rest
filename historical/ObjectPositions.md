Page navigation

* [Get worksite object positions](#object-positions)
* [Get worksite object positions count](#object-position-count)
* [Create object positions](#new-object-position)
* [Create multiple object positions](#new-object-positions)
* [Delete object position](#delete-object-position)

---

# <a name="object-positions">GET /sites/:site_id/object_positions</a>

Returns json data about worksite all object positions.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_positions
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
| site_id | Yes | Object positions site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_positions
`

### Example response

```
{
	"total": 111035,
	"data": [
	{
		"object_id": "0fbeda21195e46fbbc24f8e5a9bd739f",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"count": 39,
		"end_time": "2017-11-23T12:00:00.000Z",
		"last_time": "2017-11-23T11:45:03.615Z",
		"positions": [
		{
			"time": "2017-11-23T11:30:00.910Z",
			"lat": 64.67409168760565,
			"long": 30.674013118298895,
			"spd": 5,
			"agl": 315
		},
		{
			"time": "2017-11-23T11:30:06.213Z",
			"lat": 64.6741183182948,
			"long": 30.673978328704834,
			"spd": 5,
			"agl": 315
		},
		{
			"time": "2017-11-23T11:30:13.394Z",
			"lat": 64.67413136605576,
			"long": 30.67391514574163,
			"spd": 6,
			"agl": 315
		},
		...
		],
		"id": "1cff399ac9fd44b185f3b5dbb914335c"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| object_id | Object related with position. Object ids can be retrieved from */sites/:site_id/control_objects/* |
| site_id | Object positions site id. These IDs can be retrieved from */sites.* |
| count | Count of the position for corrent record, in other words this variable stores *positions* array count |
| end_time | Postitions stored for 15 minutes time interval. This variable stores time of the time interval ending. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| last_time | Postitions stored for 15 minutes time interval. This variable stores time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| positions |  Array of the objects with following structure: *time* - position time, *lat* - position latitude, *long* - position longtitude, *spd* - speed of the object in this position, *agl* - azimuth of the object in this position, stores as integer number, displays object direction  |
| id | Inuque identifier of the object position |

---

# <a name="object-position-count">GET /sites/:site_id/object_positions/count</a>

Returns count of all object_positions on worksite.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_positions/count
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
| site_id | Yes | Object positions site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_positions/count
`

### Example response

```
328756
```

### Response explanation

The result quantity of worksite object positions.

---

# <a name="new-object-position">POST /sites/:site_id/object_positions</a>

Create new object position from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_positions
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
| site_id | Yes | Object positions site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| object_id | Yes | Object related with position. Object ids can be retrieved from */sites/:site_id/control_objects/* | | e17172ad05d448d18450aca6f6fff653 |
| count | Yes | Count of the position for corrent record, in other words this variable stores *positions* array count | | 3 |
| last_time | Yes | Postitions stored for 15 minutes time interval. This variable stores time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:00:00.000Z |
| end_time | Yes | Postitions stored for 15 minutes time interval. This variable stores time of the time interval ending. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:15:00.000Z |
| positions | Yes | Array of the objects with following structure: *time* - position time, *lat* - position latitude, *long* - position longtitude, *spd* - speed of the object in this position, *agl* - azimuth of the object in this position, stores as integer number, displays object direction | | [{ "time": "2017-11-23T11:30:00.910Z", "lat": 64.67409168760565, "long": 30.674013118298895, "spd": 5, "agl": 315 }] |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_positions
`

### Example Body

```
{
	"object_id": "0fbeda21195e46fbbc24f8e5a9bd739f",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"count": 3,
	"end_time": "2017-11-23T12:00:00.000Z",
	"last_time": "2017-11-23T11:45:03.615Z",
	"positions": [
	{
		"time": "2017-11-23T11:30:00.910Z",
		"lat": 64.67409168760565,
		"long": 30.674013118298895,
		"spd": 5,
		"agl": 315
	},
	{
		"time": "2017-11-23T11:30:06.213Z",
		"lat": 64.6741183182948,
		"long": 30.673978328704834,
		"spd": 5,
		"agl": 315
	},
	{
		"time": "2017-11-23T11:30:13.394Z",
		"lat": 64.67413136605576,
		"long": 30.67391514574163,
		"spd": 6,
		"agl": 315
	}
	]
}
```

### Example response

```
No content
```

---

# <a name="new-object-positions">POST /sites/:site_id/object_positions/batch</a>

Batch insert for object positions from json string for specified site. Create multple object positions at one request for sended array of object positions.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_positions/batch
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
| site_id | Yes | Object positions site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| object_id | Yes | Object related with position. Object ids can be retrieved from */sites/:site_id/control_objects/* | | e17172ad05d448d18450aca6f6fff653 |
| count | Yes | Count of the position for corrent record, in other words this variable stores *positions* array count | | 3 |
| last_time | Yes | Postitions stored for 15 minutes time inetrval. This variable stores time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:00:00.000Z |
| end_time | Yes | Postitions stored for 15 minutes time inetrval. This variable stores time of the time interval ending. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:15:00.000Z |
| positions | Yes | Array of the objects with following structure: *time* - position time, *lat* - position latitude, *long* - position longtitude, *spd* - speed of the object in this position, *agl* - azimuth of the object in this position, stores as integer number, displays object direction | | [{ "time": "2017-11-23T11:30:00.910Z", "lat": 64.67409168760565, "long": 30.674013118298895, "spd": 5, "agl": 315 }] |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_positions/batch
`

### Example Body

```
[
	{
		"object_id": "0fbeda21195e46fbbc24f8e5a9bd739f",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"count": 3,
		"end_time": "2017-11-23T12:00:00.000Z",
		"last_time": "2017-11-23T11:45:03.615Z",
		"positions": [
		{
			"time": "2017-11-23T11:30:00.910Z",
			"lat": 64.67409168760565,
			"long": 30.674013118298895,
			"spd": 5,
			"agl": 315
		},
		{
			"time": "2017-11-23T11:30:06.213Z",
			"lat": 64.6741183182948,
			"long": 30.673978328704834,
			"spd": 5,
			"agl": 315
		},
		{
			"time": "2017-11-23T11:30:13.394Z",
			"lat": 64.67413136605576,
			"long": 30.67391514574163,
			"spd": 6,
			"agl": 315
		}
		]
	},
	{
		"object_id": "0fbeda21195e46fbbc24f8e5a9bd739f",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"count": 2,
		"end_time": "2017-11-23T12:15:00.000Z",
		"last_time": "2017-11-23T12:00:03.698Z",
		"positions": [
		{
			"time": "2017-11-23T12:00:03.698Z",
			"lat": 64.67383799382644,
			"long": 30.6652415356667,
			"spd": 5,
			"agl": 225
		},
		{
			"time": "2017-11-23T12:00:08.749Z",
			"lat": 64.67382549616364,
			"long": 30.665194790404275,
			"spd": 5,
			"agl": 225
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

# <a name="delete-object-position">DELETE /sites/:site_id/object_positions</a>

Delete all object positions on specified worksite.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_positions
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
| site_id | Yes | Object positions site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_positions
`

### Example response

```
No content
```

---