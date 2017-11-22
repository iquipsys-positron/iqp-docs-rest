## Get site invitations

# GET /sites/:site_id/invitations

Returns json array with data about all invitations on specified site.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations
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
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations
`

# Example Responce

```
{
	"total": 1,
	"data": [
	{
		"creator_id": "cd65c2023be34e84b2e9529264d17d21",
		"creator_name": "Dmitriy Krainiy",
		"invitee_email": "invited_user@gmail.com",
		"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
		"site_name": "Demo Minesite",
		"role": "user",
		"type": "activation",
		"create_time": "2017-11-21T07:47:49.543Z",
		"expire_time": "2017-12-06T07:47:49.543Z",
		"sent_time": "2017-11-21T07:47:49.543Z",
		"id": "eb51e4c5e785483aac44c74bcad38174"
	}
	],
}
```

---

## Get invitation info

# GET /sites/:site_id/invitations/:invitation_id

Returns json data about one or all invitation on specified site. If you don't set *invitation_id* result will contain all site invitations. To get info only about one invitation you should set *invitation_id* in request url.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations/:invitation_id
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
| invitation_id | No | invitation ids can be retrieved from */sites/:site_id/invitations* Set invitation id to get data for one invitation. | | eb51e4c5e785483aac44c74bcad38174 |

# Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations/eb51e4c5e785483aac44c74bcad38174
`

# Example Responce

```
{
	"creator_id": "cd65c2023be34e84b2e9529264d17d21",
	"creator_name": "Dmitriy Krainiy",
	"invitee_email": "invited_user@gmail.com",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"site_name": "Demo Minesite",
	"role": "user",
	"type": "activation",
	"create_time": "2017-11-21T07:47:49.543Z",
	"expire_time": "2017-12-06T07:47:49.543Z",
	"sent_time": "2017-11-21T07:47:49.543Z",
	"id": "eb51e4c5e785483aac44c74bcad38174"
}
```

---

## Create invitation

# POST /sites/:site_id/invitations

Creates new invitation from json string to specified site. 

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations
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
| creator_id | Yes | Id of the invitation creator, it can be received from */accounts* | | cd65c2023be34e84b2e9529264d17d21 |
| creator_name | Yes | Name of the invitation creator, it can be received from */accounts* | | cd65c2023be34e84b2e9529264d17d21 |
| invitee_email | Yes | On this email will be sended invite to connect worksite | | admin@gmail.com | 
| site_name | Yes | Name of the site, this name will be displayed in received email | | Demo Minesite | 
| role | Yes | User role, there is three type of roles: user, manager, admin. User have read only access, manager can't change worksite settings, edit devices, accounts and gateways. Admin have full access on worksite. | | admin |
| type | Yes | For user invitation to worksite set type as activation. | | activation |



# Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations
`

# Example Body

```
{
	"creator_id": "cd65c2023be34e84b2e9529264d17d21",
	"creator_name": "Dmitriy Krainiy",
	"invitee_email": "admin@gmail.com",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"site_name": "Demo Minesite",
	"role": "admin",
	"type": "activation"
}
```

# Example Responce

```
{
	"creator_id": "cd65c2023be34e84b2e9529264d17d21",
	"creator_name": "Dmitriy Krainiy",
	"invitee_email": "admin@gmail.com",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"site_name": "Demo Minesite",
	"role": "admin",
	"type": "activation",
	"create_time": "2017-11-21T08:12:49.758Z",
	"expire_time": "2017-12-06T08:12:49.758Z",
	"sent_time": "2017-11-21T08:12:49.758Z",
	"id": "8740dc302f5b4cc7b78a05b5918c1440"
}
```

---

## Resend invitation

# POST /sites/:site_id/invitations/:invitation_id/resend

Resend email to invited user by existing invitation.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations/:invitation_id/resend
`

# Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |
| Requires body | No |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| invitation_id | No | invitation ids can be retrieved from */sites/:site_id/invitations* | | 8740dc302f5b4cc7b78a05b5918c1440 |

# Example Request

`
POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations/8740dc302f5b4cc7b78a05b5918c1440
`

# Example Responce

```
{
	"creator_id": "cd65c2023be34e84b2e9529264d17d21",
	"creator_name": "Dmitriy Krainiy",
	"invitee_email": "admin@gmail.com",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"site_name": "Demo Minesite",
	"role": "admin",
	"type": "activation",
	"create_time": "2017-11-21T08:12:49.758Z",
	"expire_time": "2017-12-06T08:29:39.624Z",
	"sent_time": "2017-11-21T08:29:39.624Z",
	"id": "8740dc302f5b4cc7b78a05b5918c1440"
}
```

---

## Respond invitation

# POST /sites/:site_id/invitations/:invitation_id/respond

Accepts existing invitation by invitee user.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations/:invitation_id/respond
`

# Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |
| Requires body | No |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

# Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| invitation_id | No | invitation ids can be retrieved from */sites/:site_id/invitations* | | 8740dc302f5b4cc7b78a05b5918c1440 |

# Example Request

`
POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations/8740dc302f5b4cc7b78a05b5918c1440
`

# Example Responce

```
{
	"creator_id": "cd65c2023be34e84b2e9529264d17d21",
	"creator_name": "Dmitriy Krainiy",
	"invitee_email": "admin@gmail.com",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"site_name": "Demo Minesite",
	"role": "admin",
	"type": "activation",
	"create_time": "2017-11-21T08:12:49.758Z",
	"expire_time": "2017-12-06T08:29:39.624Z",
	"sent_time": "2017-11-21T08:29:39.624Z",
	"id": "8740dc302f5b4cc7b78a05b5918c1440"
}
```

---

## Delete invitation

# DELETE /sites/:site_id/invitations/:invitation_id

Deletes existing invitation.

# Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations/:invitation_id
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
| invitation_id | No | invitation ids can be retrieved from */sites/:site_id/invitations* | | 8740dc302f5b4cc7b78a05b5918c1440 |

# Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations/8740dc302f5b4cc7b78a05b5918c1440
`

# Example Responce

```
{
	"creator_id": "cd65c2023be34e84b2e9529264d17d21",
	"creator_name": "Dmitriy Krainiy",
	"invitee_email": "admin@gmail.com",
	"site_id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
	"site_name": "Demo Minesite",
	"role": "admin",
	"type": "activation",
	"create_time": "2017-11-21T08:12:49.758Z",
	"expire_time": "2017-12-06T08:12:49.758Z",
	"sent_time": "2017-11-21T08:12:49.758Z",
	"id": "8740dc302f5b4cc7b78a05b5918c1440"
}
```