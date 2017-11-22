## Get site event templates

# GET /sites/:site_id/event_templates

Returns json array with data about all event templates on specified site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/event_templates
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
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/event_templates
`

# Example Responce

```
{
	"total": 4,
	"data": [
	{
		"set_pos": false,
		"description": "Low importance event",
		"severity": 0,
		"set_object": false,
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"set_time": true,
		"id": "311856245f4a401db85625e9777783ca"
	},
	{
		"set_pos": true,
		"description": "High importance event",
		"severity": 50,
		"set_object": false,
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"set_time": true,
		"id": "c363e0d0856d40a2824da555f6ce399a"
	},
	...
}
```

---

## Get event template info

# GET /sites/:site_id/event_templates/:template_id

Returns json data about one or all event templates on specified site. If you don't set *template_id* result will contain all site event templates. To get info only about one event template you should set *template_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/event_templates/:template_id
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
| template_id | No | Template ids can be retrieved from */sites/:site_id/event_templates* Set template id to get data for one event template. | | c363e0d0856d40a2824da555f6ce399a |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/event_templates/c363e0d0856d40a2824da555f6ce399a
`

# Example Responce

```
{
	"set_pos": true,
	"description": "High importance event",
	"severity": 50,
	"set_object": false,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"set_time": true,
	"id": "c363e0d0856d40a2824da555f6ce399a"
}
```

---

## Create event template

# POST /sites/:site_id/event_templates

Creates new event template from json string for specified site. 

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/event_templates
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
| severity | Yes | Severity of the event template, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. | | 0, 50, 100 |
| description | No | Description on event template. You can set it's name here. | | Super critical event |
| set_pos | No | This value indicates is allowed to set position for event while event creation using this event template | | true, false |
| set_object | No | This value indicates is allowed to set objects related to event while event creation using this event template | | true, false |
| set_time | No | This value indicates is allowed to set time for event while event creation using this event template | | true, false |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/event_templates
`

# Example Body

```
{
	"set_pos": true,
	"description": "New event template",
	"severity": 50,
	"set_object": false,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"set_time": true
}
```

# Example Responce

```
{
	"set_pos": true,
	"description": "New event template",
	"severity": 50,
	"set_object": false,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"set_time": true,
	"id": "206721eb410344fa8c3126c1d8053feb"
}
```

---

## Edit event template

# PUT /sites/:site_id/event_templates/:template_id

Edit existing event template.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/event_templates/:template_id
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
| severity | Yes | Severity of the event template, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. | | 0, 50, 100 |
| description | No | Description on event template. You can set it's name here. | | Super critical event |
| set_pos | No | This value indicates is allowed to set position for event while event creation using this event template | | true, false |
| set_object | No | This value indicates is allowed to set objects related to event while event creation using this event template | | true, false |
| set_time | No | This value indicates is allowed to set time for event while event creation using this event template | | true, false |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| template_id | No | Template ids can be retrieved from */sites/:site_id/event_templates* Set template id to get data for one event template. | | c363e0d0856d40a2824da555f6ce399a |

# Example Request

`
 PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/event_templates/206721eb410344fa8c3126c1d8053feb
`

# Example Body

```
{
  "set_pos": false,
  "description": "New event template1",
  "severity": 100,
  "set_object": false,
  "set_time": false
}
```

# Example Responce

```
{
"set_pos": false,
"description": "New event template1",
"severity": 100,
"set_object": false,
"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
"set_time": false,
"id": "206721eb410344fa8c3126c1d8053feb"
}
```

---

## Delete event template

# DELETE /sites/:site_id/event_templates/:template_id

Deletes existing event template.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/event_templates/:template_id
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
| template_id | No | Template ids can be retrieved from */sites/:site_id/event_templates* Set template id to get data for one event template. | | c363e0d0856d40a2824da555f6ce399a |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/event_templates/206721eb410344fa8c3126c1d8053feb
`

# Example Responce

```
{
"set_pos": false,
"description": "New event template1",
"severity": 100,
"set_object": false,
"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
"set_time": false,
"id": "206721eb410344fa8c3126c1d8053feb"
}
```