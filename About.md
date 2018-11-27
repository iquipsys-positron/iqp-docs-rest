
# GET /about

Returns json array with data about server and client.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/about
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | No |

### Access security 

Anybody can execute this request.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/about
`

### Example response

```
{
	"server": {
		"name": "iqs-facade-node",
		"description": "Client facade for iQuipsys Tracker (stage)",
		"properties": {},
		"uptime": 97169944,
		"start_time": "2017-11-27T07:50:37.964Z",
		"current_time": "2017-11-28T10:50:07.908Z",
		"protocol": "http",
		"host": "tracker.pipservices.net",
		"addresses": [
		"172.31.23.77",
		"172.17.0.1"
		],
		"port": 8080,
		"url": "/api/v1/about"
	},
	"client": {
		"address": "::ffff:109.254.10.81",
		"client": "unknown",
		"platform": "unknown",
		"user": {
			"id": "cd65c2023be34e84b2e9529264d17d21",
			"name": "Dmitriy Krainiy",
			"login": "krdima92@gmail.com",
			"create_time": "2017-08-08T08:12:38.736Z",
			"language": "ru",
			"theme": "iqt-main",
			"roles": [...],
			"sites": [...],
			"settings": {...},
			"change_pwd_time": null
		}
	}
}
```

### Response explanation

The request result is an object with info about server and client data.