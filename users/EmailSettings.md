Page navigation

* [Resend verification email](#resend-email_settings)
* [Verify user email](#verify-email_settings)
* [Get user email settings](#email_settings)
* [Update user email settings](#edit-email_settings)

---

# <a name="resend-email_setting">POST /email_settings/resend</a>

Resend email with verification code for verify account email.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/email_settings/resend
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
| login | Yes | Login of the existing account to resend verification email. On this email will be sended message with verification code. | | user@gmail.com |


### Access security 

Anybody can execute this request.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/email_settings/resend
`

### Example Body

```
{
    "login":"user@gmail.com"
}
```

### Example response

```
204
```

### Response explanation

The request result is 204 when request successfully executed. Also on account email sends message with verification code.

---

# <a name="verify-email_settings">POST /email_settings/verify</a>

Verify user account by verification code received on email.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/email_settings/verify
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
| login | Yes | User login of the existing account. Logins can be retrieved from */accounts* | | user@gmail.com |
| code | Yes | Verification code, can be received on email after */email_settingss/resend* request| | 175913162 |

### Access security 

Anybody can execute this request.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/email_settings/verify
`

### Example Body

```
{
    "login":"krdima92@gmail.com",
    "code":"175913163"
}
```

### Example response

```
204
```

### Response explanation

The request result is 204 when request successfully executed it means that account email was verified.

---

# <a name="email_settings">GET /email_settings/:user_id</a>

Returns json array with data about user email settings.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/email_settings/:user_id
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | Yes |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| user_id | Yes | User account id. These IDs can be retrieved from */accounts.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed system administator rules or use own user_id.

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/email_settings/cd65c2023be34e84b2e9529264d17d21
`

### Example response

```
{
	"name": "Dmitriy Krainiy",
	"email": "krdima92@gmail.com",
	"language": null,
	"verified": true,
	"id": "cd65c2023be34e84b2e9529264d17d21"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|-------------|
| name | User account name |
| email | User account email |
| language | Language for email to user. Default value is english, can be null. |
| verified | Boolean variable to store is user email was verified |
| id | User account id |

---

# <a name="edit-email_settings">PUT /email_settings/:user_id</a>

Edit existing user email settings.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/email_settings/:user_id
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | Yes |
| Requires body | Yes |

- ### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| name | No | User account name | | User 1 |
| email | Yes | User account email | | user@gmail.com |
| language | No | Language for email to user. Default value is english, can be null. | | ут |
| verified | No | Boolean variable to store is user email was verified | | true, false |
| id | Yes | User account id | | cd65c2023be34e84b2e9529264d17d21 |


- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| user_id | Yes | User account id. These IDs can be retrieved from */accounts.*| | 9cfaf79bc95b4a9e912314eb3db7a4ba |

### Access security 

To execute this request needed system administator rules or use own user_id.

### Example Request

`
 PUT http://api.positron.iquipsys.net:30018/api/v1/email_settings/cd65c2023be34e84b2e9529264d17d21
`


### Example Body

```
{
	"email": "krdima92@gmail.com",
	"language": "en",
	"id": "cd65c2023be34e84b2e9529264d17d21"
}
```

### Example response

```
{
	"name": "Dmitriy Krainiy",
	"email": "krdima92@gmail.com",
	"language": "en",
	"ver_code": null,
	"ver_expire_time": null,
	"verified": true,
	"id": "cd65c2023be34e84b2e9529264d17d21"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|-------------|
| name | User account name |
| email | User account email |
| language | Language for email to user. Default value is english, can be null. |
| verified | Boolean variable to store is user email was verified |
| ver_code | Code for verification email, if account email verified - this variable is null |
| ver_expire_time | Time when verification code expires, if account email verified - this variable is null |
| id | User account id |