Page navigation

* [Get all activities](#activities)
* [Get current activity](#activity)
* [Get activity by id](#new-activity)


---

# <a name="activities">GET /activities</a>

Returns json array with data about all activities. Activities includes all user actions like creation, changing and deleting account, signin, etc.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/activities
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

To execute this request needed system administator rules.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/activities
`

### Example response

```
{
	"total": 2698,
	"data": [
	{
		"type": "account deleted",
		"party": {
			"id": "662635fab7dc4e1c8d888e9d300e9b3a",
			"type": "account",
			"name": "new edited user"
		},
		"ref_parents": [],
		"time": "2017-11-27T15:57:46.404Z",
		"id": "2cdaa89f57c84aabb7c52418d5c90cf2"
	},
	{
		"type": "account changed",
		"party": {
			"id": "662635fab7dc4e1c8d888e9d300e9b3a",
			"type": "account",
			"name": "new edited user"
		},
		"ref_parents": [],
		"time": "2017-11-27T15:54:21.429Z",
		"id": "e0a9d56ca19f453b8c9976a05bd6eeac"
	},
	{
		"type": "account created",
		"party": {
			"id": "662635fab7dc4e1c8d888e9d300e9b3a",
			"type": "account",
			"name": "new test user"
		},
		"ref_parents": [],
		"time": "2017-11-27T15:46:33.052Z",
		"id": "22fe98759a594c199899f7111013a5b8"
	},
	{
		"type": "account created",
		"party": {
			"id": "1c20d6fd737646a8be5845c24bea1d24",
			"type": "account",
			"name": "new test user"
		},
		"ref_parents": [],
		"time": "2017-11-27T15:46:05.683Z",
		"id": "00223b985dac48be96ef7e58ddeea6b4"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|-------------|
| type | Type of the activity describes what action was perform. Can take next values *account created*, *account changed*, *account deleted*, *sign in* |
| party | Object which describes who made the activity. For users property *type* has value account, *id* is account id, *name* is account name |
| ref_parents | Array of ids references to accounts parent for activity |
| time | Time when activity happens. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| id | Activity id |

---

# <a name="activity">GET /activities/:party_id</a>

Returns json array with data about account activity.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/activities/:party_id
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

To execute this request needed system administrator role or use own *party_id*. 

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| party_id | Yes | User activity id. These IDs can be retrieved from */activities.*| | 662635fab7dc4e1c8d888e9d300e9b3a |

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/activities/662635fab7dc4e1c8d888e9d300e9b3a
`

### Example response

```
{
	"total": 3,
	"data": [
	{
		"type": "account deleted",
		"party": {
			"id": "662635fab7dc4e1c8d888e9d300e9b3a",
			"type": "account",
			"name": "new edited user"
		},
		"ref_parents": [],
		"time": "2017-11-27T15:57:46.404Z",
		"id": "2cdaa89f57c84aabb7c52418d5c90cf2"
	},
	{
		"type": "account changed",
		"party": {
			"id": "662635fab7dc4e1c8d888e9d300e9b3a",
			"type": "account",
			"name": "new edited user"
		},
		"ref_parents": [],
		"time": "2017-11-27T15:54:21.429Z",
		"id": "e0a9d56ca19f453b8c9976a05bd6eeac"
	},
	{
		"type": "account created",
		"party": {
			"id": "662635fab7dc4e1c8d888e9d300e9b3a",
			"type": "account",
			"name": "new test user"
		},
		"ref_parents": [],
		"time": "2017-11-27T15:46:33.052Z",
		"id": "22fe98759a594c199899f7111013a5b8"
	}
	],
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| type | Type of the activity describes what action was perform. Can take next values *account created*, *account changed*, *account deleted*, *sign in* |
| party | Object which describes who made the activity. For users property *type* has value account, *id* is account id, *name* is account name |
| ref_parents | Array of ids references to accounts parent for activity |
| time | Time when activity happens. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| id | Activity id |

---

# <a name="new-activity">POST /activities</a>

Create new activity from json data.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/activities
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | No |
| Requires body | Yes |

### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|

| type | Type of the activity describes what action was perform. Can take next values *account created*, *account changed*, *account deleted*, *sign in* |
| party | Object which describes who made the activity. For users property *type* has value account, *id* is account id, *name* is account name |
| ref_parents | Array of ids references to accounts parent for activity |
| time | Time when activity happens. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| id | Activity id |

### Access security 

To execuce this request needed to have system administator role.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/activities
`

### Example Body

```
{
	"type": "signin",
	"party": {
		"id": "662635fab7dc4e1c8d888e9d300e9b3a",
		"type": "account",
		"name": "new test user"
	}
}
```

### Example response

```
{
	"type": "signin",
	"party": {
		"id": "662635fab7dc4e1c8d888e9d300e9b3a",
		"type": "account",
		"name": "new test user"
	},
	"ref_parents": [],
	"time": "2017-11-27T17:58:51.741Z",
	"id": "ee5f4ac5fade4f4c932bff5e29b5895a"
}
```

### Response explanation

The request result is a new created activity json data.