## Get site resolutions

# GET /sites/:site_id/resolutions

Returns json array with data about all resolutions on specified site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/resolutions
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
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/resolutions
`

# Example Responce

```
{
	"total": 3,
	"data": [
	{
		"default": true,
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"resolution": "Acknowledged",
		"rule_ids": [
		"0cf6a1ee5d16457b85373b84421fc9b7",
		"5ad48b88358d48fc9c84e90498748a8f",
		"926c5041121a4e688cda52978d1c0782"
		],
		"id": "d50f8396fb554dccb69f528918fb9d23"
	},
	{
		"default": true,
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"resolution": "Call supervisor",
		"rule_ids": [
		"c71278120b9c4e2a8773e1c09503e532"
		],
		"id": "2082036b232840b78d94056a75a15887"
	},
	...
}
```

---

## Get resolution info

# GET /sites/:site_id/resolutions/:resolution_id

Returns json data about one or all resolution on specified site. If you don't set *resolution_id* result will contain all site resolutions. To get info only about one resolution you should set *resolution_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/resolutions/:resolution_id
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
| resolution_id | No | Resolution ids can be retrieved from */sites/:site_id/resolutions* Set resolution id to get data for one resolution. | | 2082036b232840b78d94056a75a15887 |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/resolutions/2082036b232840b78d94056a75a15887
`

# Example Responce

```
{
	"default": true,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"resolution": "Call supervisor",
	"rule_ids": [
	"c71278120b9c4e2a8773e1c09503e532"
	],
	"id": "2082036b232840b78d94056a75a15887"
}
```

---

## Create resolution

# POST /sites/:site_id/resolutions

Creates new resolution from json string for specified site. 

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/resolutions
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
| resolution | Yes | Name of the resolution | | Call supervisor |
| default | No | Displayes if resolution will be used as default for incidents | | true, false |
| rule_ids | No | The array of string rule ids, wich incidents will be resolved by this resolution. Rule ids can be retrieved from */sites/:site_id/rules* | |  [ "c71278120b9c4e2a8773e1c09503e532" ] |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/resolutions
`

# Example Body

```
{
	"default": false,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"resolution": "Call supervisor",
	"rule_ids": [
	"c71278120b9c4e2a8773e1c09503e532"
	]
}
```

# Example Responce

```
{
	"default": false,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"resolution": "Call supervisor",
	"rule_ids": [
	"c71278120b9c4e2a8773e1c09503e532"
	],
	"id": "b1c50f73843342d8809e051bf393faf6"
}
```

---

## Edit resolution

# PUT /sites/:site_id/resolutions/:resolution_id

Edit existing resolution.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/resolutions/:resolution_id
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
| resolution | Yes | Name of the resolution | | Call supervisor |
| default | No | Displayes if resolution will be used as default for incidents | | true, false |
| rule_ids | No | The array of string rule ids, wich incidents will be resolved by this resolution. Rule ids can be retrieved from */sites/:site_id/rules* | |  [ "c71278120b9c4e2a8773e1c09503e532" ] |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| resolution_id | No | Resolution ids can be retrieved from */sites/:site_id/resolutions* Set resolution id to get data for one resolution. | | 2082036b232840b78d94056a75a15887 |

# Example Request

`
PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/resolutions/b1c50f73843342d8809e051bf393faf6
`

# Example Body

```
{
    "resolution": "new resolution1"
}
```

# Example Responce

```
{
	"default": false,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"resolution": "new resolution1",
	"rule_ids": [
	"c71278120b9c4e2a8773e1c09503e532"
	],
	"id": "b1c50f73843342d8809e051bf393faf6"
}
```

---

## Delete resolution

# DELETE /sites/:site_id/resolutions/:resolution_id

Deletes existing resolution.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/resolutions/:resolution_id
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
| resolution_id | No | Resolution ids can be retrieved from */sites/:site_id/resolutions* Set resolution id to get data for one resolution. | | 2082036b232840b78d94056a75a15887 |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/resolutions/b1c50f73843342d8809e051bf393faf6
`

# Example Responce

```
{
	"default": false,
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"resolution": "new resolution1",
	"rule_ids": [
	"c71278120b9c4e2a8773e1c09503e532"
	],
	"id": "b1c50f73843342d8809e051bf393faf6"
}
```