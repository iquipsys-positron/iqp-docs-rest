## Get site locations

# GET /sites/:site_id/locations

Returns json array with data about all locations on specified site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/locations
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
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/locations
`

# Example Responce

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

---

## Get location info

# GET /sites/:site_id/locations/:location_id

Returns json data about one or all location on specified site. If you don't set *location_id* result will contain all site locations. To get info only about one location you should set *location_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/locations/:location_id
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
| location_id | No | Location ids can be retrieved from */sites/:site_id/locations* Set location id to get data for one location. | | 1af7eb3146074daf8de07681a424104b |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/locations/1af7eb3146074daf8de07681a424104b
`

# Example Responce

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

---

## Create location

# POST /sites/:site_id/locations

Creates new location from json string for specified site. 

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/locations
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
| name | Yes | Name of the location | | Main gate, Slag quarry |
| pos | Yes | Position of the location. It stores in geoJSON point format. Object with property *coordinates* with array longtitude latitude pair.  | | { "coordinates": [ 30.646963119506836, 64.68692440226665 ] } |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/locations
`

# Example Body

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

# Example Responce

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

---

## Edit location

# PUT /sites/:site_id/locations/:location_id

Edit existing location.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/locations/:location_id
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
| name | Yes | Name of the location | | Main gate, Slag quarry |
| pos | Yes | Position of the location. It stores in geoJSON point format. Object with property *coordinates* with array longtitude latitude pair.  | | { "coordinates": [ 30.646963119506836, 64.68692440226665 ] } |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| location_id | No | Location ids can be retrieved from */sites/:site_id/locations* | | 1af7eb3146074daf8de07681a424104b |

# Example Request

`
PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/locations/f4763cb96d214254ada7d7e0f53940be
`

# Example Body

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

# Example Responce

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

---

## Delete location

# DELETE /sites/:site_id/locations/:location_id

Deletes existing location.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/locations/:location_id
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
| location_id | No | Location ids can be retrieved from */sites/:site_id/locations* | | 1af7eb3146074daf8de07681a424104b |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/locations/f4763cb96d214254ada7d7e0f53940be
`

# Example Responce

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