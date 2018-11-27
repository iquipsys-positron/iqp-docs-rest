Page navigation

* [Get worksite users](#users)
* [Connect to demo site](#connect-demo)
* [Connect to worksite by site_id](#connect-by-id)
* [Disconnect from worksite](#disconnect)

---

# <a name="users">GET /sites/:site_id/users</a>

Returns json array with data about all site users.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/users
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
 GET http://api.positron.iquipsys.net:30018/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/users
`

### Example response

```
{
	"total": null,
	"data": [
	{
		"name": "invited user",
		"login": "dimongaga@gmail.com",
		"language": "en",
		"theme": "default",
		"time_zone": null,
		"active": true,
		"create_time": "2017-11-16T09:04:10.570Z",
		"id": "0984f44cbc6648b0b23d955f9d964c2f",
		"roles": [
		"9cfaf79bc95b4a9e912314eb3db7a4ba:admin"
		],
	},
	{
		"name": "test_stas@rambler.ru",
		"login": "test_stas@rambler.ru",
		"language": "en",
		"theme": "default",
		"time_zone": null,
		"active": true,
		"create_time": "2017-11-15T12:29:32.371Z",
		"id": "e7e91e7b20d24b579e0e865b46d5fe70",
		"roles": [
		"9cfaf79bc95b4a9e912314eb3db7a4ba:user",
		"0d3ab508e7c742efaf5393a423afdd63:admin"
		],
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| name | User name |
| login | User login |
| language | User interface language |
| theme | User interface theme. Can be *default* or *accent*  |
| time_zone | User time zone, can be null. Stores as string with timezone name. |
| active | Stores is user account active |
| create_time | Time of the gateway creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| roles | All user roles. Roles is array of strings, each string is a role for some site. Roles have following structure "<site_id>:<role>". *site_id* can be retrieved from */sites.*, *role* can take next values: *user*, *manager*, *admin*. System administrator have role **admin** without site_id. |
| id | Inuque identifier of the user account |

---

# <a name="connect-demo">POST /sites/demo/roles</a>

Connect user with id sended in post body as user_id to demo worksite. As response returns demo site id.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/demo/roles
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
| user_id | Yes | User with this id will be connected to demo site. User id's can be retrieved from */accounts.*| | cd65c2023be34e84b2e9529264d17d21 |

### Access security 

To execute this request needed to be signed user.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/demo/roles
`

### Example Body

```
{ 
    "user_id": "cd65c2023be34e84b2e9529264d17d21"
}
```

### Example response

```
"9cfaf79bc95b4a9e912314eb3db7a4ba"
```

### Response explanation

The request result is a demo site id.

---

# <a name="coonect-by-id">POST /sites/:site_id/roles</a>

Connect user with id sended in post body as user_id to worksite with :site_id. As response returns all user roles.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/roles
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
| user_id | Yes | User with this id will be connected to demo site. User id's can be retrieved from */accounts.*| | a054374c0e984777ab2455abeaf32083 |
| role | Yes | User role, there is three type of roles: user, manager, admin. User have read only access, manager can't change worksite settings, edit devices, accounts and gateways. Admin have full access on worksite. | | manager |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site admin or higher roles.

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/sites/9e55c43454ad4c6f99cb20e06aac3b95/roles
`

### Example Body

```
{ 
    "user_id": "a054374c0e984777ab2455abeaf32083",
    "role": "manager"
}
```

### Example response

```
[
    "9e55c43454ad4c6f99cb20e06aac3b95:manager",
    "9cfaf79bc95b4a9e912314eb3db7a4ba:manager"
],
```

### Response explanation

The request result is an array of user roles. Roles is array of strings, each string is a role for some site. Roles have following structure "<site_id>:<role>". *site_id* can be retrieved from */sites.*, *role* can take next values: *user*, *manager*, *admin*. System administrator have role **admin** without site_id.

---

# <a name="disconnect">DELETE /sites/:site_id/roles</a>

Remove user with id sended in post body as user_id from worksite with :site_id. As response returns all user roles.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/sites/:site_id/roles
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
| user_id | Yes | User with this id will be connected to demo site. User id's can be retrieved from */accounts.*| | a054374c0e984777ab2455abeaf32083 |
| role | Yes | User role, there is three type of roles: user, manager, admin. User have read only access, manager can't change worksite settings, edit devices, accounts and gateways. Admin have full access on worksite. | | manager |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site admin or owner or higher roles.

### Example Request

`
 DEL http://api.positron.iquipsys.net:30018/api/v1/sites/9e55c43454ad4c6f99cb20e06aac3b95/roles
`

### Example Body

```
{ 
    "user_id": "a054374c0e984777ab2455abeaf32083",
    "role": "manager"
}
```

### Example response

```
[
    "9cfaf79bc95b4a9e912314eb3db7a4ba:manager"
],
```

### Response explanation

The request result is an array of user roles. Roles is array of strings, each string is a role for some site. Roles have following structure "<site_id>:<role>". *site_id* can be retrieved from */sites.*, *role* can take next values: *user*, *manager*, *admin*. System administrator have role **admin** without site_id.

---