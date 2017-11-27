Page navigation

* [Get worksite rules](#rules)
* [Get rule info](#rule)
* [Calculate position](#calc-position)
* [Create rule](#new-rule)
* [Update rule](#edit-rule)
* [Delete rule](#delete-rule)

---

# <a name="rules">GET /sites/:site_id/rules</a>

Returns json array with data about all rules on specified site.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/rules
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
| site_id | Yes | Rule site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/rules
`

### Example response

```
{
	"total": 10,
	"data": [
	{
		"interval": 300,
		"severity": 50,
		"condition": {
			"max value": "40"
		},
		"name": "Speed limit 40km/h",
		"type": "max speed",
		"incident": true,
		"send_sms": false,
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"phones": null,
		"emails": null,
		"show_journal": true,
		"exclude_zone_ids": [],
		"include_zone_ids": [],
		"exclude_group_ids": [],
		"exclude_object_ids": [],
		"include_group_ids": [
		"28417b77fae741d59fcfd8933f6af461"
		],
		"include_object_ids": [
		"7a956331bcce4bf48371984f8c187929"
		],
		"recipient_ids": [],
		"create_time": true,
		"id": "0cf6a1ee5d16457b85373b84421fc9b7"
	},
	{
		"interval": 300,
		"severity": 50,
		"condition": {
			"max value": "65"
		},
		"name": "Speed limit 65km/h",
		"type": "max speed",
		"incident": true,
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"phones": null,
		"emails": null,
		"show_journal": true,
		"exclude_zone_ids": [],
		"include_zone_ids": [],
		"exclude_group_ids": [],
		"exclude_object_ids": [],
		"include_group_ids": [
		"896ba1e245a248ccb52aaae57d522374",
		"044d550bdc36426caf7f062c185c533e"
		],
		"include_object_ids": [],
		"recipient_ids": [],
		"create_time": true,
		"id": "5ad48b88358d48fc9c84e90498748a8f"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Rule site id. These IDs can be retrieved from */sites.*|
| name | Name of the rule |
| type | Type of the rule. There are next rule types: *max speed*, *min speed*, *entry*, *exit*, *immobility*, *disappear*, *presence*, *online*, *pressed*, *long_pressed* |
| severity | Severity of the rulre, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. |
| interval | Interval in seconds between incidents creation for this rule |
| condition | Object with expected value. For rules type max value condition object have field *max value*, for min speed - *min value*, for immobility/presence - *duration*. Duration stored in seconds. |
| incident | Variable for indicataion will be created an incident when rule is triggered |
| show_journal | Variable for indicataion will be an event registeredt when rule is triggered |
| phones | List of phones for sms delivery when rule is triggered. If you don't want to send sms set variable to null |
| emails | List of emails for mail delivery when rule is triggered. If you don't want to send emails set variable to null |
| include_group_ids | Array of groups id, which are included to this rule. These ids can be retrieved from *sites/:site_id/groups*. If it doesn't set rule active for all groups. |
| exclude_group_ids | Array of groups id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/groups*. |
| include_zone_ids | Array of zone id, which are included to this rule. These ids can be retrieved from *sites/:site_id/zones*. If it doesn't set rule active for all zones. |
| exclude_zone_ids | Array of zone id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/zones*. |
| include_object_ids | Array of object id, which are included to this rule. These ids can be retrieved from *sites/:site_id/control_objects*. If it doesn't set rule active for all objects. |
| exclude_object_ids | Array of object id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/control_objects*. |
| create_time | Time of the gateway creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| id | Inuque identifier of the event template |

---

# <a name="rule">GET /sites/:site_id/rules/:rule_id</a>

Returns json data about one or all rule on specified site. If you don't set *rule_id* result will contain all site rules. To get info only about one rule you should set *rule_id* in request url.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/rules/:rule_id
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
| site_id | Yes | Rule site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| rule_id | No | rule ids can be retrieved from */sites/:site_id/rules* Set rule id to get data for one rule. | | 5ad48b88358d48fc9c84e90498748a8f |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/rules/5ad48b88358d48fc9c84e90498748a8f
`

### Example response

```
{
	"interval": 300,
	"severity": 50,
	"condition": {
		"max value": "65"
	},
	"name": "Speed limit 65km/h",
	"type": "max speed",
	"incident": true,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"phones": null,
	"emails": null,
	"show_journal": true,
	"exclude_zone_ids": [],
	"include_zone_ids": [],
	"exclude_group_ids": [],
	"exclude_object_ids": [],
	"include_group_ids": [
	"896ba1e245a248ccb52aaae57d522374",
	"044d550bdc36426caf7f062c185c533e"
	],
	"include_object_ids": [],
	"recipient_ids": [],
	"create_time": true,
	"id": "5ad48b88358d48fc9c84e90498748a8f"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| site_id | Rule site id. These IDs can be retrieved from */sites.*|
| name | Name of the rule |
| type | Type of the rule. There are next rule types: *max speed*, *min speed*, *entry*, *exit*, *immobility*, *disappear*, *presence*, *online*, *pressed*, *long_pressed* |
| severity | Severity of the rulre, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. |
| interval | Interval in seconds between incidents creation for this rule |
| condition | Object with expected value. For rules type max value condition object have field *max value*, for min speed - *min value*, for immobility/presence - *duration*. Duration stored in seconds. |
| incident | Variable for indicataion will be created an incident when rule is triggered |
| show_journal | Variable for indicataion will be an event registeredt when rule is triggered |
| phones | List of phones for sms delivery when rule is triggered. If you don't want to send sms set variable to null |
| emails | List of emails for mail delivery when rule is triggered. If you don't want to send emails set variable to null |
| include_group_ids | Array of groups id, which are included to this rule. These ids can be retrieved from *sites/:site_id/groups*. If it doesn't set rule active for all groups. |
| exclude_group_ids | Array of groups id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/groups*. |
| include_zone_ids | Array of zone id, which are included to this rule. These ids can be retrieved from *sites/:site_id/zones*. If it doesn't set rule active for all zones. |
| exclude_zone_ids | Array of zone id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/zones*. |
| include_object_ids | Array of object id, which are included to this rule. These ids can be retrieved from *sites/:site_id/control_objects*. If it doesn't set rule active for all objects. |
| exclude_object_ids | Array of object id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/control_objects*. |
| create_time | Time of the gateway creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| id | Inuque identifier of the event template |

---

# <a name="new-rule">POST /sites/:site_id/rules</a>

Create new rule from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/rules
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
| site_id | Yes | Rule site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the rule | | Speed limit 40 km/h, Entry zone |
| type | Yes | Type of the rule. There are next rule types: *max speed*, *min speed*, *entry*, *exit*, *immobility*, *disappear*, *presence*, *online*, *pressed*, *long_pressed* | | max speed |
| severity | No | Severity of the rulre, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. | | 0, 50, 100 |
| interval | No | Interval in seconds between incidents creation for this rule | | 300 |
| condition | No / Yes (for max speed, min speed, immobility) | Object with expected value. For rules type max value condition object have field *max value*, for min speed - *min value*, for immobility/presence - *duration*. Duration stored in seconds. | | {"duration":900} |
| incident | No | Variable for indicataion will be created an incident when rule is triggered | | true |
| show_journal | No | Variable for indicataion will be an event registeredt when rule is triggered | | true |
| phones | No | List of phones for sms delivery when rule is triggered. If you don't want to send sms set variable to null | | null, +380501231223 |
| emails | No | List of emails for mail delivery when rule is triggered. If you don't want to send emails set variable to null | | null, iquipsys@gmail.com |
| include_group_ids | No | Array of groups id, which are included to this rule. These ids can be retrieved from *sites/:site_id/groups*. If it doesn't set rule active for all groups. | |  ["896ba1e245a248ccb52aaae57d522374"] |
| exclude_group_ids | No | Array of groups id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/groups*. | |  ["896ba1e245a248ccb52aaae57d522374"] |
| include_zone_ids | No | Array of zone id, which are included to this rule. These ids can be retrieved from *sites/:site_id/zones*. If it doesn't set rule active for all zones. | |  ["7fa504f7b9034d979c27697f0520fdde"] |
| exclude_zone_ids | No | Array of zone id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/zones*. | |  ["7fa504f7b9034d979c27697f0520fdde"] |
| include_object_ids | No | Array of object id, which are included to this rule. These ids can be retrieved from *sites/:site_id/control_objects*. If it doesn't set rule active for all objects. | |  ["6470351cad3a46f8b484a92d7dcacce1"] |
| exclude_object_ids | No | Array of object id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/control_objects*. | |  ["6470351cad3a46f8b484a92d7dcacce1"] |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/rules
`

### Example Body

```
{
  "interval": 300,
  "severity": 50,
  "condition": {
    "max value": "65"
  },
  "name": "New rule",
  "type": "max speed",
  "incident": true,
  "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
  "phones": null,
  "emails": null,
  "show_journal": true,
  "include_group_ids": [
    "896ba1e245a248ccb52aaae57d522374",
    "044d550bdc36426caf7f062c185c533e"
  ]
}
```

### Example response

```
{
	"interval": 300,
	"severity": 50,
	"condition": {
		"max value": "65"
	},
	"name": "New rule",
	"type": "max speed",
	"incident": true,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"show_journal": true,
	"exclude_zone_ids": [],
	"include_zone_ids": [],
	"exclude_group_ids": [],
	"exclude_object_ids": [],
	"include_group_ids": [
	"896ba1e245a248ccb52aaae57d522374",
	"044d550bdc36426caf7f062c185c533e"
	],
	"include_object_ids": [],
	"recipient_ids": [],
	"create_time": true,
	"id": "3b2700490f39472dbc9cdb647936de11"
}
```

### Response explanation

The result is json data of the new created object.

---

# <a name="edit-rule">PUT /sites/:site_id/rules/:rule_id</a>

Edit existing rule.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/rules/:rule_id
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
| site_id | Yes | Rule site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the rule | | Speed limit 40 km/h, Entry zone |
| type | Yes | Type of the rule. There are next rule types: *max speed*, *min speed*, *entry*, *exit*, *immobility*, *disappear*, *presence*, *online*, *pressed*, *long_pressed* | | max speed |
| severity | No | Severity of the rulre, can take one of three values : **0** for low prioprity events, **50** for high priority events and **100** for critical events. | | 0, 50, 100 |
| interval | No | Interval in seconds between incidents creation for this rule | | 300 |
| condition | No / Yes (for max speed, min speed, immobility) | Object with expected value. For rules type max value condition object have field *max value*, for min speed - *min value*, for immobility/presence - *duration*. Duration stored in seconds. | | {"duration":900} |
| incident | No | Variable for indicataion will be created an incident when rule is triggered | | true |
| show_journal | No | Variable for indicataion will be an event registeredt when rule is triggered | | true |
| phones | No | List of phones for sms delivery when rule is triggered. If you don't want to send sms set variable to null | | null, +380501231223 |
| emails | No | List of emails for mail delivery when rule is triggered. If you don't want to send emails set variable to null | | null, iquipsys@gmail.com |
| include_group_ids | No | Array of groups id, which are included to this rule. These ids can be retrieved from *sites/:site_id/groups*. If it doesn't set rule active for all groups. | |  ["896ba1e245a248ccb52aaae57d522374"] |
| exclude_group_ids | No | Array of groups id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/groups*. | |  ["896ba1e245a248ccb52aaae57d522374"] |
| include_zone_ids | No | Array of zone id, which are included to this rule. These ids can be retrieved from *sites/:site_id/zones*. If it doesn't set rule active for all zones. | |  ["7fa504f7b9034d979c27697f0520fdde"] |
| exclude_zone_ids | No | Array of zone id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/zones*. | |  ["7fa504f7b9034d979c27697f0520fdde"] |
| include_object_ids | No | Array of object id, which are included to this rule. These ids can be retrieved from *sites/:site_id/control_objects*. If it doesn't set rule active for all objects. | |  ["6470351cad3a46f8b484a92d7dcacce1"] |
| exclude_object_ids | No | Array of object id, which are excluded from this rule. These ids can be retrieved from *sites/:site_id/control_objects*. | |  ["6470351cad3a46f8b484a92d7dcacce1"] |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Rule site id. These IDs can be retrieved from */sites.* | | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| rule_id | No | rule ids can be retrieved from */sites/:site_id/rules* | | 3b2700490f39472dbc9cdb647936de11 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/rules/3b2700490f39472dbc9cdb647936de11
`

### Example Body

```
{
  	"severity": 100,
  	"name": "New rule1",
  	"show_journal": false
}
```

### Example response

```
{
	"interval": 300,
	"severity": 100,
	"condition": {
		"max value": "65"
	},
	"name": "New rule1",
	"type": "max speed",
	"incident": true,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"show_journal": false,
	"exclude_zone_ids": [],
	"include_zone_ids": [],
	"exclude_group_ids": [],
	"exclude_object_ids": [],
	"include_group_ids": [
	"896ba1e245a248ccb52aaae57d522374",
	"044d550bdc36426caf7f062c185c533e"
	],
	"include_object_ids": [],
	"recipient_ids": [],
	"create_time": true,
	"id": "3b2700490f39472dbc9cdb647936de11"
}
```

### Response explanation

The result is json data of the edited object.

---

# <a name="delete-rule">DELETE /sites/:site_id/rules/:rule_id</a>

Deletes existing rule.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/rules/:rule_id
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
| site_id | Yes | Rule site id. These IDs can be retrieved from */sites.* | | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| rule_id | No | rule ids can be retrieved from */sites/:site_id/rules* | | 3b2700490f39472dbc9cdb647936de11 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/rules/3b2700490f39472dbc9cdb647936de11
`

### Example response

```
{
	"interval": 300,
	"severity": 100,
	"condition": {
		"max value": "65"
	},
	"name": "New rule1",
	"type": "max speed",
	"incident": true,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"show_journal": false,
	"deleted": true,
	"exclude_zone_ids": [],
	"include_zone_ids": [],
	"exclude_group_ids": [],
	"exclude_object_ids": [],
	"include_group_ids": [
	"896ba1e245a248ccb52aaae57d522374",
	"044d550bdc36426caf7f062c185c533e"
	],
	"include_object_ids": [],
	"recipient_ids": [],
	"create_time": true,
	"id": "3b2700490f39472dbc9cdb647936de11"
}
```

### Response explanation

The result is json data of the deleted object.