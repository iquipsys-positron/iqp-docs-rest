Page navigation

* [Sign up](#signup)
* [Validate login](#validate-signup)
* [Sign in](#signin)
* [Sign out](#signout)
* [Get all sessions](#sessions)
* [Get current session](#session)
* [Get session by user id](#user-session)
* [Restore session](#restore-session)
* [Delete session](#delete-session)

---

# <a name="signup">POST /signup</a>

Sign up to system. These request used for registration new user

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/signup
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | No |
| Requires body | Yes |

### Body parameters

| Name | Required | Description | Examples |
|------|----------|-------------|----------|
| serverUrl | Yes | Url to server | http://tracker.pipservices.net:8080 |
| name | Yes | User account name | User 1 |
| login | Yes | User account login, automaticaly equals to email | user@gmail.com |
| email | Yes | User email | user@gmail.com |
| password | Yes | User account password | qwerty123 |
| language | Yes | User interface language | en, ru |
| theme | Yes | User interface theme. Theme can be default or accent. | default |
| time_zone | Yes | User time zone | Europe/Moscow |

### Access security 

Anybody can execute this request.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/signup
`

### Example Body

```
{
	  "serverUrl":"http://tracker.pipservices.net:8080",
	  "name":"asd",
	  "login":"asdasdasd@asdasd.com",
	  "email":"asdasdasd@asdasd.com",
	  "password":"asdasd",
	  "language":"en",
	  "theme":"default",
	  "time_zone":null
}
```

### Example response

```
{
	"user_id": "b66b608f9df3412a984b80dbdbfb2b1b",
	"user_name": "asd",
	"address": "::ffff:109.254.10.81",
	"client": "chrome",
	"user": {
		"settings": {},
		"sites": [],
		"roles": [],
		"theme": "default",
		"language": "en",
		"time_zone": null,
		"create_time": "2017-11-27T13:15:11.060Z",
		"login": "asdasdasd@asdasd.com",
		"name": "asd",
		"id": "b66b608f9df3412a984b80dbdbfb2b1b"
	},
	"data": null,
	"request_time": "2017-11-27T13:15:11.119Z",
	"open_time": "2017-11-27T13:15:11.119Z",
	"active": true,
	"id": "6e96b347d523446e9eb7886f62d8b9e8"
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| user_id | User account id |
| user_name | Name of the user account |
| address | User IP address |
| client | User browser |
| user | Object with user settings, worksites where user have access, user roles, user interface theme, user interface language, ser account create time, etc. |
| request_time | Time when request has been received | 
| open_time | Time when session has been opened |
| active | Variable to store is session active |
| id | Session id, this id needed for all requests where authorization is required. |

---

# <a name="validate-signup">GET /signup/validate</a>

Check if selected login exists in system or no. In case of existing login recieve error with code *LOGIN_ALREADY_USED*

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/signup/validate
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | No |

### URL parameters

| Name | Required | Description | Examples |
|------|----------|-------------|----------|
| login | Yes | User login | krdima92@gmail.com |

### Access security 

Anybody can execute this request.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/signup/validate?login=unexistinguser@gmail.com
`

### Example response

```
204
```

### Response explanation

In case of successfull validation, when login not fount in system the result is *204*, otherwise, when used existing in system login the result us error with code *LOGIN_ALREADY_USED*

---

# <a name="signin">POST /signin</a>

Sign in for existing user to system.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/signin
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | No |
| Requires body | Yes |

### Body parameters

| Name | Required | Description | Examples |
|------|----------|-------------|----------|
| login | Yes | User login | krdima92@gmail.com |
| password | Yes | User password | qweeqw |

### Access security 

Anybody can execute this request.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/signin
`

### Example Body

```
{
    "login": "krdima92@gmail.com",
    "password": "qweewq"
}
```

### Example response

```
{
  "user_id": "cd65c2023be34e84b2e9529264d17d21",
  "user_name": "Dmitriy Krainiy",
  "address": "::ffff:109.254.10.81",
  "client": "chrome",
  "user": {
    "change_pwd_time": null,
    "settings": {
      "verified_email": "true",
      "incident_rules_615c5f3e00dc448698f20e3ae22944c1": "{\"enabled\":true,\"include_object_ids\":[],\"exclude_object_ids\":[],\"include_group_ids\":[],\"exclude_group_ids\":[],
      ...
    },
    "sites": [
      {
        "name": "Test site 5",
        "id": "3382613d643c47f7abd86a025b39b4dc"
      },
      {
        "name": "Demo site",
        "id": "3cc4b1a29e5b4ecd9bb2a2f5d4223572"
      },
      {
        "name": "LGOK",
        "id": "5ac3eae28ab049869481fd19557b88d4"
      },
      {
        "name": "Smoke test",
        "id": "672052da4ad2405d902d30275c17f203"
      },
      {
        "name": "Test site changed 3",
        "id": "9958f0dd1faa494fbc48ba816a02fdd0"
      },
      {
        "name": "Demo Minesite",
        "id": "9cfaf79bc95b4a9e912314eb3db7a4ba"
      },
      {
        "name": "Test site 2",
        "id": "a4ad733934a444d5b6ca77445d17d7c2"
      },
      {
        "name": "Test site 1",
        "id": "b2b50ebdb57a4a19a6c3b7250bcbd498"
      },
      {
        "name": "Demo Minesite_copy",
        "id": "dc857d9972c74dccbc3f52eb0cab985e"
      }
    ],
    "roles": [
      "9cfaf79bc95b4a9e912314eb3db7a4ba:admin",
      "dc857d9972c74dccbc3f52eb0cab985e:admin",
      "672052da4ad2405d902d30275c17f203:admin",
      "3cc4b1a29e5b4ecd9bb2a2f5d4223572:admin",
      "3382613d643c47f7abd86a025b39b4dc:admin",
      "804e2ec176ea4d119cfe067469daf18a:admin",
      "5ac3eae28ab049869481fd19557b88d4:admin",
      "4951e68b17ba4b0e981bb0218ce92daf:admin",
      "e8eb3c0607ef4d56977b60a2e938aa79:admin",
      "29c81b7e03c6469a923fa2da0e09f8b2:admin",
      "7fdf17af1b7d4e57b100a498efdf88b2:admin",
      "74c5596f6383485082700f4e3406f44d:admin",
      "19039b50b28e4343b00f1001d266207f:admin",
      "9958f0dd1faa494fbc48ba816a02fdd0:admin",
      "b2b50ebdb57a4a19a6c3b7250bcbd498:admin",
      "a4ad733934a444d5b6ca77445d17d7c2:admin",
      "admin"
    ],
    "theme": "iqt-main",
    "language": "ru",
    "create_time": "2017-08-08T08:12:38.736Z",
    "login": "krdima92@gmail.com",
    "name": "Dmitriy Krainiy",
    "id": "cd65c2023be34e84b2e9529264d17d21"
  },
  "data": null,
  "request_time": "2017-11-27T12:47:00.326Z",
  "open_time": "2017-11-27T12:47:00.326Z",
  "active": true,
  "id": "13b48f0fdd1c4ee9a9f2f89120f5b5f7"
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| user_id | User account id |
| user_name | Name of the user account |
| address | User IP address |
| client | User browser |
| user | Object with user settings, worksites where user have access, user roles, user interface theme, user interface language, ser account create time, etc. |
| request_time | Time when request has been received | 
| open_time | Time when session has been opened |
| active | Variable to store is session active |
| id | Session id, this id needed for all requests where authorization is required. |

---

# <a name="signout">POST /signout</a>

Sign out for user from session.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/signout
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | No |
| Requires body | Yes |

### Access security 

Anybody can execute this request.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/signout
`

### Example response

```
204
```

### Response explanation

In case of successfull signout the result is *204*.

---

# <a name="sessions">GET /sessions</a>

Returns json array with data about all sessions.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sessions
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

To execute this request needed system administrator role. 

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sessions
`

### Example response

```
{
	"total": 2184,
	"data": [
	{
		"user_id": "4390c2ae20a8449aac459d6f1a5ac097",
		"user_name": "Simulation",
		"address": "::ffff:54.92.237.255",
		"client": "Pip.Facade PowerShell Client",
		"request_time": "2017-11-27T14:11:53.974Z",
		"open_time": "2017-11-27T14:11:53.974Z",
		"active": true,
		"id": "f87b974cd0d647dd97320a2aaae91124"
	},
	{
		"user_id": "cd65c2023be34e84b2e9529264d17d21",
		"user_name": "Dmitriy Krainiy",
		"address": "::ffff:109.254.10.81",
		"client": "chrome",
		"request_time": "2017-11-27T14:01:17.470Z",
		"open_time": "2017-11-27T14:01:17.470Z",
		"active": true,
		"id": "0e66eb96b0b043cfbc297d10f1a0c1a9"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| user_id | User account id |
| user_name | Name of the user account |
| address | User IP address |
| client | User browser |
| request_time | Time when request for session open has been received | 
| open_time | Time when session has been opened |
| active | Variable to store is session active |
| id | Session id, this id needed for all requests where authorization is required. |

---

# <a name="session">GET /sessions/current</a>

Returns json array with data about current session.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sessions/current
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
 GET http://tracker.pipservices.net:8080/api/v1/sessions/current
`

### Example response

```
{
	"user_id": "cd65c2023be34e84b2e9529264d17d21",
	"user_name": "Dmitriy Krainiy",
	"address": "::ffff:109.254.10.81",
	"client": "chrome",
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
	},
	"data": null,
	"request_time": "2017-11-27T14:01:17.470Z",
	"open_time": "2017-11-27T14:01:17.470Z",
	"active": true,
	"id": "0e66eb96b0b043cfbc297d10f1a0c1a9"
}
```

### Response explanation

The request result is of object with following structure

| Name | Description | 
|------|----------|
| user_id | User account id |
| user_name | Name of the user account |
| address | User IP address |
| client | User browser |
| user | Object with user settings, worksites where user have access, user roles, user interface theme, user interface language, ser account create time, etc. |
| request_time | Time when open session request has been received | 
| open_time | Time when session has been opened |
| active | Variable to store is session active |
| id | Session id, this id needed for all requests where authorization is required. |

---

# <a name="user-sessions">GET /sessions/:user_id</a>

Returns json array with data about all sessions.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sessions/:user_id
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
 GET http://tracker.pipservices.net:8080/api/v1/sessions/4390c2ae20a8449aac459d6f1a5ac097
`

### Example response

```
{
	"total": 22,
	"data": [
	{
		"user_id": "4390c2ae20a8449aac459d6f1a5ac097",
		"user_name": "Simulation",
		"address": "::ffff:54.92.237.255",
		"client": "Pip.Facade PowerShell Client",
		"request_time": "2017-11-27T14:11:53.974Z",
		"open_time": "2017-11-27T14:11:53.974Z",
		"active": true,
		"id": "f87b974cd0d647dd97320a2aaae91124"
	},
	{
		"user_id": "4390c2ae20a8449aac459d6f1a5ac097",
		"user_name": "Simulation",
		"address": "::ffff:54.92.237.255",
		"client": "Pip.Facade PowerShell Client",
		"request_time": "2017-11-27T13:25:32.760Z",
		"open_time": "2017-11-27T13:25:32.760Z",
		"active": true,
		"id": "6bc10f19f7b74164acbe2417f295b574"
	},
	{
		"user_id": "4390c2ae20a8449aac459d6f1a5ac097",
		"user_name": "Simulation",
		"address": "::ffff:54.92.237.255",
		"client": "Pip.Facade PowerShell Client",
		"request_time": "2017-11-27T07:20:24.263Z",
		"open_time": "2017-11-27T07:20:24.263Z",
		"active": true,
		"id": "4fae1a74deb44ff292038600fbed0952"
	},
	...
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| user_id | User account id |
| user_name | Name of the user account |
| address | User IP address |
| client | User browser |
| request_time | Time when request for session open has been received | 
| open_time | Time when session has been opened |
| active | Variable to store is session active |
| id | Session id, this id needed for all requests where authorization is required. |

---

# <a name="restore-session">POST /sessions/restore</a>

Restore expired session by id. Sesion id can be retrieved from */sessions*.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sessions/restore
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | No |
| Requires body | Yes |

### Body parameters

| Name | Required | Description | Examples |
|------|----------|-------------|----------|
| login | Yes | User login | krdima92@gmail.com |
| password | Yes | User password | qweeqw |

### Access security 

To execuce this request needed to be signed to system.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sessions/restore
`

### Example Body

```
{
    "session_id": "4fae1a74deb44ff292038600fbed0952"
}
```

### Example response

```
{
	"user_id": "4390c2ae20a8449aac459d6f1a5ac097",
	"user_name": "Simulation",
	"address": "::ffff:54.92.237.255",
	"client": "Pip.Facade PowerShell Client",
	"user": {
		"id": "4390c2ae20a8449aac459d6f1a5ac097",
		"name": "Simulation",
		"login": "sim_demo",
		"create_time": "2017-11-10T07:42:25.640Z",
		"roles": [
		"9cfaf79bc95b4a9e912314eb3db7a4ba:admin"
		],
		"sites": [
		{
			"id": "9cfaf79bc95b4a9e912314eb3db7a4ba",
			"name": "Demo Minesite"
		}
		],
	},
	"data": null,
	"request_time": "2017-11-27T07:20:24.263Z",
	"open_time": "2017-11-27T07:20:24.263Z",
	"active": true,
	"id": "4fae1a74deb44ff292038600fbed0952"
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| user_id | User account id |
| user_name | Name of the user account |
| address | User IP address |
| client | User browser |
| user | Object with user settings, worksites where user have access, user roles, user interface theme, user interface language, ser account create time, etc. |
| request_time | Time when request has been received | 
| open_time | Time when session has been opened |
| active | Variable to store is session active |
| id | Session id, this id needed for all requests where authorization is required. |

---

# <a name="delete-session">GET /sessions/:user_id/:session_id</a>

Delete existing session by user and session ids.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sessions/:user_id/:session_id
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
| user_id | Yes | User account id. These IDs can be retrieved from */accounts.*| | 4390c2ae20a8449aac459d6f1a5ac097 |
| session_id | Yes | Session id can be retrieved from */session.*| | 4fae1a74deb44ff292038600fbed0952 |

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/sessions/4390c2ae20a8449aac459d6f1a5ac097/4fae1a74deb44ff292038600fbed0952
`

### Example response

```
{
    "user_id": "4390c2ae20a8449aac459d6f1a5ac097",
	  "user_name": "Simulation",
	  "address": "::ffff:54.92.237.255",
	  "client": "Pip.Facade PowerShell Client",
	  "user": null,
	  "data": null,
	  "close_time": "2017-11-27T14:44:44.717Z",
	  "request_time": "2017-11-27T14:44:44.717Z",
	  "open_time": "2017-11-27T07:20:24.263Z",
	  "active": false,
	  "id": "4fae1a74deb44ff292038600fbed0952"
}
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| user_id | User account id |
| user_name | Name of the user account |
| address | User IP address |
| client | User browser |
| user | Object with user settings, worksites where user have access, user roles, user interface theme, user interface language, ser account create time, etc. |
| request_time | Time when open session request has been received | 
| open_time | Time when session has been opened |
| active | Variable to store is session active |
| id | Session id, this id needed for all requests where authorization is required. |

---