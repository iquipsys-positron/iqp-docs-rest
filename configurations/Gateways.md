# GET /sites/:site_id/gateways

Returns json array with data about all gateways on specified site.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/gateways
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
| site_id | Yes | Gateway site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/gateways
`

### Example response

```
{
	"total": 4,
	"data": [
	{
		"label": "Gateway2",
		"active": true,
		"udi": "0000000002",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"model": "multiconnect conduit",
		"create_time": "2017-08-29T13:08:56.083Z",
		"id": "3a7e8b7ad1074f50a8bcf04073b4e39f"
	},
	{
		"model": "unknown",
		"udi": "45d5678976677",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"active": true,
		"create_time": "2017-09-20T17:42:39.549Z",
		"id": "c5100dc948a0451889864abb091a3313"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Gateway site id. These IDs can be retrieved from */sites.* |
| label | Human readable label for gateway |
| model | Model of the gateway. Can take next values **multiconnect conduit** or **unknown** |
| udi | Gateway MAC address |
| create_time | Time of the gateway creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| active | Variable to store is gateway active |
| id | Inuque identifier of the gateway |

---

# GET /sites/:site_id/gateways/:gateway_id

Returns json data about one or all gateways on specified site. If you don't set *gateway_id* result will contain all site gateways. To get info only about one gateway you should set *gateway_id* in request url.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/gateways/:gateway_id
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
| site_id | Yes | Gateway site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| gateway_id | No | Gateway ids can be retrieved from */sites/:site_id/gateways/* Set gateway id to get data for one gateway. | | 3a7e8b7ad1074f50a8bcf04073b4e39f |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/gateways/3a7e8b7ad1074f50a8bcf04073b4e39f
`

### Example response

```
{
	"label": "Gateway2",
	"active": true,
	"udi": "0000000002",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"model": "multiconnect conduit",
	"create_time": "2017-08-29T13:08:56.083Z",
	"stats": [],
	"id": "3a7e8b7ad1074f50a8bcf04073b4e39f"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| site_id | Gateway site id. These IDs can be retrieved from */sites.* |
| label | Human readable label for gateway |
| model | Model of the gateway. Can take next values **multiconnect conduit** or **unknown** |
| udi | Gateway MAC address |
| create_time | Time of the gateway creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| active | Variable to store is gateway active |
| id | Inuque identifier of the gateway |


---

# Create gateway

### POST /sites/:site_id/gateways

Creates new gateway from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/gateways
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
| site_id | Yes | Gateway site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| udi | Yes | Gateway MAC address | | 1F52GH86F9A8 |
| model | Model of the gateway. Can take next values **multiconnect conduit** or **unknown** |
| label | No | Human readable label for gateway | | gateway01 |
| active | No | Variable to store is gateway active | true | true, false |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Gateway site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/gateways
`

### Example Body

```
{
	"label": "New gateway",
	"active": true,
	"udi": "123456789123",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba"
}
```

### Example response

```
{
	"label": "New gateway",
	"active": true,
	"udi": "123456789123",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"create_time": "2017-11-03T17:07:25.469Z",
	"stats": [],
	"id": "aafa6bfefd674529a33eaf9da7e54c61"
}
```

### Response explanation

The result is json data of new created object.

---

# POST /sites/:site_id/gateways/validate_udi

Return gateway id for setted udi in request body. If gateway not found returns empty string.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/gateways/validate_udi
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
| udi | Yes | Unique gateway identifier | | 001, abc, a1b2c3 |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/gateways/validate_udi
`

### Example Body

```
{
	"udi": "123456789123"
}
```

### Example response

```
"aafa6bfefd674529a33eaf9da7e54c61"
```

### Response explanation

The result is an id of finded gateway by udi.

---

# PUT /sites/:site_id/gateways/:gateway_id

Edit existing gateway.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/gateways/:gateway_id
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
| site_id | No | Gateway site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| udi | Yes | Gateway MAC address | | 1F52GH86F9A8 |
| label | No | Human readable label for gateway | | gateway01 |
| active | No | Variable to store is gateway active | true | true, false |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Gateway site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| gateway_id | No | Gateway ids can be retrieved from */sites/:site_id/gateways/* | | 3a7e8b7ad1074f50a8bcf04073b4e39f |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/gateways/aafa6bfefd674529a33eaf9da7e54c61
`

### Example Body

```
{
  "label": "New gateway1",
  "active": false,
  "udi": "123456789123",
  "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba"
}
```

### Example response

```
{
	"label": "New gateway1",
	"active": false,
	"udi": "123456789123",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"create_time": "2017-11-03T17:07:25.469Z",
	"stats": [],
	"id": "aafa6bfefd674529a33eaf9da7e54c61"
}
```

### Response explanation

The result is edited object json data.

---

# DELETE /sites/:site_id/gateways/:gateway_id

Deletes existing gateway.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/gateways/:gateway_id
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
| site_id | Yes | Gateway site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| gateway_id | No | Gateway ids can be retrieved from */sites/:site_id/gateways/* | | 3a7e8b7ad1074f50a8bcf04073b4e39f |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/gateways/aafa6bfefd674529a33eaf9da7e54c61
`

### Example response

```
{
	"label": "New gateway1",
	"active": false,
	"udi": "123456789123",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"create_time": "2017-11-03T17:07:25.469Z",
	"stats": [],
	"id": "aafa6bfefd674529a33eaf9da7e54c61"
}
```

### Response explanation

The result is deleted object json data.

---

# TO DO : ping gateway

# POST /sites/:site_id/gateways/:gateway_id/ping

Ping existing gateway.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/gateways/:gateway_id/ping
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

- ### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| | | | | |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/gateways/3a7e8b7ad1074f50a8bcf04073b4e39f/ping
`

### Example response

```

```

### Response explanation

The result is data about ping gateway.

---

# TO DO : request_stats gateway

# POST /sites/:site_id/gateways/:gateway_id/request_stats

Returns gateways statistics information.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/gateways/:gateway_id/request_stats
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

- ### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| | | | | |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/gateways/3a7e8b7ad1074f50a8bcf04073b4e39f/request_stats
`

### Example response

```

```

### Response explanation

The result is data about gateway statistics