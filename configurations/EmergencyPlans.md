Page navigation

* [Get worksite emergency plans](#emergency-plans)
* [Get emergency plan info](#emergency-plan)
* [Create emergency plan](#new-emergency-plan)
* [Update emergency plan](#edit-emergency-plan)
* [Delete emergency plan](#delete-emergency-plan)

---

# <a name="emergency-plans">GET /sites/:site_id/emergency_plans</a>

Returns json array with data about all emergecy plans on specified site.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/emergency_plans
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
| site_id | Yes | Emergency plan site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/emergency_plans
`

### Example response

```
{
	"total": 2,
	"data": [
	{
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"name": "Fire",
		"steps": [
		{
			"name": "Call firefighters",
			"index": 1,
			"actions": [],
		},
		{
			"name": "Tell nearby workers about emergency",
			"index": 2,
			"actions": [],
		}
		],
		"id": "1026847f61a342cc9068e96ed9c1ea72"
	},
	{
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"name": "Road accident",
		"steps": [
		{
			"name": "Contact with accident participants",
			"index": 1,
			"actions": [],
		},
		{
			"name": "Ask how big is an accident",
			"index": 2,
			"actions": [],
		},
		{
			"name": "Call an ambulance",
			"index": 3,
			"actions": [],
		},
		{
			"name": "Contact with nearby workers",
			"index": 4,
			"actions": [],
		}
		],
		"id": "e29d987847f14101b288765aa5858fdb"
	}
	],
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Emergency plan site id. These IDs can be retrieved from */sites.* |
| name | Name of the emergency plan |
| steps | Objects array of required steps to complite the emergency plan processing with sturcture described below |
| id | Inuque identifier of the device |

- ### *steps* object structure
| Name | Description | Examples |
|------|-------------|----------|
| index | The step order index | 1 |
| name | The name of step | Do that |
| actions | Objects array of step action sequence. Each action have property *type* and *params*. | *Watch example below* |
| actions.type | Type of action. There are next types: *note* for text, *call phone* for phone, *local link* for link on site, *global_link* external http address. | note |
| actions.params | Object with value for action. For *type* = **local link** params have two properties - *text* for description and *page* with next values: *ep_action_page_map* for link to monitoring map, *ep_action_page_map_people* for link to monitoring>people, *ep_action_page_map_object* for link to monitoring>objects, *ep_action_page_events* for link to monitoring>events. Other examples you can see below. | *Watch example below* |


---

# <a name="get-emergency-plan">GET /sites/:site_id/emergency_plans/:plan_id</a>

Returns json data about one or all emergecy plan on specified site. If you don't set *plan_id* result will contain all site emergecy plans. To get info only about one emergecy plan you should set *plan_id* in request url.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/emergency_plans/:plan_id
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
| site_id | Yes | Emergency plan site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| plan_id | No | Emergency plan ids can be retrieved from */sites/:site_id/emergency_plans* Set plan id to get data for one emergecy plan. | | 1026847f61a342cc9068e96ed9c1ea72 |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/emergency_plans/1026847f61a342cc9068e96ed9c1ea72
`

### Example response

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "Fire",
	"steps": [
	{
		"name": "Call firefighters",
		"index": 1,
		"actions": [],
	},
	{
		"name": "Tell nearby workers about emergency",
		"index": 2,
		"actions": [],
	}
	],
	"id": "1026847f61a342cc9068e96ed9c1ea72"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| site_id | Emergency plan site id. These IDs can be retrieved from */sites.* |
| name | Name of the emergency plan |
| steps | Objects array of required steps to complite the emergency plan processing with sturcture described below |
| id | Inuque identifier of the device |

- ### *steps* object structure
| Name | Description | Examples |
|------|-------------|----------|
| index | The step order index | 1 |
| name | The name of step | Do that |
| actions | Objects array of step action sequence. Each action have property *type* and *params*. | *Watch example below* |
| actions.type | Type of action. There are next types: *note* for text, *call phone* for phone, *local link* for link on site, *global_link* external http address. | note |
| actions.params | Object with value for action. For *type* = **local link** params have two properties - *text* for description and *page* with next values: *ep_action_page_map* for link to monitoring map, *ep_action_page_map_people* for link to monitoring>people, *ep_action_page_map_object* for link to monitoring>objects, *ep_action_page_events* for link to monitoring>events. Other examples you can see below. | *Watch example below* |

---

# <a name="new-emergency-plan">POST /sites/:site_id/emergency_plans</a>

Create new emergecy plan from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/emergency_plans
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
| site_id | Yes | Emergency plan site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the emergecy plan | | Fire, Explosion |
| steps | No | Objects array of required steps to complite the emergency plan processing | | *Watch example below* |

- ### *steps* object structure
| Name | Description | Examples |
|------|-------------|----------|
| index | The step order index | 1 |
| name | The name of step | Do that |
| actions | Objects array of step action sequence. Each action have property *type* and *params*. | *Watch example below* |
| actions.type | Type of action. There are next types: *note* for text, *call phone* for phone, *local link* for link on site, *global_link* external http address. | note |
| actions.params | Object with value for action. For *type* = **local link** params have two properties - *text* for description and *page* with next values: *ep_action_page_map* for link to monitoring map, *ep_action_page_map_people* for link to monitoring>people, *ep_action_page_map_object* for link to monitoring>objects, *ep_action_page_events* for link to monitoring>events. Other examples you can see below. | *Watch example below* |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Emergency plan site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/emergency_plans
`

### Example Body

```
{
  "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
  "name": "New Emergency plan",
  "steps": [
    {
      "index": 1,
      "name": "Do this",
      "actions": [
        {
          "type": "note",
          "params": {
            "text": "some text"
          }
        },
        {
          "type": "call phone",
          "params": {
            "phone": "+380501231223"
          }
        },
        {
          "type": "local link",
          "params": {
            "text": "description",
            "page": "ep_action_page_map"
          }
        },
        {
          "type": "global link",
          "params": {
            "uri": "http://web-site.com"
          }
        }
      ]
    },
    {
      "index": 2,
      "name": "Do that",
      "actions": []
    }
  ]
}
```

### Example response

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "New Emergency plan",
	"steps": [
	{
		"index": 1,
		"name": "Do this",
		"actions": [
		{
			"type": "note",
			"params": {
				"text": "some text"
			}
		},
		{
			"type": "call phone",
			"params": {
				"phone": "+380501231223"
			}
		},
		{
			"type": "local link",
			"params": {
				"page": "ep_action_page_map",
				"text": "description"
			}
		},
		{
			"type": "global link",
			"params": {
				"uri": "http://web-site.com"
			}
		}
		],
	},
	{
		"index": 2,
		"name": "Do that",
		"actions": [],
	}
	],
	"id": "df9cb21c557d4420a7c11d2b91eb070a"
}
```

### Response explanation

The result is json data of new created object.

---

# <a name="edit-emergency-plan">PUT /sites/:site_id/emergency_plans/:plan_id</a>

Edit existing emergecy plan.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/emergency_plans/:plan_id
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
| site_id | No | Emergency plan site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the emergecy plan | | Fire, Explosion |
| steps | No | Objects array of required steps to complite the emergency plan processing | | *Watch example below* |

- ### *steps* object structure
| Name | Description | Examples |
|------|-------------|----------|
| index | The step order index | 1 |
| name | The name of step | Do that |
| actions | Objects array of step action sequence. Each action have property *type* and *params*. | *Watch example below* |
| actions.type | Type of action. There are next types: *note* for text, *call phone* for phone, *local link* for link on site, *global_link* external http address. | note |
| actions.params | Object with value for action. For *type* = **local link** params have two properties - *text* for description and *page* with next values: *ep_action_page_map* for link to monitoring map, *ep_action_page_map_people* for link to monitoring>people, *ep_action_page_map_object* for link to monitoring>objects, *ep_action_page_events* for link to monitoring>events. Other examples you can see below. | *Watch example below* |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Emergency plan site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| plan_id | No | Object ids can be retrieved from */sites/:site_id/emergency_plans* | | df9cb21c557d4420a7c11d2b91eb070a |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/emergency_plans/df9cb21c557d4420a7c11d2b91eb070a
`

### Example Body

```
{
	"name": "New Emergency plan1",
	"steps": [
	{
		"index": 1,
		"name": "Do this",
		"actions": [
		{
			"type": "note",
			"params": {
				"text": "some text"
			}
		},
		{
			"type": "call phone",
			"params": {
				"phone": "+380501231223"
			}
		},
		{
			"type": "local link",
			"params": {
				"text": "description",
				"page": "ep_action_page_map"
			}
		},
		{
			"type": "global link",
			"params": {
				"uri": "http://web-site.com"
			}
		}
		]
	}
	]
}
```

### Example response

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "New Emergency plan1",
	"steps": [
	{
		"name": "Do this",
		"index": 1,
		"actions": [
		{
			"params": {
				"text": "some text"
			},
			"type": "note"
		},
		{
			"params": {
				"phone": "+380501231223"
			},
			"type": "call phone"
		},
		{
			"params": {
				"page": "ep_action_page_map",
				"text": "description"
			},
			"type": "local link"
		},
		{
			"params": {
				"uri": "http://web-site.com"
			},
			"type": "global link"
		}
		],
	}
	],
	"id": "df9cb21c557d4420a7c11d2b91eb070a"
}
```

### Response explanation

The result is json data of the edited object.

---

# <a name="delete-emergency-plan">DELETE /sites/:site_id/emergency_plans/:plan_id</a>

Deletes existing emergecy plan.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/emergency_plans/:plan_id
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
| site_id | Yes | Emergency plan site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| plan_id | No | Object ids can be retrieved from */sites/:site_id/emergency_plans* | | df9cb21c557d4420a7c11d2b91eb070a |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/emergency_plans/df9cb21c557d4420a7c11d2b91eb070a
`

### Example response

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "New Emergency plan1",
	"steps": [
	{
		"name": "Do this",
		"index": 1,
		"actions": [
		{
			"params": {
				"text": "some text"
			},
			"type": "note"
		},
		{
			"params": {
				"phone": "+380501231223"
			},
			"type": "call phone"
		},
		{
			"params": {
				"page": "ep_action_page_map",
				"text": "description"
			},
			"type": "local link"
		},
		{
			"params": {
				"uri": "http://web-site.com"
			},
			"type": "global link"
		}
		],
	}
	],
	"id": "df9cb21c557d4420a7c11d2b91eb070a"
}
```

### Response explanation

The result is data about deleted object.