Page navigation

* [Get worksite devices](#devices)
* [Get device info](#device)
* [Validate device udi](#validate-udi)
* [Create device](#new-device)
* [Update device](#edit-device)
* [Delete device](#delete-device)
* [Ping device](#ping-device)

---

# <a name="devices">GET /sites/:site_id/devices</a>

Returns json array with data about all devices on specified site.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices
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
| site_id | Yes | Device site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices
`

### Example response

```
{
	"total": 40,
	"data": [
	{
		"label": "simulated6",
		"udi": "006",
		"active": true,
		"type": "simulated",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"object_id": null,
		"create_time": "2017-08-29T13:08:49.066Z",
		"id": "203bf2fabcde4db789d9f18ce6ec8e1a"
	},
	{
		"label": "simulated14",
		"udi": "0014",
		"active": true,
		"type": "simulated",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"object_id": null,
		"create_time": "2017-08-29T13:08:50.795Z",
		"id": "26597611e56b4ed4b19d7ea7543ff710"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| label | Human readable label for device |
| udi | Unique device identifier. Setted by user, must be unique on the site. |
| active | Variable to store is device active |
| type | Type of device. There are next types in system: *unknown*, *simulated*, *iot device*, *smartphone*. If not set type while creation type will be *unknown* |
| site_id | Device site id. These IDs can be retrieved from */sites.* |
| object_id | Id of the control object related to the device |
| create_time | Time of the device creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| id | Inuque identifier of the device |

---

# <a name="device">GET /sites/:site_id/devices/:device_id</a>

Returns json data about one or all devices on specified site. If you don't set *device_id* result will contain all site devices. To get info only about one device you should set *device_id* in request url.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices/:device_id
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
| site_id | Yes | Device site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| device_id | No | Device ids can be retrieved from */sites/:site_id/devices/* Set device id to get data for one device. | | 591d23649f1b4a03b1d77861064a18ce |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices/8477b12c42a64707b5b0cc19885a00e5
`

### Example response

```
{
	"type": "simulated",
	"udi": "4567865",
	"label": "sim001",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"active": true,
	"create_time": "2017-09-28T09:21:02.016Z",
	"object_id": "2ff6d17cec174c0eafc81d6cdad95630",
	"id": "8477b12c42a64707b5b0cc19885a00e5"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| label | Human readable label for device |
| udi | Unique device identifier. Setted by user, must be unique on the site. |
| active | Variable to store is device active |
| type | Type of device. There are next types in system: *unknown*, *simulated*, *iot device*, *smartphone*. If not set type while creation type will be *unknown* |
| site_id | Device site id. These IDs can be retrieved from */sites.* |
| object_id | Id of the control object related to the device |
| create_time | Time of the device creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| id | Inuque identifier of the device |

---

# <a name="new-device">POST /sites/:site_id/devices</a>

Create new device from json string for specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices
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
| site_id | Yes | Device site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| udi | Yes | Unique device identifier. Setted by user, must be unique on the site. | | 001, abc, a1b2c3 |
| type | No | Type of device. There are next types in system: *unknown*, *simulated*, *iot device*, *smartphone*. If not set type while creation type will be *unknown* | unknown | unknown, simulated, iot device, smartphone |
| label | No | Human readable label for device | | Device01 |
| active | No | Variable to store is device active | true | true, false |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Device site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices
`

### Example Body

```
{
	"label": "New device",
	"udi": "12345",
	"active": true,
	"type": "simulated",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"object_id": "6348633470884f04aeb59122472d8c06"
}
```

### Example response

```
{
	"label": "New device",
	"udi": "12345",
	"active": true,
	"type": "simulated",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"object_id": "6348633470884f04aeb59122472d8c06",
	"create_time": "2017-11-03T11:46:12.420Z",
	"id": "390e9c7e1283408995b1d3e756eb238e"
}
```

### Response explanation

The result is json data of new created object.

---

# <a name="validate-udi">POST /sites/:site_id/devices/validate_udi</a>

Return device id for setted udi in request body. If device not found returns empty string.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices/validate_udi
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
| udi | Yes | Unique device identifier | | 001, abc, a1b2c3 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices/validate_udi
`

### Example Body

```
{
  "udi": "12345"
}
```

### Example response

```
"4f5378e1a033461bae6b51cb34538d92"
```

### Response explanation

The result is an id of finded device by udi.

---

# <a name="edit-device">PUT /sites/:site_id/devices/:device_id</a>

Edit existing device.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices/:device_id
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
| site_id | No | Device site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| udi | No | Unique device identifier. Setted by user, must be unique on the site. | | 001, abc, a1b2c3 |
| type | No | Type of device. There are next types in system: *unknown*, *simulated*, *iot device*, *smartphone*. If not set type while creation type will be *unknown* | unknown | unknown, simulated, iot device, smartphone |
| label | No | Human readable label for device | | Device01 |
| active | No | Variable to store is device active | true | true, false |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Device site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| device_id | No | Device ids can be retrieved from */sites/:site_id/devices/* | | 591d23649f1b4a03b1d77861064a18ce |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices/4f5378e1a033461bae6b51cb34538d92
`

### Example Body

```
{
	"label": "New device1",
	"udi": "123456",
	"active": false,
	"type": "unknown"
}
```

### Example response

```
{
	"udi": "123456",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"type": "unknown",
	"active": false,
	"create_time": "2017-11-03T11:59:02.541Z",
	"label": "New device1",
	"id": "4f5378e1a033461bae6b51cb34538d92"
}
```

### Response explanation

The result is edited object json data.

---

# <a name="delete-device">DELETE /sites/:site_id/devices/:device_id</a>

Deletes existing device.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices/:device_id
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
| site_id | Yes | Device site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| device_id | No | Device ids can be retrieved from */sites/:site_id/devices/* | | 591d23649f1b4a03b1d77861064a18ce |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices/4f5378e1a033461bae6b51cb34538d92
`

### Example response

```
{
"udi": "123456",
"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
"type": "unknown",
"active": false,
"create_time": "2017-11-03T11:59:02.541Z",
"label": "New device1",
"deleted": true,
"object_id": null,
"id": "4f5378e1a033461bae6b51cb34538d92"
}
```

### Response explanation

The result is data about deleted object.

---

# <a name="ping-device">POST /sites/:site_id/devices/:device_id/ping</a>

Ping existing device.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices/:device_id/ping
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

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices/6f5d31e2fcda4385a724cf34b7584437/ping
`

### Response explanation

If no errors received the ping is successfull.