Page navigation

Statistics for system administator

* [Get all counters](#counters)
* [Get all groups](#groups)
* [Get all statistics values](#all-statistics-adm)
* [Get any worksite statistics](#statistics-adm)
* [Get any worksite statistics by name](#statistics-name-adm)
* [?Edit any statistics](#edit-statistics-adm)

Statistics for worksite account

* [Get worksite statistics](#statistics)
* [Get worksite statistics by name](#statistics-name)
* [?Edit statistics](#edit-statistics)

---

# <a name="counters">GET /statistics/counters</a>

Returns json data about all counters. Counters used as parameters to get statistcs data.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/statistics/counters
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
| group | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed system administator role.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/statistics/counters
`

### Example response

```
{
	"total": 4180,
	"data": [
	{
		"group": "b2b50ebdb57a4a19a6c3b7250bcbd498",
		"name": "events.74154c8e324f47f5ac25287a20f0fc64.all"
	},
	{
		"group": "b2b50ebdb57a4a19a6c3b7250bcbd498",
		"name": "params.74154c8e324f47f5ac25287a20f0fc64.immobile"
	},
	{
		"group": "b2b50ebdb57a4a19a6c3b7250bcbd498",
		"name": "params.36795c42a8e5434eaac455f4124d7a4b.speed"
	},
	{
		"group": "b2b50ebdb57a4a19a6c3b7250bcbd498",
		"name": "events.1532e2d74a154a28a9c42d486a4d1d26.all"
	},
	{
		"group": "b2b50ebdb57a4a19a6c3b7250bcbd498",
		"name": "params.1532e2d74a154a28a9c42d486a4d1d26.immobile"
	},
	{
		"group": "b2b50ebdb57a4a19a6c3b7250bcbd498",
		"name": "events.fc11b9873b5448879dfd4154a2d0bf24.bc627709c51c4b01abce939162b553f3"
	},
	{
		"group": "b2b50ebdb57a4a19a6c3b7250bcbd498",
		"name": "params.9579783351164c05a4be1e5ec7a13c03.online"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| group | Site id. These IDs can be retrieved from */sites.*|
| name | Counter name. Statistic counter contains from three part *params.<object_id>.<param_name>. Set object_id for get data for only one object, to get statistics for all objects set value to **all**. *param_name* is a name of received parameter - *online*, *immobile*, *distance*, *speed*. To receive state updates statistics and errors while updating you need to use *state_update.<device_id>* and *state_errors.<device_id>*. Instead of device_id you can use *all* for all devices statistics. |

---

# <a name="groups">GET /statistics/groups</a>

Returns json data about all groups. Groups used to specify worksite for receiving statistics.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/statistics/groups
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

To execute this request needed system administator role.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/statistics/groups
`

### Example response

```
{
	"total": 13,
	"data": [
	"b2b50ebdb57a4a19a6c3b7250bcbd498",
	"91a809841410417f8e9c38745d8ea511",
	"b185bf2974c44a709f50a3f28715f7c2",
	"0987fbb7c73a4b86b6e4d1647968fb3d",
	"a4ad733934a444d5b6ca77445d17d7c2",
	"5ac3eae28ab049869481fd19557b88d4",
	"639869d7715f4c629488ea8008b2cf7e",
	"3382613d643c47f7abd86a025b39b4dc",
	"9958f0dd1faa494fbc48ba816a02fdd0",
	"3cc4b1a29e5b4ecd9bb2a2f5d4223572",
	"dc857d9972c74dccbc3f52eb0cab985e",
	"9cfaf79bc95b4a9e912314eb3db7a4ba"
	],
}

```

### Response explanation

The request result is an array of string site ids.

---

# <a name="all-statistics-adm">POST /statistics</a>

Returns json data with all statistics values.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/statistics
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | Yes |
| Requires body | Yes |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

### Body Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| group | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed system administrator role.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/statistics
`

### Example response

```
[
{
	"type": 0,
	"values": [
	{
		"value": 34
	},
	{
		"value": 269.402
	},
	{
		"value": 1128860.0309999948
	},
	{
		"value": 205
	},
	{
		"value": 25879.52299999998
	},
	...
},
...
]
```

### Response explanation

The request result is an array of objects with statistic values.

---

# <a name="statistics-adm">GET /statistics/:group</a>

Returns json data about worksite all statistics. The statistic store values for parameters such as presence, immobile, average speed and distance for objects by hours, days and monthes. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/statistics/:group
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
| group | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed system administrator role.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/statistics/9cfaf79bc95b4a9e912314eb3db7a4ba
`

### Example response

```
[
{
	"group": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "presence.all.da2f183cbcb541b1bf74f05a3ffe8ebc",
	"type": 0,
	"values": [
	{
		"value": 894830.181999986
	}
	],
},
{
	"group": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "presence.36929eb1ee404aaa9de3114033c51386.338c32dee6a04c468a479330ad1d7acf",
	"type": 0,
	"values": [
	{
		"value": 1672296.351999974
	}
	],
},
{
	"group": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "presence.36929eb1ee404aaa9de3114033c51386.da2f183cbcb541b1bf74f05a3ffe8ebc",
	"type": 0,
	"values": [
	{
		"value": 804247.6119999944
	}
	],
},
...
]
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| group | Site id. These IDs can be retrieved from */sites.*|
| name | Statistic counter contains from three part *params.<object_id>.<param_name>. Set object_id for get data for only one object, to get statistics for all objects set value to **all**. *param_name* is a name of received parameter - *online*, *immobile*, *distance*, *speed*. To receive state updates statistics and errors while updating you need to use *state_update.<device_id>* and *state_errors.<device_id>*. Instead of device_id you can use *all* for all devices statistics. |
| type | Each counter have type, there are next types - hour, day, week, month and year. Type is a request url parameter and can take next value - **0**: Total, **1**: Year, **2**: Month, **3**: Day, **4**: Hour. |
| values | Array of objects values. If type not total then each object have filed *year*, *month*, *day*, *hour* for storing date and hour and *value*. Value stores in seconds or meters depends on what parameter you asked. | 

---

# <a name="statistics-name-adm">GET /statistics/:group/:name</a>

Returns json data about worksite statistics. The statistic store values for parameters such as presence, immobile, average speed and distance. Data stores with specific counter name, wich defines parameter and object. Each counter have type, there are next types - hour, day, week, month and year. Type is a request url parameter and can take next value - **0**: Total, **1**: Year, **2**: Month, **3**: Day, **4**: Hour.

To get data for specified date you have to set url parameter *from_time* and *to_time*. This parameter have datetime format yyyy-MM-ddTHH:mm:ss.fffZ and has to be sended in site timezone. With these parameters you have also set site *timezone* url parameter.

The result values for distance return in meters, for presence and imobile in seconds.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/statistics/:group/:name
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
| group | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Statistic counter contains from three part *params.<object_id>.<param_name>. Set object_id for get data for only one object, to get statistics for all objects set value to **all**. *param_name* is a name of received parameter - *online*, *immobile*, *distance*, *speed*. To receive state updates statistics and errors while updating you need to use *state_update.<device_id>* and *state_errors.<device_id>*. Instead of device_id you can use *all* for all devices statistics. | | presence.36929eb1ee404aaa9de3114033c51386.338c32dee6a04c468a479330ad1d7acf |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

```
 GET http://tracker.pipservices.net:8080/api/v1/statistics/9cfaf79bc95b4a9e912314eb3db7a4ba/params.all.distance?from_time=2017-11-22T22:00:00.000Z&timezone=Asia%2FBeirut&to_time=2017-11-23T21:59:00.000Z&type=4
```

### Example response

```
{
	"group": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "params.all.distance",
	"type": 4,
	"values": [
	{
		"year": 2017,
		"month": 11,
		"day": 23,
		"hour": 0,
		"value": 228658.61623147537
	},
	{
		"year": 2017,
		"month": 11,
		"day": 23,
		"hour": 1,
		"value": 198108.52903203486
	},
	{
		"year": 2017,
		"month": 11,
		"day": 23,
		"hour": 2,
		"value": 182708.35893691206
	},
	{
		"year": 2017,
		"month": 11,
		"day": 23,
		"hour": 3,
		"value": 197958.12618555035
	},
	{
		"year": 2017,
		"month": 11,
		"day": 23,
		"hour": 4,
		"value": 191448.47637147532
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| group | Site id. These IDs can be retrieved from */sites.*|
| name | Statistic counter contains from three part *params.<object_id>.<param_name>. Set object_id for get data for only one object, to get statistics for all objects set value to **all**. *param_name* is a name of received parameter - *online*, *immobile*, *distance*, *speed*. To receive state updates statistics and errors while updating you need to use *state_update.<device_id>* and *state_errors.<device_id>*. Instead of device_id you can use *all* for all devices statistics. |
| type | Each counter have type, there are next types - hour, day, week, month and year. Type is a request url parameter and can take next value - **0**: Total, **1**: Year, **2**: Month, **3**: Day, **4**: Hour. |
| values | Array of objects values. If type not total then each object have filed *year*, *month*, *day*, *hour* for storing date and hour and *value*. Value stores in seconds or meters depends on what parameter you asked. | 

---

# <a name="statistics">GET /sites/:group/statistics</a>

Returns json data about worksite all statistics. The statistic store values for parameters such as presence, immobile, average speed and distance for objects by hours, days and monthes. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:group/statistics
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
| group | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/statistics
`

### Example response

```
[
{
	"group": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "presence.all.da2f183cbcb541b1bf74f05a3ffe8ebc",
	"type": 0,
	"values": [
	{
		"value": 894830.181999986
	}
	],
},
{
	"group": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "presence.36929eb1ee404aaa9de3114033c51386.338c32dee6a04c468a479330ad1d7acf",
	"type": 0,
	"values": [
	{
		"value": 1672296.351999974
	}
	],
},
{
	"group": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "presence.36929eb1ee404aaa9de3114033c51386.da2f183cbcb541b1bf74f05a3ffe8ebc",
	"type": 0,
	"values": [
	{
		"value": 804247.6119999944
	}
	],
},
...
]
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| group | Site id. These IDs can be retrieved from */sites.*|
| name | Statistic counter contains from three part *params.<object_id>.<param_name>. Set object_id for get data for only one object, to get statistics for all objects set value to **all**. *param_name* is a name of received parameter - *online*, *immobile*, *distance*, *speed*. To receive state updates statistics and errors while updating you need to use *state_update.<device_id>* and *state_errors.<device_id>*. Instead of device_id you can use *all* for all devices statistics. |
| type | Each counter have type, there are next types - hour, day, week, month and year. Type is a request url parameter and can take next value - **0**: Total, **1**: Year, **2**: Month, **3**: Day, **4**: Hour. |
| values | Array of objects values. If type not total then each object have filed *year*, *month*, *day*, *hour* for storing date and hour and *value*. Value stores in seconds or meters depends on what parameter you asked. | 

---

# <a name="statistics-name">GET /sites/:group/statistics/:name</a>

Returns json data about worksite statistics . The statistic store values for parameters such as presence, immobile, average speed and distance. Data stores with specific counter name, wich defines parameter and object. Each counter have type, there are next types - hour, day, week, month and year. Type is a request url parameter and can take next value - **0**: Total, **1**: Year, **2**: Month, **3**: Day, **4**: Hour.

To get data for specified date you have to set url parameter *from_time* and *to_time*. This parameter have datetime format yyyy-MM-ddTHH:mm:ss.fffZ and has to be sended in site timezone. With these parameters you have also set site *timezone* url parameter.

The result values for distance return in meters, for presence and imobile in seconds.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:group/statistics/:name
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
| group | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| name | Yes | Statistic counter contains from three part *params.<object_id>.<param_name>. Set object_id for get data for only one object, to get statistics for all objects set value to **all**. *param_name* is a name of received parameter - *online*, *immobile*, *distance*, *speed*. To receive state updates statistics and errors while updating you need to use *state_update.<device_id>* and *state_errors.<device_id>*. Instead of device_id you can use *all* for all devices statistics. | | presence.36929eb1ee404aaa9de3114033c51386.338c32dee6a04c468a479330ad1d7acf |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

```
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/statistics/params.all.distance?from_time=2017-11-22T22:00:00.000Z&timezone=Asia%2FBeirut&to_time=2017-11-23T21:59:00.000Z&type=4
```

### Example response

```
{
	"group": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"name": "params.all.distance",
	"type": 4,
	"values": [
	{
		"year": 2017,
		"month": 11,
		"day": 23,
		"hour": 0,
		"value": 228658.61623147537
	},
	{
		"year": 2017,
		"month": 11,
		"day": 23,
		"hour": 1,
		"value": 198108.52903203486
	},
	{
		"year": 2017,
		"month": 11,
		"day": 23,
		"hour": 2,
		"value": 182708.35893691206
	},
	{
		"year": 2017,
		"month": 11,
		"day": 23,
		"hour": 3,
		"value": 197958.12618555035
	},
	{
		"year": 2017,
		"month": 11,
		"day": 23,
		"hour": 4,
		"value": 191448.47637147532
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| group | Site id. These IDs can be retrieved from */sites.*|
| name | Statistic counter contains from three part *params.<object_id>.<param_name>. Set object_id for get data for only one object, to get statistics for all objects set value to **all**. *param_name* is a name of received parameter - *online*, *immobile*, *distance*, *speed*. To receive state updates statistics and errors while updating you need to use *state_update.<device_id>* and *state_errors.<device_id>*. Instead of device_id you can use *all* for all devices statistics. |
| type | Each counter have type, there are next types - hour, day, week, month and year. Type is a request url parameter and can take next value - **0**: Total, **1**: Year, **2**: Month, **3**: Day, **4**: Hour. |
| values | Array of objects values. If type not total then each object have filed *year*, *month*, *day*, *hour* for storing date and hour and *value*. Value stores in seconds or meters depends on what parameter you asked. | 

---

# TO DO: <a name="editstatistics">POST /sites/:grop/statistics/:name</a>