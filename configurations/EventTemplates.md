Page navigation

* [Get worksiteevent templates](#event-templates)
* [Getevent template info](#event-template)
* [Createevent template](#new-event-template)
* [Updateevent template](#edit-event-template)
* [Deleteevent template](#delete-event-template)

---

# <a name="event-templates">GET /sites/:site_id/event_templates</a>

Returns json array with data about all event templates on specified site.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/event_templates
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
| site_id | Yes | Event template site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/event_templates
`

### Example response

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

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Event template site id. These IDs can be retrieved from */sites.* |
| set_pos | This value indicates is allowed to set position for event while event creation using this event template |
| description | Description on event template. You can set it's name here |
| severity | Severity of the event template, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. |
| set_object | This value indicates is allowed to set objects related to event while event creation using this event template |
| set_time | This value indicates is allowed to set time for event while event creation using this event template |
| id | Inuque identifier of the event template |

---

# <a name="event-template">GET /sites/:site_id/event_templates/:template_id</a>

Returns json data about one or all event templates on specified site. If you don't set *template_id* result will contain all site event templates. To get info only about one event template you should set *template_id* in request url.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/event_templates/:template_id
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
| site_id | Yes | Event template site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| template_id | No | Template ids can be retrieved from */sites/:site_id/event_templates* Set template id to get data for one event template. | | c363e0d0856d40a2824da555f6ce399a |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/event_templates/c363e0d0856d40a2824da555f6ce399a
`

### Example response

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

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| site_id | Event template site id. These IDs can be retrieved from */sites.* |
| set_pos | This value indicates is allowed to set position for event while event creation using this event template |
| description | Description on event template. You can set it's name here |
| severity | Severity of the event template, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. |
| set_object | This value indicates is allowed to set objects related to event while event creation using this event template |
| set_time | This value indicates is allowed to set time for event while event creation using this event template |
| id | Inuque identifier of the event template |

---

# <a name="new-event-template">POST /sites/:site_id/event_templates</a>

Create new event template from json string for specified site. 

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/event_templates
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
| site_id | Yes | Event template site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| severity | Yes | Severity of the event template, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. | | 0, 50, 100 |
| description | No | Description on event template. You can set it's name here. | | Super critical event |
| set_pos | No | This value indicates is allowed to set position for event while event creation using this event template | | true, false |
| set_object | No | This value indicates is allowed to set objects related to event while event creation using this event template | | true, false |
| set_time | No | This value indicates is allowed to set time for event while event creation using this event template | | true, false |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Event template site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/event_templates
`

### Example Body

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

### Example response

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

### Response explanation

The result is json data of new created object.

---

# <a name="edit-event-template">PUT /sites/:site_id/event_templates/:template_id</a>

Edit existing event template.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/event_templates/:template_id
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
| site_id | No | Event template site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| severity | Yes | Severity of the event template, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. | | 0, 50, 100 |
| description | No | Description on event template. You can set it's name here. | | Super critical event |
| set_pos | No | This value indicates is allowed to set position for event while event creation using this event template | | true, false |
| set_object | No | This value indicates is allowed to set objects related to event while event creation using this event template | | true, false |
| set_time | No | This value indicates is allowed to set time for event while event creation using this event template | | true, false |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Event template site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| template_id | No | Template ids can be retrieved from */sites/:site_id/event_templates*| | c363e0d0856d40a2824da555f6ce399a |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 PUT http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/event_templates/206721eb410344fa8c3126c1d8053feb
`

### Example Body

```
{
	"set_pos": false,
	"description": "New event template1",
	"severity": 100,
	"set_object": false,
	"set_time": false
}
```

### Example response

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

### Response explanation

The result is json data of the edited object.

---

# <a name="delete-event-template">DELETE /sites/:site_id/event_templates/:template_id</a>

Deletes existing event template.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/event_templates/:template_id
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

### Access security 

To execute this request needed site manager or higher roles.

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Event template site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| template_id | No | Template ids can be retrieved from */sites/:site_id/event_templates* | | c363e0d0856d40a2824da555f6ce399a |

### Example Request

`
 DELETE http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/event_templates/206721eb410344fa8c3126c1d8053feb
`

### Example response

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

### Response explanation

The result is json data of the deleted object.