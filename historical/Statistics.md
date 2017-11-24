# GET /sites/:group/statistics

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
| name | Statistic counter contains from three part *params.<object_id>.<param_name>. Set object_id for get data for only one object, to get statistics for all objects set value to **all**. *param_name* is a name of received parameter - *online*, *immobile*, *distance*, *speed*. |
| type | Each counter have type, there are next types - hour, day, week, month and year. Type is a request url parameter and can take next value - **0**: Total, **1**: Year, **2**: Month, **3**: Day, **4**: Hour. |
| values | Array of objects values. If type not total then each object have filed *year*, *month*, *day*, *hour* for storing date and hour and *value*. Value stores in seconds or meters depends on what parameter you asked. | 

---

# GET /sites/:group/statistics/:name

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
| name | Yes | Statistic counter contains from three part *params.<object_id>.<param_name>. Set object_id for get data for only one object, to get statistics for all objects set value to **all**. *param_name* is a name of received parameter - *online*, *immobile*, *distance*, *speed*. | | presence.36929eb1ee404aaa9de3114033c51386.338c32dee6a04c468a479330ad1d7acf |

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
| name | Statistic counter contains from three part *params.<object_id>.<param_name>. Set object_id for get data for only one object, to get statistics for all objects set value to **all**. *param_name* is a name of received parameter - *online*, *immobile*, *distance*, *speed*. |
| type | Each counter have type, there are next types - hour, day, week, month and year. Type is a request url parameter and can take next value - **0**: Total, **1**: Year, **2**: Month, **3**: Day, **4**: Hour. |
| values | Array of objects values. If type not total then each object have filed *year*, *month*, *day*, *hour* for storing date and hour and *value*. Value stores in seconds or meters depends on what parameter you asked. | 


---

# TO DO: post /sites/:grop/statistics/:name 