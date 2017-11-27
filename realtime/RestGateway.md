# <a name="update-status">POST /gateway/update_status</a>

Update device status by rest gateway

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/gateways/update_status
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


### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/gateways/update_status
`

### Example Body

```
{
	"site_id": "9958f0dd1faa494fbc48ba816a02fdd0",
	"device_udi": "9876898765678",
	"time": "2017-11-27T13:02:31.398Z",
	"immobile": false,
	"long": 37.640559,
	"lat": 51.299172, 
	"alt": 200,
	"angle": 45,
	"speed": 50,
	"quality": 2
}
```

### Example response

```

```

### Response explanation



---