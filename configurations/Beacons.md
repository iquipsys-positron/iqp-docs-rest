# GET /sites/:site_id/beacons

Returns json array with data about all beacons on specified site.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons
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
| site_id | Yes | Beacon site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons
`

### Example response

```
{
	"total": 1,
	"data": [
	{
		"udi": "123123",
		"label": "beacon1",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"id": "11fdec89d29b481c9c21d2ed050f65fb"
	}
	]
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| udi | Beacon unique identifier |
| label | Human readable label for beacon |
| site_id | Beacon site id. These IDs can be retrieved from */sites.* |
| id | Inuque identifier of the beacon |

---

# GET /sites/:site_id/beacons/:beacon_id

Returns json data about one or all beacons on specified site. If you don't set *beacon_id* result will contain all site beacons. To get info only about one beacon you should set *beacon_id* in request url.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons/:beacon_id
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
| site_id | Yes | Beacon site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| beacon_id | No | beacon ids can be retrieved from */sites/:site_id/beacons/* Set beacon id to get data for one beacon. | | 11fdec89d29b481c9c21d2ed050f65fb |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons/11fdec89d29b481c9c21d2ed050f65fb
`

### Example response

```
{
    "udi": "123123",
    "label": "beacon1",
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
    "id": "11fdec89d29b481c9c21d2ed050f65fb"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| udi | Beacon unique identifier |
| label | Human readable label for beacon |
| site_id | Beacon site id. These IDs can be retrieved from */sites.* |
| id | Inuque identifier of the beacon |

---

# TO DO : POST /sites/:site_id/beacons/calculate_position

Calculates object position by data from beacons

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons/calculate_position
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
| site_id | Yes | Beacon site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| udis | Yes | Array fo beacon unique identifiers | | ["8765456"] |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Beacon site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons/calculate_position
`

### Example Body

```
{
    "udis": ["8765456", "2125563"],
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba"
}
```

### Example response

```

```

### Response explanation

The request result is an object position.

---

# POST /sites/:site_id/beacons

Create new beacon from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons
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
| site_id | Yes | Beacon site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| udi | Yes | beacon unique identifier | | 8765456 |
| label | No | Human readable label for beacon | | beacon2 |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Beacon site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons
`

### Example Body

```
{
    "udi": "8765456",
    "label": "beacon2",
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba"
}
```

### Example response

```
{
    "udi": "8765456",
    "label": "beacon2",
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
    "id": "cb1f859233a04b0fb68c8d8f01dca9d2"
}

```

### Response explanation

The result is json data of new created object.

---

# PUT /sites/:site_id/beacons/:beacon_id

Edit existing beacon.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons/:beacon_id
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
| site_id | No | Beacon site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| udi | Yes | beacon unique identifier | | 8765456 |
| label | No | Human readable label for beacon | | beacon2 |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Beacon site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| beacon_id | No | beacon ids can be retrieved from */sites/:site_id/beacons/* | | cb1f859233a04b0fb68c8d8f01dca9d2 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons/cb1f859233a04b0fb68c8d8f01dca9d2
`

### Example Body

```
{
    "udi": "87654561",
    "label": "beacon2_"
}
```

### Example response

```
{
    "udi": "87654561",
    "label": "beacon2_",
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
    "id": "cb1f859233a04b0fb68c8d8f01dca9d2"
}
```

### Response explanation

The result is json data of the edited object.

---

# DELETE /sites/:site_id/beacons/:beacon_id

Deletes existing beacon.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons/:beacon_id
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
| site_id | Yes | Beacon site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| beacon_id | No | beacon ids can be retrieved from */sites/:site_id/beacons/* | | cb1f859233a04b0fb68c8d8f01dca9d2 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons/cb1f859233a04b0fb68c8d8f01dca9d2
`

### Example response

```
{
    "udi": "87654561",
    "label": "beacon2_",
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
    "id": "cb1f859233a04b0fb68c8d8f01dca9d2"
}
```

### Response explanation

The result is json data of the deleted object.