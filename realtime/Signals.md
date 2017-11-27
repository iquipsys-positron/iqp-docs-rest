Page navigation

* [Get worksite all signals](#signals)
* [Create signal](#new-signal)
* [Update signals](#edit-signals)
* [Delete signal](#delete-signal)

---

# <a name="signals">GET /sites/:site_id/signals</a>

Returns json array with data about all signals on specified site.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/signals
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
| site_id | Yes | signal site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/signals
`

### Example response

```
{
	"total": 1,
	"data": [
	{
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"device_id": "32c1ac2cfdcf4f75a271a4a9ffeab04f",
		"time": "2017-11-27T11:26:40.201Z",
		"type": 1,
		"lock_until": 0,
		"sent": true,
		"id": "566fd1b6ec9d41ce9cb4966e3b64c5ff"
	}
	],
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Signal site id. These IDs can be retrieved from */sites.* |
| time | Time of the signal creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| device_id | Id of the device for signal. Device ids can be retrieved from */sites/:site_id/devices/* |
| type | Signal type can be *0* - none, *1* - attention, *2* - confirmation, *3* - warning, *4* - emergency |
| sent | Boolean value to store if signal is sended to device |
| lock_until | This variable is flag of temporary object lock, to exlude signal double processing. |
| id |  Inuque identifier of the signal |

---

# <a name="new-signals">POST /sites/:site_id/signals</a>

Creates new signal from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/signals
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
| site_id | Yes | Signal site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| time | Yes | Time of the signal creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:13:00.000Z | 
| device_id | Yes | Id of the device for signal. Device ids can be retrieved from */sites/:site_id/devices/* | | e17172ad05d448d18450aca6f6fff653 |
| type | Yes | Signal type can be *0* - none, *1* - attention, *2* - confirmation, *3* - warning, *4* - emergency | | 1 |
| sent | Yes | Boolean value to store if signal is sended to device | | false |
| lock_until | No | This variable is flag of temporary object lock, to exlude signal double processing. | 0 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/signals
`

### Example Body

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"device_id": "32c1ac2cfdcf4f75a271a4a9ffeab04f",
	"time": "2017-11-27T13:02:31.398Z",
	"type": 1,
	"sent": false,
	"lock_until": 0 
}
```

### Example response

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"device_id": "32c1ac2cfdcf4f75a271a4a9ffeab04f",
	"time": "2017-11-27T11:26:40.201Z",
	"type": 1,
	"lock_until": 0,
	"sent": true,
	"id": "566fd1b6ec9d41ce9cb4966e3b64c5ff"
}
```

### Response explanation

The result is json data of the new created signal.

---

# <a name="lock-signal">GET /sites/:site_id/signals/:signal_id/lock</a>

Lock existing signal.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/signals/:signal_id/lock
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
| site_id | Yes | signal site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| signal_id | No | signal ids can be retrieved from */sites/:site_id/signals* | | a3a6c6c4339045689ebd6fac9bc4cea1 |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/signals/566fd1b6ec9d41ce9cb4966e3b64c5ff/lock

`

### Example response

```
true
```

### Response explanation

The request result displays is signal locked. 

---

# <a name="close-signal">GET /sites/:site_id/signals/:signal_id/close</a>

Close existing signal.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/signals/:signal_id/close
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
| site_id | Yes | signal site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| signal_id | No | signal ids can be retrieved from */sites/:site_id/signals* | | 566fd1b6ec9d41ce9cb4966e3b64c5ff |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/signals/566fd1b6ec9d41ce9cb4966e3b64c5ff/close

`

### Example response

```
true
```

### Response explanation

The request result displays is signal closed. 

---

# <a name="delete-signal">DELETE /sites/:site_id/signals/:signal_id</a>

Deletes existing signal.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/signals/:signal_id
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
| site_id | Yes | signal site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| signal_id | No | signal ids can be retrieved from */sites/:site_id/signals* | | 566fd1b6ec9d41ce9cb4966e3b64c5ff |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/signals/566fd1b6ec9d41ce9cb4966e3b64c5ff
`

### Example response

```
{
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"device_id": "32c1ac2cfdcf4f75a271a4a9ffeab04f",
	"time": "2017-11-27T11:26:40.201Z",
	"type": 1,
	"lock_until": 0,
	"sent": true,
	"id": "566fd1b6ec9d41ce9cb4966e3b64c5ff"
}
```

### Response explanation

The result is json data of the deleted signal.