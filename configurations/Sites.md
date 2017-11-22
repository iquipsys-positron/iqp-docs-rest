## Get sites

# GET /sites

Returns json array with data about existing sites

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites
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


# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites
`

# Example Responce

```
{
	"total": 71,
	"data": [
	{
		"center": {
			"type": "Point",
			"coordinates": [],
		},
		"name": "Новая площадка для 1@1.com",
		"create_time": "2017-08-11T14:53:44.726Z",
		"active": true,
		"version": 10,
		"code": "11COM97",
		"active_int": 60,
		"inactive_int": 300,
		"offsite_int": 900,
		"offline_timeout": 900,
		"radius": 10,
		"geometry": {...},
		"boundaries": {...},
		"id": "964fe4e7b3034e48b47053a9431d215c"
	},
	{
		"center": {
			"type": "Point",
			"coordinates": [],
		},
		"name": "erfdr4ed",
		"language": "ru",
		"create_time": "2017-09-18T12:37:46.067Z",
		"active": true,
		"version": 122,
		"code": "ERFDR66",
		"active_int": 60,
		"inactive_int": 300,
		"offsite_int": 900,
		"offline_timeout": 900,
		"radius": 10,
		"geometry": {...},
		"boundaries": {...},
		"id": "9797346dc74f4f048b713d60bb433850"
	},
	...
}
```

---

## Get site info

# GET /sites/:site_id

Returns json data about one or all site on specified site. If you don't set *site_id* result will contain all  sites. To get info only about one site you should set *site_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id
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
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba
`

# Example Responce

```
{
	"radius": 4.151634860479783,
	"center": {
		"type": "Point",
		"coordinates": [
		30.68261719042971,
		64.6891835535622
		],
	},
	"name": "Demo Minesite",
	"create_time": "2017-08-29T13:08:41.174Z",
	"active": true,
	"version": 180,
	"code": "DEMOM58",
	"active_int": 11,
	"inactive_int": 300,
	"offsite_int": 900,
	"offline_timeout": 900,
	"geometry": {...},
	"boundaries": {...},
	"language": "ru",
	"timezone": "Asia/Beirut",
	"data_rate": 0,
	"description": "Mine site with large territory and a few controlled objects",
	"address": "Some place, KC 123456 nnnn",
	"org_size": 100,
	"industry": "Quarries",
	"purpose": "safe",
	"total_sites": 2,
	"map_north": null,
	"id": "9cfaf79bc95b4a9e912314eb3db7a4ba"
}
```

---

## Generate site code

# POST /sites/:site_id/generate_code

Generate new unique identify code for site. As respond returns new generated code. Doesn't change existing code.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/generate_code
`

# Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |
| Requires body | No |

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
POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/generate_code
`

# Example Responce

```
"DEMOM56"
```

---

## Create site

# POST /sites

Creates new site from json data.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites
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
| name | Yes | Name of the site | | Work zone, Special equipment zone |
| center | No | Request can execute without center, but site must be on the map, so set site center. It stores in geoJSON point format. Object with properties *type* and *coordinates* with array longtitude latitude pair.  | | { "type": "Point", "coordinates": [ 30.694127082824707, 64.69424468980802 ] } |
| radius | No | Radius from site center the border. Stores in killometers. | 10 | 4.15 |
| code | No | Automaticly generated unique code for site identification | | DEMOM58 |
| active_int | Interval in seconds between messages from device, when it is active | 60 | 60 |
| inactive_int | Interval in seconds between messages from device, when it is inactive | 300 | 300 |
| offsite_int | Interval in seconds between messages from device, when it is out of site | 900 | 900 |
| offline_timeout | Timeout in seconds when device become offline. When system doesn't receives any message from device *offline_timeout* seconds the device become offline on site | 900 | 900 |
| language | No | Language of the site | | en, ru |
| timezone | No | Time zone of the site | | Asia/Beirut, Europe/Moscow |
| description | No | Site description, some info about site | |  Mine site with large territory and a few controlled objects | 

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites
`

# Example Body

```
{
  "name": "New empty site",
  "center": {
		"type": "Point",
		"coordinates": [
		30.68261719042971,
		64.6891835535622
		],
	}
}
```

# Example Responce

```
{
	"name": "New empty site",
     "center": {
		"type": "Point",
		"coordinates": [
		30.68261719042971,
		64.6891835535622
		],
	},
	"create_time": "2017-11-21T11:02:39.451Z",
	"active": true,
	"version": 220,
	"code": "NEWEM12",
	"active_int": 60,
	"inactive_int": 300,
	"offsite_int": 900,
	"offline_timeout": 900,
	"radius": 10,
	"id": "1c1bf27822cc41e688575595f747fb0e"
}
```

---

## Validate code

# POST /sites/validate_code

Using this request you can find existing site by code. If site exists request returns site id, otherwise empty string.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/validate_code
`

# Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |
| Requires body | Yes |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

- ### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| code | Yes | Code of the existing site, you can get it from */sites* | | DELTH84 |

# Example Request

`
POST http://tracker.pipservices.net:8080/api/v1/sites/validate_code
`

# Example Body

```
{
    "code": "DELTH84"
}

```

# Example Responce

```
"9e55c43454ad4c6f99cb20e06aac3b95"
```

---

## Edit site

# PUT /sites/:site_id

Edit info about existing site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id
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
| name | No | Name of the site | | Work zone, Special equipment zone |
| center | No | Request can execute without center, but site must be on the map, so set site center. It stores in geoJSON point format. Object with properties *type* and *coordinates* with array longtitude latitude pair.  | | { "type": "Point", "coordinates": [ 30.694127082824707, 64.69424468980802 ] } |
| radius | No | Radius from site center the border. Stores in killometers. | 10 | 4.15 |
| code | No | Automaticly generated unique code for site identification | | DEMOM58 |
| active_int | Interval in seconds between messages from device, when it is active | 60 | 60 |
| inactive_int | Interval in seconds between messages from device, when it is inactive | 300 | 300 |
| offsite_int | Interval in seconds between messages from device, when it is out of site | 900 | 900 |
| offline_timeout | Timeout in seconds when device become offline. When system doesn't receives any message from device *offline_timeout* seconds the device become offline on site | 900 | 900 |
| language | No | Language of the site | | en, ru |
| timezone | No | Time zone of the site | | Asia/Beirut, Europe/Moscow |
| description | No | Site description, some info about site | |  Mine site with large territory and a few controlled objects | 

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/1c1bf27822cc41e688575595f747fb0e
`

# Example Body

```
{
  "language": "en",
  "timezone": "Europe/Moscow"
}
```

# Example Responce

```
{
	"name": "New empty site",
     "center": {
		"type": "Point",
		"coordinates": [
		30.68261719042971,
		64.6891835535622
		],
	},
	"create_time": "2017-11-21T11:02:39.451Z",
	"active": true,
	"version": 222,
	"code": "181063",
	"active_int": 60,
	"inactive_int": 300,
	"offsite_int": 900,
	"offline_timeout": 900,
	"radius": 10,
	"language": "en",
	"timezone": "Europe/Moscow",
	"id": "1c1bf27822cc41e688575595f747fb0e"
}
```

---

## Delete site

# DELETE /sites/:site_id

Delete existing site from system.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id
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
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 1c1bf27822cc41e688575595f747fb0e |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/1c1bf27822cc41e688575595f747fb0e
`

# Example Responce

```
{
	"name": "New empty site",
     "center": {
		"type": "Point",
		"coordinates": [
		30.68261719042971,
		64.6891835535622
		],
	},
	"create_time": "2017-11-21T11:02:39.451Z",
	"active": true,
	"version": 222,
	"code": "181063",
	"active_int": 60,
	"inactive_int": 300,
	"offsite_int": 900,
	"offline_timeout": 900,
	"radius": 10,
	"language": "en",
	"timezone": "Europe/Moscow",
	"id": "1c1bf27822cc41e688575595f747fb0e"
}
```

---

## Remove site

# POST /sites/:site_id/remove

Remove signed user from setted site. Returns nothing, and disconnects user from site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/remove
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
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9e55c43454ad4c6f99cb20e06aac3b95 |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9e55c43454ad4c6f99cb20e06aac3b95/remove
`

# Example Responce

*No content*