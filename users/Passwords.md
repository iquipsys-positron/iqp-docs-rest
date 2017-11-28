Page navigation

* [Recover password](#recover-password)
* [Reset password](#reset-password)
* [Change password](#change-password)

---

# <a name="recover-password">POST /passwords/recover</a>

Send email with password recovery code.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/passwords/recover
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
| login | Yes | Login of the existing account to recovery password. On this email will be sended message with recovery code. | | user@gmail.com |


### Access security 

Anybody can execute this request.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/passwords/recover
`

### Example Body

```
{
    "login":"krdima92@gmail.com"
}
```

### Example response

```
204
```

### Response explanation

The request result is 204 when request successfully executed. Also on account email sends message with password recovery code.

---

# <a name="reset-password">POST /passwords/reset</a>

Reset user password by recovery code received on email after execution */passwords/recover* request.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/passwords/reset
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
| login | Yes | User login of the existing account. Logins can be retreived from */accounts* | | user@gmail.com |
| code | Yes | Password recovery code, received on email after execution */passwords/recover* request| | 175913162 |
| password | Yes | User new password. Minimum 6 symbols | | 123321 |

### Access security 

Anybody can execute this request.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/passwords/reset
`

### Example Body

```
{
    "login":"krdima92@gmail.com",
    "code":"175913163",
    "password":"123456"
}
```

### Example response

```
204
```

### Response explanation

The request result is 204 when request successfully executed it means that password for account was changed.

---

# <a name="change-password">POST /passwords/:user_id/change</a>

Change user password by user id.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/passwords/:user_id/change
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | Yes |
| Requires body | Yes |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

### Body parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| login | Yes | User login of the existing account. Logins can be retreived from */accounts* | | user@gmail.com |
| old_password | Yes | User current password. Minimum 6 symbols | | 123123 |
| new_password | Yes | User new password. Minimum 6 symbols | | 123321 |
| user_id | Yes | Id of the user for changing password. User id can be retreived from */accounts* | | cd65c2023be34e84b2e9529264d17d21 |

### Access security 

To execute this request needed system administator rule or use own user_id.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/passwords/cd65c2023be34e84b2e9529264d17d21/change
`

### Example Body

```
{
    "login":"krdima92@gmail.com",
    "old_password":"qweewq",
    "new_password":"asddsa",
    "user_id":"cd65c2023be34e84b2e9529264d17d21"
}
```

### Example response

```
204
```

### Response explanation

The request result is 204 when request successfully executed it means that password for account was changed.

---