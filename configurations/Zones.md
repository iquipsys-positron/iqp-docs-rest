# GET /sites/:site_id/zones

Returns json array with data about all zones on specified site. There is different zone types - line, circle and polygone for geo zone and object zone.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/zones
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
| site_id | Yes | Zone site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/zones
`

### Example response

```
{
	"total": 20,
	"data": [
	{
		"distance": 243.85110001288226,
		"name": "East dump zone",
		"type": "circle",
		"geometry": {
			"type": "Polygon",
			"coordinates": [
			[
			30.694127082824703,
			64.69643769543671
			],
			[
			30.697142885338184,
			64.69601883796147
			],
			...
			],
		},
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"boundaries": {
			"type": "Polygon",
			"coordinates": [
			[
			[
			30.689247609373155,
			64.69205168417933
			],,
			[
			30.699006556276252,
			64.69643769543671
			],
			],
			],
		},
		"center": {
			"type": "Point",
			"coordinates": [
			30.694127082824707,
			64.69424468980802
			],
		},
		"exclude_group_ids": [],
		"exclude_object_ids": [],
		"include_group_ids": [],
		"include_object_ids": [],
		"id": "caef7aeb8b80489aa1f0aab8644f58d2"
	},
	{
		"name": "Excavator zone",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"type": "object",
		"distance": 10,
		"geometry": null,
		"exclude_group_ids": [],
		"exclude_object_ids": [],
		"include_group_ids": [
		"4dfb98d581a34d5e9cc5887335ddcc1b"
		],
		"include_object_ids": [],
		"id": "338c32dee6a04c468a479330ad1d7acf"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| name |  Name of the zone |
| site_id | Zone site id. These IDs can be retrieved from */sites.* |
| distance | For linear zone distance is line width, for circle zones distance is circle radius, for polygon zones distance not nesessery. Stores as number. |
| geometry | Geometry of zone. It stores in geoJSON format. Object with property *type* = LineString for linear zones and Polygon for others; and *coordinates* with array longtitude latitude pair. |
| center | Needed just for circle zones. This is zone center, it stores in geoJSON point format. Object with properties *type* and *coordinates* with array longtitude latitude pair.  |
| boundaries | Automaticaly generated from center and radius boundaries object. |
| type | Type of zone. There are *object* zone types for object zones and next geo zone types: *line*, *circle*, *polygon* for geo zones |
| exclude_group_ids | Array of group ids which is included to this zone. These ids can be retrieved from */sites/:site_id/groups* |
| exclude_object_ids | Array of objects ids which is included to this zone. These ids can be retrieved from */sites/:site_id/control_objects* |
| include_group_ids | Array of group ids which is excluded from this zone. These ids can be retrieved from */sites/:site_id/groups* |
| include_object_ids | Array of objects ids which is excluded from this zone. These ids can be retrieved from */sites/:site_id/control_objects* |
| id |  Inuque identifier of the zone |

---

# GET /sites/:site_id/zones/:zone_id

Returns json data about one or all zone on specified site. If you don't set *zone_id* result will contain all site zones. To get info only about one zone you should set *zone_id* in request url.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/zones/:zone_id
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
| site_id | Yes | Zone site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| zone_id | No | zone ids can be retrieved from */sites/:site_id/zones* Set zone id to get data for one zone. | | 338c32dee6a04c468a479330ad1d7acf |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/zones/338c32dee6a04c468a479330ad1d7acf
`

### Example response

```
{
	"name": "Excavator zone",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"type": "object",
	"distance": 10,
	"geometry": null,
	"exclude_group_ids": [],
	"exclude_object_ids": [],
	"include_group_ids": [
	"4dfb98d581a34d5e9cc5887335ddcc1b"
	],
	"include_object_ids": [],
	"id": "338c32dee6a04c468a479330ad1d7acf"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| name |  Name of the zone |
| site_id | Zone site id. These IDs can be retrieved from */sites.* |
| distance | For linear zone distance is line width, for circle zones distance is circle radius, for polygon zones distance not nesessery. Stores as number. |
| geometry | Geometry of zone. It stores in geoJSON format. Object with property *type* = LineString for linear zones and Polygon for others; and *coordinates* with array longtitude latitude pair. |
| center | Needed just for circle zones. This is zone center, it stores in geoJSON point format. Object with properties *type* and *coordinates* with array longtitude latitude pair.  |
| boundaries | Automaticaly generated from center and radius boundaries object. |
| type | Type of zone. There are *object* zone types for object zones and next geo zone types: *line*, *circle*, *polygon* for geo zones |
| exclude_group_ids | Array of group ids which is included to this zone. These ids can be retrieved from */sites/:site_id/groups* |
| exclude_object_ids | Array of objects ids which is included to this zone. These ids can be retrieved from */sites/:site_id/control_objects* |
| include_group_ids | Array of group ids which is excluded from this zone. These ids can be retrieved from */sites/:site_id/groups* |
| include_object_ids | Array of objects ids which is excluded from this zone. These ids can be retrieved from */sites/:site_id/control_objects* |
| id |  Inuque identifier of the zone |

---

# POST /sites/:site_id/zones

Create new zone from json string for specified site. The coordinates format depends on zone type, make sure that you use correct format for coordinates array using GeoJSON.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/zones
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
| site_id | Yes | Zone site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the zone | | Work zone, Special equipment zone |
| type | Yes | Type of zone. There are *object* zone types for object zones and next geo zone types: *line*, *circle*, *polygon* for geo zones | | line, object, circle, polygon |
| geometry| | Geometry of zone. It stores in geoJSON format. Object with property *type* = LineString for linear zones and Polygon for others; and *coordinates* with array longtitude latitude pair. | | {"type": "Polygon", "coordinates": [ [ [ 30.694127082824703, 64.69643769543671 ],, [ 30.697142885338184, 64.69601883796147 ],, [ [ 30.691111280311226, 64.69601883796147 ], ], ], } |
| distance | |  For linear zone distance is line width, for circle zones distance is circle radius, for polygon zones distance not nesessery. Stores as number. | | 10, 15.498 |
| center | | Needed just for circle zones. This is zone center, it stores in geoJSON point format. Object with properties *type* and *coordinates* with array longtitude latitude pair.  | | { "type": "Point", "coordinates": [ 30.694127082824707, 64.69424468980802 ], } |
| exclude_group_ids | | Array of group ids which is included to this zone. These ids can be retrieved from */sites/:site_id/groups* | | ["4dfb98d581a34d5e9cc5887335ddcc1b"] |
| exclude_object_ids | | Array of objects ids which is included to this zone. These ids can be retrieved from */sites/:site_id/control_objects* | | ["841abccea54d47bd87b04195764a859b"] |
| include_group_ids | | Array of group ids which is excluded from this zone. These ids can be retrieved from */sites/:site_id/groups* | | ["4dfb98d581a34d5e9cc5887335ddcc1b"] |
| include_object_ids | | Array of objects ids which is excluded from this zone. These ids can be retrieved from */sites/:site_id/control_objects* | | ["841abccea54d47bd87b04195764a859b"] |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Zone site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/zones
`

### Example Body

```
{
  "name": "New zone",
  "site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
  "type": "object",
  "distance": 10,
  "geometry": null,
  "exclude_group_ids": [],
  "exclude_object_ids": [],
  "include_group_ids": [
    "4dfb98d581a34d5e9cc5887335ddcc1b"
  ],
  "include_object_ids": []
}
```

### Example response

```
{
	"name": "New zone",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"type": "object",
	"distance": 10,
	"geometry": null,
	"exclude_group_ids": [],
	"exclude_object_ids": [],
	"include_group_ids": [
	"4dfb98d581a34d5e9cc5887335ddcc1b"
	],
	"include_object_ids": [],
	"id": "0de21f52892641c9b3021ff88f304fb8"
}
```

### Response explanation

The result is json data of the new created object.

---

# PUT /sites/:site_id/zones/:zone_id

Edit existing zone.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/zones/:zone_id
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
| site_id | Yes | Zone site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Name of the zone | | Work zone, Special equipment zone |
| type | Yes | Type of zone. There are *object* zone types for object zones and next geo zone types: *line*, *circle*, *polygon* for geo zones | | line, object, circle, polygon |
| geometry | Yes (geo zones) / No (object zones) | Geometry of zone. It stores in geoJSON format. Object with property *type* = LineString for linear zones and Polygon for others; and *coordinates* with array longtitude latitude pair. | No | {"type": "Polygon", "coordinates": [ [ [ 30.694127082824703, 64.69643769543671 ],, [ 30.697142885338184, 64.69601883796147 ],, [ [ 30.691111280311226, 64.69601883796147 ], ], ], } |
| distance | No |  For linear zone distance is line width, for circle zones distance is circle radius, for polygon zones distance not nesessery. Stores as number. | | 10, 15.498 |
| center | No | Needed just for circle zones. This is zone center, it stores in geoJSON point format. Object with properties *type* and *coordinates* with array longtitude latitude pair.  | | { "type": "Point", "coordinates": [ 30.694127082824707, 64.69424468980802 ], } |
| exclude_group_ids | No | Array of group ids which is included to this zone. These ids can be retrieved from */sites/:site_id/groups* | | ["4dfb98d581a34d5e9cc5887335ddcc1b"] |
| exclude_object_ids | No | Array of objects ids which is included to this zone. These ids can be retrieved from */sites/:site_id/control_objects* | | ["841abccea54d47bd87b04195764a859b"] |
| include_group_ids | No | Array of group ids which is excluded from this zone. These ids can be retrieved from */sites/:site_id/groups* | | ["4dfb98d581a34d5e9cc5887335ddcc1b"] |
| include_object_ids | No | Array of objects ids which is excluded from this zone. These ids can be retrieved from */sites/:site_id/control_objects* | | ["841abccea54d47bd87b04195764a859b"] |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Zone site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| zone_id | No | zone ids can be retrieved from */sites/:site_id/zones* | | 338c32dee6a04c468a479330ad1d7acf |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/zones/0de21f52892641c9b3021ff88f304fb8
`

### Example Body

```
{
	"name": "New zone1",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"distance": 15
}
```

### Example response

```
{
	"name": "New zone1",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"type": "object",
	"distance": 15,
	"geometry": null,
	"exclude_group_ids": [],
	"exclude_object_ids": [],
	"include_group_ids": [
	"4dfb98d581a34d5e9cc5887335ddcc1b"
	],
	"include_object_ids": [],
	"id": "0de21f52892641c9b3021ff88f304fb8"
}
```

### Response explanation

The result is json data of the edited object.

---

# DELETE /sites/:site_id/zones/:zone_id

Deletes existing zone.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/zones/:zone_id
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
| site_id | Yes | Zone site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| zone_id | No | zone ids can be retrieved from */sites/:site_id/zones* | | 338c32dee6a04c468a479330ad1d7acf |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/zones/0de21f52892641c9b3021ff88f304fb8
`

### Example response

```
{
	"name": "New zone1",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"type": "object",
	"distance": 15,
	"geometry": null,
	"exclude_group_ids": [],
	"exclude_object_ids": [],
	"include_group_ids": [
	"4dfb98d581a34d5e9cc5887335ddcc1b"
	],
	"include_object_ids": [],
	"id": "0de21f52892641c9b3021ff88f304fb8"
}
```

### Response explanation

The result is json data of the deleted object.