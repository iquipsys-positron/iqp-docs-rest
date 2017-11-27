Page navigation

* [Get worksite invitations](#invitations)
* [Get invitation info](#invitation)
* [Create invitation](#new-invitation)
* [Delete invitation](#delete-invitation)
* [Resend invitation](#resend-invitation)
* [Respond invitation](#respond-invitation)

---

# <a name="invitations">GET /sites/:site_id/invitations</a>

Returns json array with data about all invitations on specified site.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations
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
| site_id | Yes | Invitation site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations
`

### Example response

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

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| site_id | Invitation site id. These IDs can be retrieved from */sites.* |
| creator_id | Id of the invitation creator, it can be received from */accounts*|
| creator_name | Name of the invitation creator, it can be received from */accounts* |
| invitee_email | On this email will be sended invite to connect worksite |
| site_name | Invitation site name. These names can be retrieved from */sites.* |
| role | User role, there is three type of roles: user, manager, admin. User have read only access, manager can't change worksite settings, edit devices, accounts and gateways. Admin have full access on worksite. |
| type | For user invitation to worksite set type as activation |
| create_time | Time of the invitation creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| expire_time | Time of the invitation expire. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| sent_time | Time when invitation has been sended. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| id | Inuque identifier of the event template |

---

# <a name="invitation">GET /sites/:site_id/invitations/:invitation_id</a>

Returns json data about one or all invitation on specified site. If you don't set *invitation_id* result will contain all site invitations. To get info only about one invitation you should set *invitation_id* in request url.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations/:invitation_id
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
| site_id | Yes | Invitation site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| invitation_id | No | invitation ids can be retrieved from */sites/:site_id/invitations* Set invitation id to get data for one invitation. | | eb51e4c5e785483aac44c74bcad38174 |

### Access security 

To execute this request needed site user or higher roles.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations/eb51e4c5e785483aac44c74bcad38174
`

### Example response

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

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| site_id | Invitation site id. These IDs can be retrieved from */sites.* |
| creator_id | Id of the invitation creator, it can be received from */accounts*|
| creator_name | Name of the invitation creator, it can be received from */accounts* |
| invitee_email | On this email will be sended invite to connect worksite |
| site_name | Invitation site name. These names can be retrieved from */sites.* |
| role | User role, there is three type of roles: user, manager, admin. User have read only access, manager can't change worksite settings, edit devices, accounts and gateways. Admin have full access on worksite. |
| type | For user invitation to worksite set type as activation |
| create_time | Time of the invitation creation. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| expire_time | Time of the invitation expire. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| sent_time | Time when invitation has been sended. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ  |
| id | Inuque identifier of the event template |

---

# <a name="new-invitation">POST /sites/:site_id/invitations</a>

Creates new invitation from json string to specified site. 

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations
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
| site_id | Yes | Invitation site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| creator_id | Yes | Id of the invitation creator, it can be received from */accounts* | | cd65c2023be34e84b2e9529264d17d21 |
| creator_name | Yes | Name of the invitation creator, it can be received from */accounts* | | cd65c2023be34e84b2e9529264d17d21 |
| invitee_email | Yes | On this email will be sended invite to connect worksite | | admin@gmail.com | 
| site_name | Yes | Name of the site, this name will be displayed in received email | | Demo Minesite | 
| role | Yes | User role, there is three type of roles: user, manager, admin. User have read only access, manager can't change worksite settings, edit devices, accounts and gateways. Admin have full access on worksite. | | admin |
| type | Yes | For user invitation to worksite set type as activation. | | activation |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations
`

### Example Body

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

### Example response

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

### Response explanation

The result is json data of new created invitation.

---

# <a name="delete-invitation">DELETE /sites/:site_id/invitations/:invitation_id</a>

Deletes existing invitation.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations/:invitation_id
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
| site_id | Yes | Invitation site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| invitation_id | No | invitation ids can be retrieved from */sites/:site_id/invitations* | | 8740dc302f5b4cc7b78a05b5918c1440 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
 DELETE http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations/8740dc302f5b4cc7b78a05b5918c1440
`

### Example response

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

### Response explanation

The result is json data of the deleted invitation.

---

# <a name="resend-invitation">POST /sites/:site_id/invitations/:invitation_id/resend</a>

Resend email to invited user by existing invitation.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations/:invitation_id/resend
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |
| Requires body | No |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Invitation site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| invitation_id | No | invitation ids can be retrieved from */sites/:site_id/invitations* | | 8740dc302f5b4cc7b78a05b5918c1440 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations/8740dc302f5b4cc7b78a05b5918c1440
`

### Example response

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

### Response explanation

The result is json data of the resended invitation.

---

# <a name="respond-invitation">POST /sites/:site_id/invitations/:invitation_id/respond</a>

Accepts existing invitation by invitee user.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sites/:site_id/invitations/:invitation_id/respond
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |
| Requires body | No |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| site_id | Yes | Invitation site id. These IDs can be retrieved from */sites.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |
| invitation_id | No | invitation ids can be retrieved from */sites/:site_id/invitations* | | 8740dc302f5b4cc7b78a05b5918c1440 |

### Access security 

To execute this request needed site manager or higher roles.

### Example Request

`
POST http://tracker.pipservices.net:8080/api/v1/sites/9cfaf79bc95b4a9e912314eb3db7a4ba/invitations/8740dc302f5b4cc7b78a05b5918c1440
`

### Example response

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

### Response explanation

The result is json data about responsed invitation.
