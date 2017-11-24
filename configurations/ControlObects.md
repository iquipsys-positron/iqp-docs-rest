# GET /sites/:site_id/control_objects

Returns json array with data about all control objects on specified site.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/control_objects
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
| site_id | Yes | Control object site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/control_objects
`

### Example response

```
{
	"total": 29,
	"data": [
	{
		"name": "Esmarelda Villalobos",
		"description": "Driver",
		"type": "employee",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"category": "person",
		"device_id": "58974eb97b6948cb986b17e219314a31",
		"group_ids": [
		"d2ca097c76c94d61b20d96f96ee041af",
		"e892a72d6a2b4ca8899efb44a860f7d0",
		"561154dd93154c9eb307d1f0569a67db"
		],
		"id": "6470351cad3a46f8b484a92d7dcacce1"
	},
	{
		"name": "TK123",
		"description": "Haul truck",
		"type": "haul",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"category": "equipment",
		"device_id": "afbdd036a6d449bf9fef99d73792b890",
		"group_ids": [
		"044d550bdc36426caf7f062c185c533e",
		"de56b3d20b50452cb5e440377819835f"
		],
		"id": "a84e8721a8174e7e9b69e011dceb4ba6"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| name | Name of the control object |
| description | Description for control object |
| type | Type of control object. Control object type dependes of category, there are next types for category *person*: *employee*, *contractor*, *visitor*, *other*; for category *equipment* : *excavator*, *haul*, *drill*, *dozer*, *grader*, *bus*, *water*, *blast*, *special*, *light*, *dumpcar*, *locomotive*, *other*; for category *asset*: *pump*, *generator*, *crane*, *fork lift*, *access point*, *welding*, *other*  |
| site_id | Control object site id. These IDs can be retrieved from */sites.* |
| category | Category of control object. There are next categories in system: *person*, *equipment*, *asset* |
| device_id | Id of the device connected to the control object |
| groups_ids | If object included to group, group id stores in this array of string group ids. These ids can be retrieved from */sites/:site_id/object_groups* |
| id | Inuque identifier of the control object |

---

# GET /sites/:site_id/control_objects/:object_id

Returns json data about one or all control object on specified site. If you don't set *object_id* result will contain all site control objects. To get info only about one control object you should set *object_id* in request url.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/control_objects/:object_id
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
| site_id | Yes | Control object site id. These IDs can be retrieved from */sites.* | | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| object_id | No | Object ids can be retrieved from */sites/:site_id/control_objects* Set object id to get data for one control object. | | 6470351cad3a46f8b484a92d7dcacce1 |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/control_objects/a84e8721a8174e7e9b69e011dceb4ba6
`

### Example response

```
{
	"name": "TK123",
	"description": "Haul truck",
	"type": "haul",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"category": "equipment",
	"device_id": "afbdd036a6d449bf9fef99d73792b890",
	"group_ids": [
	"044d550bdc36426caf7f062c185c533e",
	"de56b3d20b50452cb5e440377819835f"
	],
	"id": "a84e8721a8174e7e9b69e011dceb4ba6"

```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| name | Name of the control object |
| description | Description for control object |
| type | Type of control object. Control object type dependes of category, there are next types for category *person*: *employee*, *contractor*, *visitor*, *other*; for category *equipment* : *excavator*, *haul*, *drill*, *dozer*, *grader*, *bus*, *water*, *blast*, *special*, *light*, *dumpcar*, *locomotive*, *other*; for category *asset*: *pump*, *generator*, *crane*, *fork lift*, *access point*, *welding*, *other*  |
| site_id | Control object site id. These IDs can be retrieved from */sites.* |
| category | Category of control object. There are next categories in system: *person*, *equipment*, *asset* |
| device_id | Id of the device connected to the control object |
| groups_ids | If object included to group, group id stores in this array of string group ids. These ids can be retrieved from */sites/:site_id/object_groups* |
| id | Inuque identifier of the control object |

---

# POST /sites/:site_id/control_objects

Create new control object from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/control_objects
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
| site_id | Yes | Control object site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the control object | | Tim Roth, Kamaz 5511 |
| category | Yes | Category of control object. There are next categories in system: *person*, *equipment*, *asset* | | person, equipment, asset |
| type | Yes | Type of control object. Control object type dependes of category, there are next types for category *person*: *employee*, *contractor*, *visitor*, *other*; for category *equipment* : *excavator*, *haul*, *drill*, *dozer*, *grader*, *bus*, *water*, *blast*, *special*, *light*, *dumpcar*, *locomotive*, *other*; for category *asset*: *pump*, *generator*, *crane*, *fork lift*, *access point*, *welding*, *other* | | employee, bus, pump |
| description | No | Description for control object | | Haul truck |
| group_ids | No | If object included to group, group id stores in this array of string group ids. These ids can be retrieved from */sites/:site_id/object_groups* |  | ["044d550bdc36426caf7f062c185c533e", "de56b3d20b50452cb5e440377819835f"] |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Control object site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/control_objects
`

### Example Body

```
{
	"name": "New object",
	"description": "test rest",
	"type": "haul",
	"category": "equipment",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
}
```

### Example response

```
{
	"name": "New object",
	"description": "test rest",
	"type": "haul",
	"category": "equipment",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"group_ids": [],
	"id": "668cc01908324d4597de605fb90c30d0"
}
```

### Response explanation

The result is json data of new created object.

---

# PUT /sites/:site_id/control_objects/:object_id

Edit existing control object.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/control_objects/:object_id
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
| site_id | No | Control object site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | No | Name of the control object | | Tim Roth, Kamaz 5511 |
| category | No | Type of control object. There are next categories in system: *person*, *equipment*, *asset* | | person, equipment, asset |
| type | No | Type of control object. Control object type dependes of category, there are next types for category *person*: *employee*, *contractor*, *visitor*, *other*; for category *equipment* : *excavator*, *haul*, *drill*, *dozer*, *grader*, *bus*, *water*, *blast*, *special*, *light*, *dumpcar*, *locomotive*, *other*; for category *asset*: *pump*, *generator*, *crane*, *fork lift*, *access point*, *welding*, *other* | | employee, bus, pump |
| description | No | Description for control object | | Haul truck |
| group_ids | No | Array of string group ids. These ids can be retrieved from */sites/:site_id/object_groups* |  | ["044d550bdc36426caf7f062c185c533e", "de56b3d20b50452cb5e440377819835f"] |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Control object site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| object_id | No | Object ids can be retrieved from */sites/:site_id/control_objects* | | 6470351cad3a46f8b484a92d7dcacce1 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/control_objects/668cc01908324d4597de605fb90c30d0
`

### Example Body

```
{
	"name": "New object1",
	"description": "test rest1",
	"type": "employee",
	"category": "person"
}
```

### Example response

```
{
	"name": "New object1",
	"description": "test rest1",
	"type": "employee",
	"category": "person",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"group_ids": [],
	"id": "668cc01908324d4597de605fb90c30d0"
}
```

### Response explanation

The result is edited object json data.

---

# DELETE /sites/:site_id/control_objects/:object_id

Deletes existing control object.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/control_objects/:object_id
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
| site_id | Yes | Control object site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| object_id | No | Object ids can be retrieved from */sites/:site_id/control_objects* | | 6470351cad3a46f8b484a92d7dcacce1 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/control_objects/668cc01908324d4597de605fb90c30d0
`

### Example response

```
{
	"name": "New object1",
	"description": "test rest1",
	"type": "employee",
	"category": "person",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"deleted": true,
	"device_id": null,
	"perm_assign_id": null,
	"group_ids": [],
	"id": "668cc01908324d4597de605fb90c30d0"
}
```

### Response explanation

The result is data about deleted object.