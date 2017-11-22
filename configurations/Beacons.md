## Get site beacons

# GET /sites/:site_id/beacons

Returns json array with data about all beacons on specified site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons
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
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons
`

# Example Responce

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

---

## Get beacon info

# GET /sites/:site_id/beacons/:beacon_id

Returns json data about one or all beacons on specified site. If you don't set *beacon_id* result will contain all site beacons. To get info only about one beacon you should set *beacon_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons/:beacon_id
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
| beacon_id | No | beacon ids can be retrieved from */sites/:site_id/beacons/* Set beacon id to get data for one beacon. | | 11fdec89d29b481c9c21d2ed050f65fb |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons/11fdec89d29b481c9c21d2ed050f65fb
`

# Example Responce

```
{
    "udi": "123123",
    "label": "beacon1",
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
    "id": "11fdec89d29b481c9c21d2ed050f65fb"
}
```

---

## Create beacon

# POST /sites/:site_id/beacons

Create new beacon from json string for specified site. 

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons
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
| udi | Yes | beacon unique identifier | | 8765456 |
| label | No | Human readable label for beacon | | beacon2 |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons
`

# Example Body

```
{
    "udi": "8765456",
    "label": "beacon2",
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba"
}
```

# Example Responce

```
{
    "udi": "8765456",
    "label": "beacon2",
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
    "id": "cb1f859233a04b0fb68c8d8f01dca9d2"
}

```

---

## Edit beacon

# PUT /sites/:site_id/beacons/:beacon_id

Edit existing beacon.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons/:beacon_id
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
| udi | Yes | beacon unique identifier | | 8765456 |
| label | No | Human readable label for beacon | | beacon2 |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| beacon_id | No | beacon ids can be retrieved from */sites/:site_id/beacons/* | | cb1f859233a04b0fb68c8d8f01dca9d2 |

# Example Request

`
 PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons/cb1f859233a04b0fb68c8d8f01dca9d2
`

# Example Body

```
{
    "udi": "87654561",
    "label": "beacon2_"
}
```

# Example Responce

```
{
    "udi": "87654561",
    "label": "beacon2_",
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
    "id": "cb1f859233a04b0fb68c8d8f01dca9d2"
}
```

---

## Delete beacon

# DELETE /sites/:site_id/beacons/:beacon_id

Deletes existing beacon.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/beacons/:beacon_id
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
| beacon_id | No | beacon ids can be retrieved from */sites/:site_id/beacons/* | | cb1f859233a04b0fb68c8d8f01dca9d2 |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/beacons/cb1f859233a04b0fb68c8d8f01dca9d2
`

# Example Responce

```
{
    "udi": "87654561",
    "label": "beacon2_",
    "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
    "id": "cb1f859233a04b0fb68c8d8f01dca9d2"
}
```