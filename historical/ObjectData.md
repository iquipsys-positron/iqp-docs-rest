Page navigation

* [Get worksite object data](#object-data)
* [Create object data](#new-object-data)
* [Create object data batch](#new-object-data-batch)
* [Delete object data](#delete-object-data)

---

# <a name="object-data">GET /sites/:site_id/object_data</a>

Returns json data about worksite all object data.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/object_data
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
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_data
`

### Example response

```
{
    "total": 185,
    "data": [
        {
            "object_id": "04a6e95fe43545418b2345a9fdaa742f",
            "site_id": "3bdd0757ac2b416093fa87f92df31bd6",
            "end_time": "2018-11-26T13:15:00.000Z",
            "values": [
                {
                    "time": "2018-11-26T13:12:59.736Z",
                    "states": [],
                    "commands": null,
                    "events": null,
                    "params": [
                        {
                            "id": 1,
                            "typ": null,
                            "val": 4
                        },
                        {
                            "id": 2,
                            "typ": null,
                            "val": 4
                        },
                        {
                            "id": 3,
                            "typ": null,
                            "val": 4
                        },
                        {
                            "id": 4,
                            "typ": null,
                            "val": 4
                        },
                        {
                            "id": 5,
                            "typ": null,
                            "val": 4
                        },
                        {
                            "id": 6,
                            "typ": null,
                            "val": 4
                        },
                        {
                            "id": 7,
                            "typ": null,
                            "val": 4
                        },
                        {
                            "id": 8,
                            "typ": null,
                            "val": 4
                        },
                        {
                            "id": 9,
                            "typ": null,
                            "val": 4
                        }
                    ]
                },
                ...
            ]
        }
    ]
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Site id. These IDs can be retrieved from */sites.*|
| start_time | data stored for 15 minutes time interval. This variable stores time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| end_time | data stored for 15 minutes time interval. This variable stores time of the time interval ending. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| object_id | Object ids can be retrieved from */sites/:site_id/control_objects/* | 
| values | Array of objects structure described below| 
| time | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| states | Array of device data states | 
| commands | Array of device data commands. Commdands is signals for hardware device |
| events | Array of device data events. Events is current temporary states of device, for example - button press. |
| params | Array of device data params. Params is device sensor data, for example - immobility, powered or any other sensor data |

---

# <a name="new-object-data">POST /sites/:site_id/object_data</a>

Create new object data from json string for specified site. 

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/object_data
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
| site_id | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| start_time | data stored for 15 minutes time interval. This variable stores time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:00:00.000Z |
| end_time | data stored for 15 minutes time interval. This variable stores time of the time interval ending. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T20:00:00.000Z |
| object_id | Object ids can be retrieved from */sites/:site_id/control_objects/* |  | e17172ad05d448d18450aca6f6fff653 |
| values | Array of objects structure described below | | |
| time | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:00:00.000Z |
| states | Array of device data states | | [ { "id": 1, "val": 1 }] |
| commands | Array of device data commands. Commdands is signals for hardware device | | [ { "id": 1, "val": 1 } ] |
| events | Array of device data events. Events is current temporary states of device, for example - button press. | | [ { "id": 1, "val": 1 } ] |
| params | Array of device data params. Params is device sensor data, for example - immobility, powered or any other sensor data | [ { "id": 1, "val": 1 } ]

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_data
`

### Example Body

```
{
    "object_id": "04a6e95fe43545418b2345a9fdaa742f",
    "site_id": "3bdd0757ac2b416093fa87f92df31bd6",
    "end_time": "2018-11-26T13:15:00.000Z",
    "values": [
        {
            "time": "2018-11-26T13:12:59.736Z",
            "states": [],
            "commands": null,
            "events": null,
            "params": [
                {
                    "id": 1,
                    "typ": null,
                    "val": 4
                },
                {
                    "id": 2,
                    "typ": null,
                    "val": 4
                },
                {
                    "id": 3,
                    "typ": null,
                    "val": 4
                },
                {
                    "id": 4,
                    "typ": null,
                    "val": 4
                },
                {
                    "id": 5,
                    "typ": null,
                    "val": 4
                },
                {
                    "id": 6,
                    "typ": null,
                    "val": 4
                },
                {
                    "id": 7,
                    "typ": null,
                    "val": 4
                },
                {
                    "id": 8,
                    "typ": null,
                    "val": 4
                },
                {
                    "id": 9,
                    "typ": null,
                    "val": 4
                }
            ]
        },
        ...
    ]
}
```

### Example response

```
No content
```

---


# <a name="new-object-data-batch">POST /sites/:site_id/data/batch</a>

Batch insert for object states from json string for specified site. Create multple object states at one request for sended array of object states.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/object_states/batch
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
| site_id | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| start_time | data stored for 15 minutes time interval. This variable stores time of the time interval begining. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:00:00.000Z |
| end_time | data stored for 15 minutes time interval. This variable stores time of the time interval ending. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T20:00:00.000Z |
| object_id | Object ids can be retrieved from */sites/:site_id/control_objects/* |  | e17172ad05d448d18450aca6f6fff653 |
| values | Array of objects structure described below | | |
| time | Object state time. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ | | 2017-11-21T18:00:00.000Z |
| states | Array of device data states | | [ { "id": 1, "val": 1 }] |
| commands | Array of device data commands. Commdands is signals for hardware device | | [ { "id": 1, "val": 1 } ] |
| events | Array of device data events. Events is current temporary states of device, for example - button press. | | [ { "id": 1, "val": 1 } ] |
| params | Array of device data params. Params is device sensor data, for example - immobility, powered or any other sensor data | [ { "id": 1, "val": 1 } ]

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_data/batch
`

### Example Body

```
[
    {
    "object_id": "04a6e95fe43545418b2345a9fdaa742f",
    "site_id": "3bdd0757ac2b416093fa87f92df31bd6",
    "end_time": "2018-11-26T13:15:00.000Z",
    "values": [
        {
            "time": "2018-11-26T13:12:59.736Z",
            "states": [],
            "commands": null,
            "events": null,
            "params": [
                {
                    "id": 1,
                    "typ": null,
                    "val": 4
                },
                {
                    "id": 2,
                    "typ": null,
                    "val": 4
                },
                ...
            ]
        },
        ...
    ]
    },
    {
    "object_id": "04a6e95fe43545418b2345a9fdaa742f",
    "site_id": "3bdd0757ac2b416093fa87f92df31bd6",
    "end_time": "2018-11-26T13:15:00.000Z",
    "values": [
        {
            "time": "2018-11-26T13:12:59.736Z",
            "states": [],
            "commands": null,
            "events": null,
            "params": [
                {
                    "id": 1,
                    "typ": null,
                    "val": 4
                },
                {
                    "id": 2,
                    "typ": null,
                    "val": 4
                },
                ...
            ]
        },
        ...
    ]
    }
]
```

### Example response

```
No content
```

---

# <a name="delete-object-data">DELETE /sites/:site_id/object_data</a>

Delete all object data on specified worksite.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/object_data
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
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 DELETE http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/object_data
`

### Example response

```
No content
```