Page navigation

* [Get worksite locations](#locations)
* [Get location info](#location)
* [Create location](#new-location)
* [Update location](#edit-location)
* [Delete location](#delete-location)

---

# <a name="locations">GET /sites/:site_id/locations</a>

Returns json array with data about all locations on specified site.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/locations
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
| site_id | Yes | Location site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/locations
`

### Example response

```
{
	"total": 5,
	"data": [
	{
		"name": "Карьер Центральный",
		"pos": {
			"coordinates": [
			30.646963119506836,
			64.68692440226665
			],
		},
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"id": "1af7eb3146074daf8de07681a424104b"
	},
	{
		"name": "Карьер Южный",
		"pos": {
			"coordinates": [
			30.700178146362305,
			64.67525188469001
			],
		},
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"id": "21ccdab5baaa41fdbb3282433b3d9178"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| name | Name of the location |
| pos | Position of the location. It stores in geoJSON point format. Object with property *coordinates* with array longtitude latitude pair. |
| site_id | Location site id. These IDs can be retrieved from */sites.* |
| id | Inuque identifier of the location |

---

# <a name="location">GET /sites/:site_id/locations/:location_id</a>

Returns json data about one or all location on specified site. If you don't set *location_id* result will contain all site locations. To get info only about one location you should set *location_id* in request url.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/locations/:location_id
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
| site_id | Yes | Location site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| location_id | No | Location ids can be retrieved from */sites/:site_id/locations* Set location id to get data for one location. | | 1af7eb3146074daf8de07681a424104b |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/locations/1af7eb3146074daf8de07681a424104b
`

### Example response

```
{
	"name": "Карьер Центральный",
	"pos": {
		"coordinates": [
		30.646963119506836,
		64.68692440226665
		],
	},
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"id": "1af7eb3146074daf8de07681a424104b"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| name | Name of the location |
| pos | Position of the location. It stores in geoJSON point format. Object with property *coordinates* with array longtitude latitude pair. |
| site_id | Location site id. These IDs can be retrieved from */sites.* |
| id | Inuque identifier of the location |

---

# <a name="new-location">POST /sites/:site_id/locations</a>

Create new location from json string for specified site. 

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/locations
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
| site_id | Yes | Location site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the location | | Main gate, Slag quarry |
| pos | Yes | Position of the location. It stores in geoJSON point format. Object with property *coordinates* with array longtitude latitude pair.  | | { "coordinates": [ 30.646963119506836, 64.68692440226665 ] } |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/locations
`

### Example Body

```
{
	"name": "New location",
	"pos": {
		"coordinates": [
		30.646963119506836,
		64.68692440226665
		]
	},
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba"
}
```

### Example response

```
{
	"name": "New location",
	"pos": {
		"coordinates": [
		30.646963119506836,
		64.68692440226665
		],
	},
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"id": "f4763cb96d214254ada7d7e0f53940be"
}
```

### Response explanation

The result is json data of new created object.

---

# <a name="edit-location">PUT /sites/:site_id/locations/:location_id</a>

Edit existing location.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/locations/:location_id
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
| site_id | No | Location site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the location | | Main gate, Slag quarry |
| pos | Yes | Position of the location. It stores in geoJSON point format. Object with property *coordinates* with array longtitude latitude pair.  | | { "coordinates": [ 30.646963119506836, 64.68692440226665 ] } |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Location site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| location_id | No | Location ids can be retrieved from */sites/:site_id/locations* | | 1af7eb3146074daf8de07681a424104b |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
PUT http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/locations/f4763cb96d214254ada7d7e0f53940be
`

### Example Body

```
{
	"name": "New location1",
	"pos": {
		"coordinates": [
		30.65696,
		64.69692
		]
	}
}
```

### Example response

```
{
	"name": "New location1",
	"pos": {
		"coordinates": [
		30.65696,
		64.69692
		],
	},
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"id": "f4763cb96d214254ada7d7e0f53940be"
}
```

### Response explanation

The result is json data of the edited object.

---

# <a name="delete-location">DELETE /sites/:site_id/locations/:location_id</a>

Deletes existing location.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/locations/:location_id
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
| site_id | Yes | Location site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| location_id | No | Location ids can be retrieved from */sites/:site_id/locations* | | 1af7eb3146074daf8de07681a424104b |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 DELETE http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/locations/f4763cb96d214254ada7d7e0f53940be
`

### Example response

```
{
	"name": "New location1",
	"pos": {
		"coordinates": [
		30.65696,
		64.69692
		],
	},
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"id": "f4763cb96d214254ada7d7e0f53940be"
}
```

### Response explanation

The result is json data of the deleted object.