## Get site object groups

# GET /sites/:site_id/object_groups

Returns json array with data about all object groups on specified site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_groups
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
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 89efee4152f74944932b1aa9ef78dedd |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_groups
`

# Example Responce

```
{
	"total": 11,
	"data": [
	{
		"name": "Quality control",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"object_ids": [
		"841abccea54d47bd87b04195764a859b",
		"6470351cad3a46f8b484a92d7dcacce1",
		"e17172ad05d448d18450aca6f6fff653",
		"6fb41f9479024da79b9f76a2daba053c"
		],
		"id": "561154dd93154c9eb307d1f0569a67db"
	},
	{
		"name": "Ancillary workers",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"object_ids": [
		"6470351cad3a46f8b484a92d7dcacce1",
		"a37ba2449acd4cf6b3a5eccff65f0f5d",
		"7322a1eabe604efe873ac0c461e7265a"
		],
		"id": "d2ca097c76c94d61b20d96f96ee041af"
	},
	...
}
```

---

## Get object group info

# GET /sites/:site_id/object_groups/:group_id

Returns json data about one or all object groups on specified site. If you don't set *group_id* result will contain all site object groups. To get info only about one object group you should set *group_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_groups/:group_id
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
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 89efee4152f74944932b1aa9ef78dedd |
| group_id | No | Group ids can be retrieved from */sites/:site_id/object_groups/* Set object group id to get data for one object group. | | 561154dd93154c9eb307d1f0569a67db |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_groups/561154dd93154c9eb307d1f0569a67db
`

# Example Responce

```
{
"name": "Quality control",
"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
"object_ids": [
  "841abccea54d47bd87b04195764a859b",
  "6470351cad3a46f8b484a92d7dcacce1",
  "e17172ad05d448d18450aca6f6fff653",
  "6fb41f9479024da79b9f76a2daba053c"
],
"id": "561154dd93154c9eb307d1f0569a67db"
}
```

---

## Create object group

# POST /sites/:site_id/object_groups

Creates new object group from json string for specified site. 

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_groups
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
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 89efee4152f74944932b1aa9ef78dedd |
| name | Yes | Name of the new object group | | Drivers, Trucks |
| object_ids | No | Array of string object ids. These ids can be retrieved from */sites/:site_id/control_objects* |  | ["841abccea54d47bd87b04195764a859b","6470351cad3a46f8b484a92d7dcacce1",] |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 89efee4152f74944932b1aa9ef78dedd |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_groups
`

# Example Body

```
{
	"name": "New group",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba"
}
```

# Example Responce

```
{
"name": "New group",
"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
"object_ids": [],
"id": "ff5aa58819004f34a1a1485e61dd3c26"
}
```

---

## Edit object group

# PUT /sites/:site_id/object_groups/:group_id

Edit existing object group.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_groups/:group_id
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
| site_id | No | Site id. These IDs can be retrieved from */sites.*| | 89efee4152f74944932b1aa9ef78dedd |
| name | No | Name of the new object group | | Drivers, Trucks |
| object_ids | No | Array of string object ids. These ids can be retrieved from */sites/:site_id/control_objects* |  | ["841abccea54d47bd87b04195764a859b","6470351cad3a46f8b484a92d7dcacce1",] |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 89efee4152f74944932b1aa9ef78dedd |
| group_id | No | Group ids can be retrieved from */sites/:site_id/object_groups/* Set object group id to get data for one object group. | | 561154dd93154c9eb307d1f0569a67db |

# Example Request

`
 PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_groups/ff5aa58819004f34a1a1485e61dd3c26
`

# Example Body

```
{
  "name": "New group1", 
  "object_ids" : "841abccea54d47bd87b04195764a859b"
}
```

# Example Responce

```
{
"name": "New group1",
"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
"object_ids": [
  "841abccea54d47bd87b04195764a859b"
],
"id": "ff5aa58819004f34a1a1485e61dd3c26"
}
```

---

## Delete object groups

# DELETE /sites/:site_id/object_groups/:group_id

Deletes existing object group.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/object_groups/:group_id
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
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 89efee4152f74944932b1aa9ef78dedd |
| group_id | No | Group ids can be retrieved from */sites/:site_id/object_groups/* Set object group id to get data for one object group. | | 561154dd93154c9eb307d1f0569a67db |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_groups/ff5aa58819004f34a1a1485e61dd3c26
`

# Example Responce

```
{
"name": "New group1",
"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
"object_ids": [
  "841abccea54d47bd87b04195764a859b"
],
"id": "ff5aa58819004f34a1a1485e61dd3c26"
}
```