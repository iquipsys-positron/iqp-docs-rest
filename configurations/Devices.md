## Get site devices

# GET /sites/:site_id/devices

Returns json array with data about all devices on specified site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices
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
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices
`

# Example Responce

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

---

## Get device info

# GET /sites/:site_id/devices/:device_id

Returns json data about one or all devices on specified site. If you don't set *device_id* result will contain all site devices. To get info only about one device you should set *device_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices/:device_id
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
| device_id | No | Device ids can be retrieved from */sites/:site_id/devices/* Set device id to get data for one device. | | 591d23649f1b4a03b1d77861064a18ce |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices/8477b12c42a64707b5b0cc19885a00e5
`

# Example Responce

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

---

## Create device

# POST /sites/:site_id/devices

Creates new device from json string for specified site. 

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices
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
| udi | Yes | Unique device identifier. Setted by user, must be unique on the site. | | 001, abc, a1b2c3 |
| type | No | Type of device. There are next types in system: *unknown*, *simulated*, *iot device*, *smartphone*. If not set type while creation type will be *unknown* | unknown | unknown, simulated, iot device, smartphone |
| label | No | Human readable label for device | | Device01 |
| active | No | Variable to store is device active | true | true, false |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices
`

# Example Body

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

# Example Responce

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

---

## Get device id by device udi

# POST /sites/:site_id/devices/validate_udi

Return device id for setted udi in request body. If device not found returns empty string.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices/validate_udi
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
| udi | Yes | Unique device identifier | | 001, abc, a1b2c3 |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices/validate_udi
`

# Example Body

```
{
  "udi": "12345"
}
```

# Example Responce

```
"4f5378e1a033461bae6b51cb34538d92"
```

---

## Edit device

# PUT /sites/:site_id/devices/:device_id

Edit existing device.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices/:device_id
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
| udi | No | Unique device identifier. Setted by user, must be unique on the site. | | 001, abc, a1b2c3 |
| type | No | Type of device. There are next types in system: *unknown*, *simulated*, *iot device*, *smartphone*. If not set type while creation type will be *unknown* | unknown | unknown, simulated, iot device, smartphone |
| label | No | Human readable label for device | | Device01 |
| active | No | Variable to store is device active | true | true, false |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| device_id | No | Device ids can be retrieved from */sites/:site_id/devices/* Set device id to get data for one device. | | 591d23649f1b4a03b1d77861064a18ce |

# Example Request

`
 PUT http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices/4f5378e1a033461bae6b51cb34538d92
`

# Example Body

```
{
  "label": "New device1",
  "udi": "123456",
  "active": false,
  "type": "unknown"
}
```

# Example Responce

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

---

## Delete device

# DELETE /sites/:site_id/devices/:device_id

Deletes existing device.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices/:device_id
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
| device_id | No | Device ids can be retrieved from */sites/:site_id/devices/* Set device id to get data for one device. | | 591d23649f1b4a03b1d77861064a18ce |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices/4f5378e1a033461bae6b51cb34538d92
`

# Example Responce

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

---

## TO DO : ping device

## Ping device

# POST /sites/:site_id/devices/:device_id/ping

Ping existing device.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/devices/:device_id/ping
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

- ### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| | | | | |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/devices/6f5d31e2fcda4385a724cf34b7584437/ping
`

# Example Responce

```

```