Page navigation

* [Get all accounts](#accounts)
* [Get current account](#account)
* [Get account by id](#user-account)
* [Create account](#new-account)
* [Update account](#edit-account)
* [Delete account](#delete-account)

---

# <a name="accounts">GET /accounts</a>

Returns json array with data about all accounts.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/accounts
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

To execute this request needed to be signed in system.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/accounts
`

### Example response

```
{
	"total": 51,
	"data": [
	{
		"name": "asd",
		"login": "asdasdasd@asdasd.com",
		"language": "en",
		"theme": "default",
		"time_zone": null,
		"active": true,
		"create_time": "2017-11-27T13:15:11.060Z",
		"id": "b66b608f9df3412a984b80dbdbfb2b1b"
	},
	{
		"name": "new user",
		"login": "uytfvbnkiuyg@asdasdas.com",
		"language": "en",
		"theme": "default",
		"time_zone": null,
		"active": true,
		"create_time": "2017-11-17T08:39:08.331Z",
		"id": "9e2bfef7e5364983935fd8c7be3522d6"
	},
	{
		"name": "invited user",
		"login": "dimongaga@gmail.com",
		"language": "en",
		"theme": "default",
		"time_zone": null,
		"active": true,
		"create_time": "2017-11-16T09:04:10.570Z",
		"id": "0984f44cbc6648b0b23d955f9d964c2f"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| name | Name of the user account |
| login | User account login, ussualy equals to email |
| language | User interface language |
| theme | User interface theme. Theme can be default or accent |
| time_zone | User time zone |
| create_time | Time when account has been created. Stores in format yyyy-MM-ddTHH:mm:ss.fffZ |
| active | Variable to store is account active |
| id | Account id |

---

# <a name="account">GET /accounts/current</a>

Returns json array with data about current account.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/accounts/current
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

To execute this request needed to be signed in system.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/accounts/current
`

### Example response

```
{
	"name": "Dmitriy Krainiy",
	"login": "krdima92@gmail.com",
	"theme": "iqt-main",
	"language": "ru",
	"about": "",
	"active": true,
	"create_time": "2017-08-08T08:12:38.736Z",
	"id": "cd65c2023be34e84b2e9529264d17d21"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| name | Name of the user account |
| login | User account login, ussualy equals to email |
| language | User interface language |
| theme | User interface theme. Theme can be default or accent |
| time_zone | User time zone |
| create_time | Time when account has been created |
| active | Variable to store is account active |
| id | Account id |

---

# <a name="user-account">GET /accounts/:user_id</a>

Returns json array with data about user account.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/accounts/:user_id
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

To execute this request needed system administrator role or use own *user_id*. 

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| user_id | Yes | User account id. These IDs can be retrieved from */accounts.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/accounts/4390c2ae20a8449aac459d6f1a5ac097
`

### Example response

```
{
	"name": "invited user",
	"login": "dimongaga@gmail.com",
	"language": "en",
	"theme": "default",
	"time_zone": null,
	"active": true,
	"create_time": "2017-11-16T09:04:10.570Z",
	"id": "0984f44cbc6648b0b23d955f9d964c2f"
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| name | Name of the user account |
| login | User account login, ussualy equals to email |
| language | User interface language |
| theme | User interface theme. Theme can be default or accent |
| time_zone | User time zone |
| create_time | Time when account has been created |
| active | Variable to store is account active |
| id | Account id |

---

# <a name="new-account">POST /accounts</a>

Create new account from json data.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/accounts
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | No |
| Requires body | Yes |

### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| name | Yes | Name of the user account | | User 1 |
| login | Yes | User account login, ussualy equals to email | | user@gmail.com |
| email | Yes | User email | | user@gmail.com |
| language | No | User interface language | en | en, ru |
| theme | User interface theme. Theme can be default or accent |
| time_zone | No | User time zone | null | Europe/Moscow |
| create_time | No | Time when account has been created | <current_time> | 2017-11-27T15:46:33.041Z |
| active | No | Variable to store is account active | true |

### Access security 

To execuce this request needed to have system administator role.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/accounts
`

### Example Body

```
{
	"name": "new test user",
	"login": "usert0@gmail.com",
	"email": "usert0@gmail.com",
	"language": "en",
	"theme": "default",
	"time_zone": "Europe/Moscow",
	"active": true
}
```

### Example response

```
{
	"name": "new test user",
	"login": "usert0@gmail.com",
	"language": "en",
	"theme": "default",
	"time_zone": "Europe/Moscow",
	"active": true,
	"create_time": "2017-11-27T15:46:33.041Z",
	"id": "662635fab7dc4e1c8d888e9d300e9b3a",
	"password": "pass2312341"
}
```

### Response explanation

The request result is a new created account json data.

---

# <a name="edit-account">PUT /accounts/:user_id</a>

Edites existing account.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/accounts/:user_id
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | No |
| Requires body | Yes |

- ### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| name | Yes | Name of the user account | | User 1 |
| login | Yes | User account login, ussualy equals to email | | user@gmail.com |
| email | Yes | User email | | user@gmail.com |
| language | No | User interface language | en | en, ru |
| theme | User interface theme. Theme can be default or accent |
| time_zone | No | User time zone | null | Europe/Moscow |
| create_time | No | Time when account has been created | <current_time> | 2017-11-27T15:46:33.041Z |
| active | No | Variable to store is account active | true |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| user_id | Yes | User account id. These IDs can be retrieved from */accounts.*| | 662635fab7dc4e1c8d888e9d300e9b3a |

### Access security 

To execuce this request needed to have system administator role or use own *user_id*.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/accounts/662635fab7dc4e1c8d888e9d300e9b3a
`

### Example Body

```
{
	"name": "new edited user",
	"login": "usert0@gmail.com",
	"language": "ru"
}
```

### Example response

```
{
	"name": "new edited user",
	"login": "usert0@gmail.com",
	"language": "ru",
	"theme": "default",
	"time_zone": "Europe/Moscow",
	"active": true,
	"create_time": "2017-11-27T15:46:33.041Z",
	"id": "662635fab7dc4e1c8d888e9d300e9b3a"
}
```

### Response explanation

The request result is an edited account json data.

---

# <a name="delete-account">GET /accounts/:user_id</a>

Delete existing account.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/accounts/:user_id
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

To execute this request needed to be system administator or use own *user_id*.

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| user_id | Yes | User account id. These IDs can be retrieved from */accounts.*| | 662635fab7dc4e1c8d888e9d300e9b3a |

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/accounts/662635fab7dc4e1c8d888e9d300e9b3a
`

### Example response

```
{
	"name": "new edited user",
	"login": "usert0@gmail.com",
	"language": "ru",
	"theme": "default",
	"time_zone": "Europe/Moscow",
	"active": true,
	"create_time": "2017-11-27T15:46:33.041Z",
	"id": "662635fab7dc4e1c8d888e9d300e9b3a"
}
```

### Response explanation

The request result is a deleted account json data.

---