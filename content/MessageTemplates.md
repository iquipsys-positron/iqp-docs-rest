Page navigation

* [Get all message templates](#msg_templates)
* [Get message template info](#msg_template)
* [Create message template](#new-msg_template)
* [Update message template](#edit-msg_template)
* [Delete message template](#delete-msg_template)

---

# <a name="msg_templates">GET /msg_templates</a>

Returns json array with data about all message templates.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/msg_templates
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
 GET http://api.positron.iquipsys.net:30018/api/v1/msg_templates
`

### Example response

```
{
	"total": 4,
	"data": [
	{
		"name": "verify_email",
		"text": {
			"en": "Please verify your account by entering this code {{code}} at iQuipsys.com site, or by clicking on this link."
		},
		"subject": {
			"en": "Verify iQuipsys Positron email"
		},
		"from": "info@iquipsys.com",
		"html": {
			"en": "<p>Please verify your account by clicking the following <a href='{{client_url}}/#/verify_email?server_url={{server_url}}&email={{email}}&code={{code}}&login={{email}}'>link</a>.</p><br> <p>Alternitevly you can enter this code <b>{{code}}</b> at iQuipsys.com email verification page.</p>"
		},
		"status": "new",
		"id": "ca4c33e54552445c86e7eba1f4064c31"
	},
	{
		"name": "recover_password",
		"text": {
			"en": "{{name}}, please use this code {{code}} to reset your password"
		},
		"subject": {
			"en": "Password recovery for iQuipsys Positron"
		},
		"from": "info@iquipsys.com",
		"html": {
			"en": "<p>{{name}}, please use this code <b>{{code}}</b> to reset your password at password recovery dialog"
		},
		"status": "new",
		"id": "102f2ac4f4484ae899fabe8b439ddc5e"
	},
	{
		"name": "invitation",
		"text": {
			"en": "Hello, {{invitee_name}}! You were invited to join site {{site_name}} at iQuipsys Positron by {{creator_name}}. Please signup by this link."
		},
		"subject": {
			"en": "Invitation to join an iQuipsys Positron worksite"
		},
		"from": "info@iquipsys.com",
		"html": {
			"en": "<p>{{#invitee_name}} Hello, {{invitee_name}}! {{/invitee_name}}You were invited to join site <b>{{site_name}}</b> at iQuipsys Positron by {{creator_name}}. Click <a href='{{client_url}}/#/signup?server_url={{server_url}}&login={{invitee_email}}'>this</a> link to signup.</p>"
		},
		"status": "new",
		"id": "76ab7182f69341ae840328c192fa6732"
	},
	{
		"name": "access_request",
		"text": {
			"en": "You were requested to grant access to site {{site_name}} at iQuipsys Positron{{#invitee_name}} by {{invitee_name}}{{/invitee_name}}"
		},
		"subject": {
			"en": "iQuipsys Positron worksite access request"
		},
		"from": "info@iquipsys.com",
		"html": {
			"en": "<p>You were requested to grant access to site <b>{{site_name}}</b> at iQuipsys Positron{{#invitee_name}} by <b>{{invitee_name}}</b>{{/invitee_name}}</p>"
		},
		"status": "new",
		"id": "589009d73d8f4ac9b496276662d7f389"
	}
	],
}a
```

### Response explanation

The request result is an array of objects with following structure

| Name | Description | 
|------|----------|
| name | Name of the message template |
| text | Text of the message template, stored as MultiString. |
| subject | Subject for message template, it will be the title of received email. |
| from | Email address of the sender. |
| html | Formated text of message template, stored as MultiString. This is content of the received email. |
| status | Message template status, can take next values - *new*, *writing*, *translating*, *verifying*, *completed* |
| id | Inuque identifier of the message template |

---

# <a name="msg_template">GET /msg_templates/:template_id</a>

Returns json data about one or all message template on specified site. If you don't set *template_id* result will contain all site message templates. To get info only about one message template you should set *template_id* in request url.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/msg_templates/:template_id
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
| template_id | No | message template ids can be retrieved from */msg_templates* Set message template id to get data for one message template. | | 1af7eb3146074daf8de07681a424104b |

### Access security 

To execute this request needed system administrator role. 

### Example Request

`
 GET http://api.positron.iquipsys.net:30018/api/v1/msg_templates/589009d73d8f4ac9b496276662d7f389
`

### Example response

```
{
	"name": "access_request",
	"text": {
		"en": "You were requested to grant access to site {{site_name}} at iQuipsys Positron{{#invitee_name}} by {{invitee_name}}{{/invitee_name}}"
	},
	"subject": {
		"en": "iQuipsys Positron worksite access request"
	},
	"from": "info@iquipsys.com",
	"html": {
		"en": "<p>You were requested to grant access to site <b>{{site_name}}</b> at iQuipsys Positron{{#invitee_name}} by <b>{{invitee_name}}</b>{{/invitee_name}}</p>"
	},
	"status": "new",
	"id": "589009d73d8f4ac9b496276662d7f389"
}
```

### Response explanation

The request result is an object with following structure

| Name | Description | 
|------|----------|
| name | Name of the message template |
| text | Text of the message template, stored as MultiString. |
| subject | Subject for message template, it will be the title of received email. |
| from | Email address of the sender. |
| html | Formated text of message template, stored as MultiString. This is content of the received email. |
| status | Message template status, can take next values - *new*, *writing*, *translating*, *verifying*, *completed* |
| id | Inuque identifier of the message template |

---

# <a name="new-msg_template">POST /msg_templates</a>

Create new message template from json string for specified site. In message templates you can use mustache templates for next variables: *id*, *name*, *email*, *phone*, *code* in verification messages and *creator_id*, *creator_name*, *invitee_name*, *invitee_email*, *site_id*, *site_name* in invitation messages.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/msg_templates
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
| name | Name of the message template |
| text | Text of the message template, stored as MultiString. |
| subject | Subject for message template, it will be the title of received email. |
| from | Email address of the sender. |
| html | Formated text of message template, stored as MultiString. This is content of the received email. |
| status | Message template status, can take next values - *new*, *writing*, *translating*, *verifying*, *completed* |

### Access security 

To execute this request needed system administrator role. 

### Example Request

`
 POST http://api.positron.iquipsys.net:30018/api/v1/msg_templates
`

### Example Body

```
{
	"name": "recover_password1",
	"text": {
		"en": "{{name}}, please use this code {{code}} to reset your password"
	},
	"subject": {
		"en": "Password recovery for iQuipsys Positron"
	},
	"from": "info@iquipsys.com",
	"html": {
		"en": "<p>{{name}}, please use this code <b>{{code}}</b> to reset your password at password recovery dialog"
	},
	"status": "new"
}
```

### Example response

```
{
	"name": "recover_password1",
	"text": {
		"en": "{{name}}, please use this code {{code}} to reset your password"
	},
	"subject": {
		"en": "Password recovery for iQuipsys Positron"
	},
	"from": "info@iquipsys.com",
	"html": {
		"en": "<p>{{name}}, please use this code <b>{{code}}</b> to reset your password at password recovery dialog"
	},
	"status": "new",
	"id": "102f2ac4f4484ae899fabe8b439ddc5e"
}
```

### Response explanation

The result is json data of new created object.

---

# <a name="edit-msg_template">PUT /msg_templates/:template_id</a>

Edit existing message template.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/msg_templates/:template_id
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
| name | Name of the message template |
| text | Text of the message template, stored as MultiString. |
| subject | Subject for message template, it will be the title of received email. |
| from | Email address of the sender. |
| html | Formated text of message template, stored as MultiString. This is content of the received email. |
| status | Message template status, can take next values - *new*, *writing*, *translating*, *verifying*, *completed* |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| template_id | No | message template ids can be retrieved from */msg_templates* | | 102f2ac4f4484ae899fabe8b439ddc5e |

### Access security 

To execute this request needed system administrator role. 

### Example Request

`
PUT http://api.positron.iquipsys.net:30018/api/v1/msg_templates/102f2ac4f4484ae899fabe8b439ddc5e
`

### Example Body

```
{
	"name": "recover_password1",
	"text": {
		"en": "{{name}}, please use this code {{code}} to reset your password"
	},
	"subject": {
		"en": "Password recovery for iQuipsys Positron"
	},
	"from": "info@iquipsys.com",
	"html": {
		"en": "<p>{{name}}, please use this code <b>{{code}}</b> to reset your password at password recovery dialog"
	},
	"status": "new"
}
```

### Example response

```
{
	"name": "recover_password",
	"text": {
		"en": "{{name}}, please use this code {{code}} to reset your password"
	},
	"subject": {
		"en": "Password recovery for iQuipsys Positron"
	},
	"from": "info@iquipsys.com",
	"html": {
		"en": "<p>{{name}}, please use this code <b>{{code}}</b> to reset your password at password recovery dialog"
	},
	"status": "new",
	"id": "102f2ac4f4484ae899fabe8b439ddc5e"
}
```

### Response explanation

The result is json data of the edited object.

---

# <a name="delete-msg_template">DELETE /msg_templates/:template_id</a>

Deletes existing message template.

### Request URL

`
http://api.positron.iquipsys.net:30018/api/v1/msg_templates/:template_id
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
| template_id | No | message template ids can be retrieved from */msg_templates* | | 102f2ac4f4484ae899fabe8b439ddc5e |

### Access security 

To execute this request needed system administrator role. 

### Example Request

`
 DELETE http://api.positron.iquipsys.net:30018/api/v1/msg_templates/102f2ac4f4484ae899fabe8b439ddc5e
`

### Example response

```
{
	"name": "recover_password",
	"text": {
		"en": "{{name}}, please use this code {{code}} to reset your password"
	},
	"subject": {
		"en": "Password recovery for iQuipsys Positron"
	},
	"from": "info@iquipsys.com",
	"html": {
		"en": "<p>{{name}}, please use this code <b>{{code}}</b> to reset your password at password recovery dialog"
	},
	"status": "new",
	"id": "102f2ac4f4484ae899fabe8b439ddc5e"
}
```

### Response explanation

The result is json data of the deleted object.