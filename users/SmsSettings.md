Page navigation

* [Resend verification sms](#resend-sms_settings)
* [Verify user sms](#verify-sms_settings)
* [Get user sms settings](#sms_settings)
* [Update user sms settings](#edit-sms_settings)

---

# <a name="resend-sms_setting">POST /sms_settings/resend</a>

Resend sms with verification code for verify account phone number.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sms_settings/resend
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
| phone | Yes | User phone number in form E.123 international +7 AAA BBB BB BB. | | +380508308403 |


### Access security 

Anybody can execute this request.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sms_settings/resend
`

### Example Body

```
{
	"phone": "+380508308443"
}
```

### Example response

```
204
```

### Response explanation

The request result is 204 when request successfully executed. Also on account phone number sends message with verification code.

---

# <a name="verify-sms_settings">POST /sms_settings/verify</a>

Verify user account by verification code received from sms.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sms_settings/verify
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
| phone | Yes | User phone number in form E.123 international +7 AAA BBB BB BB. | | +380508308403 |
| code | Yes | Verification code, can be received from sms after */sms_settingss/resend* request| | 175913162 |

### Access security 

Anybody can execute this request.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/sms_settings/verify
`

### Example Body

```
{
    "phone": "+380508308443",
    "code":"175913163"
}
```

### Example response

```
204
```

### Response explanation

The request result is 204 when request successfully executed it means that account phone number was verified.

---

# <a name="sms_settings">GET /sms_settings/:user_id</a>

Returns json array with data about user sms settings.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sms_settings/:user_id
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
 GET http://tracker.pipservices.net:8080/api/v1/sms_settings/cd65c2023be34e84b2e9529264d17d21
`

### Example response

```
{
	"phone": "+380508308403",
	"verified": false,
	"id": "cd65c2023be34e84b2e9529264d17d21"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|-------------|
| phone | User phone number in form E.123 international	+7 AAA BBB BB BB. |
| verified | Boolean variable to store is user sms was verified |
| id | User account id |

---

# <a name="edit-sms_settings">PUT /sms_settings/:user_id</a>

Edit existing user sms settings.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/sms_settings/:user_id
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
| phone | Yes | User phone number in form E.123 international +7 AAA BBB BB BB. | | +380508308403 |
| verified | No | Boolean variable to store is user email was verified | | true, false |
| id | No | User account id. This id can be retrieved from */accounts* | | cd65c2023be34e84b2e9529264d17d21 |

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
 PUT http://tracker.pipservices.net:8080/api/v1/sms_settings/cd65c2023be34e84b2e9529264d17d21
`


### Example Body

```
{
	"phone": "+380508308443"
}
```

### Example response

```
{
	"phone": "+380508308443",
	"ver_code": "888906187",
	"ver_expire_time": "2017-11-29T07:09:21.115Z",
	"verified": false,
	"id": "cd65c2023be34e84b2e9529264d17d21"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|-------------|
| phone | User phone number in form E.123 international	+7 AAA BBB BB BB. |
| verified | Boolean variable to store is user sms was verified |
| ver_code | Code for verification phone number, if account phone number verified - this variable is null |
| ver_expire_time | Time when verification code expires, if account sms verified - this variable is null |
| id | User account id |