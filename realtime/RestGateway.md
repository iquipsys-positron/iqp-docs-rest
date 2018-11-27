# <a name="update-status">POST /gateway/update_status</a>

Update device status by rest gateway

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/gateways/update_status
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
| time | No | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T13:07:10.676Z |
| device_udi | Unique device identifier specifies what device send state update to gateway. Device udi can be retrieved from */sites/:site_id/devices* | | 0001 |
| immobile | No | Boolean variable which indacates is device immobile | false | true, false |
| pressed | No | Boolean indicator to store is button on tracker pressed | false | true, false |
| long_pressed | No  | Boolean indicator to store is button on tracker pressed | false | true, false |
| lat | No | Latitude of the device position | | 51.29459 |
| long | No | Longtitude of the device position | | 32.29459 |
| alt | No | Altitude of the device position. Stores in meters | 200 |
| angle | No | Object azimuth, displays moving direction. Stores in degrees | 45 |
| speed | No | Object speed, stores in kilometers per hour | 55 |
| quality | No | Displayes quality of signal from tracker | 2 |

### Access security 

To execute this request needed system administator roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/gateways/update_status
`

### Example Body

```
{
	"device_udi": "9876898765678",
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
204 No content
```

### Response explanation

On successfull device state update responce is 204 no content.