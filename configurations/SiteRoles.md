## Get site users

# GET /sites/:site_id/users

Returns json array with data about all site users.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/users
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
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/users
`

# Example Responce

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

---

## Connect to demo site

# POST /sites/demo/roles

Connect user with id sended in post body as user_id to demo worksite. As responce returns demo site id.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/demo/roles
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
| user_id | Yes | User with this id will be connected to demo site. User id's can be retrieved from */accounts.*| | cd65c2023be34e84b2e9529264d17d21 |


# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/demo/roles
`

# Example Body

```
{ 
    "user_id": "cd65c2023be34e84b2e9529264d17d21"
}
```

# Example Responce

```
"9cfaf79bc95b4a9e912314eb3db7a4ba"
```

---

## Connect to existing site

# POST /sites/:site_id/roles

Connect user with id sended in post body as user_id to worksite with :site_id. As responce returns all user roles.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/roles
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
| user_id | Yes | User with this id will be connected to demo site. User id's can be retrieved from */accounts.*| | a054374c0e984777ab2455abeaf32083 |
| role | Yes | User role, there is three type of roles: user, manager, admin. User have read only access, manager can't change worksite settings, edit devices, accounts and gateways. Admin have full access on worksite. | | manager |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9e55c43454ad4c6f99cb20e06aac3b95/roles
`

# Example Body

```
{ 
    "user_id": "a054374c0e984777ab2455abeaf32083",
    "role": "manager"
}
```

# Example Responce

```
[
    "9e55c43454ad4c6f99cb20e06aac3b95:manager",
    "9cfaf79bc95b4a9e912314eb3db7a4ba:manager"
],
```

---

## Disconnect user from existing site

# DEL /sites/:site_id/roles

Connect user with id sended in post body as user_id to worksite with :site_id. As responce returns all user roles.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/roles
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
| user_id | Yes | User with this id will be connected to demo site. User id's can be retrieved from */accounts.*| | a054374c0e984777ab2455abeaf32083 |
| role | Yes | User role, there is three type of roles: user, manager, admin. User have read only access, manager can't change worksite settings, edit devices, accounts and gateways. Admin have full access on worksite. | | manager |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

# Example Request

`
 DEL http://tracker.pipservices.net:8080/api/v1/sites/9e55c43454ad4c6f99cb20e06aac3b95/roles
`

# Example Body

```
{ 
    "user_id": "a054374c0e984777ab2455abeaf32083",
    "role": "manager"
}
```

# Example Responce

```
[
    "9cfaf79bc95b4a9e912314eb3db7a4ba:manager"
],
```

---