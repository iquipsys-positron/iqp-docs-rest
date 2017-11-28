Page navigation

* [Get user roles](#roles)
* [Grant user roles](#grant-roles)
* [Revoke user roles](#revoke-roles)

---

# <a name="roles">GET /roles/:user_id</a>

Returns json data about all user roles.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/roles/:user_id
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
| user_id | Yes | User ids can be retrieved from */accounts* | | 5ad48b88358d48fc9c84e90498748a8f |

### Access security 

To execute this request needed system administrator role.

### Example Request

`
 GET http://tracker.pipservices.net:8080/api/v1/roles/5ad48b88358d48fc9c84e90498748a8f
`

### Example response

```
[
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
]
```

### Response explanation

The request result is an array of user roles. Each role represents as string with next structure "<site_id>:<role>". Site ids can be retreived from */sites/all*, role can take next values: *user*, *manager*, *admin*. For system administator role is admin, without site id.

---

# <a name="grant-roles">POST /roles/:user_id/grant</a>

Grant roles for user. Can be sended multiple roles at ones in string array.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/roles/:user_id/grant
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |
| Requires body | Yes |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| user_id | Yes | User ids can be retrieved from */accounts* | | 0984f44cbc6648b0b23d955f9d964c2f |

### Access security 

To execute this request needed system administrator role.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/roles/0984f44cbc6648b0b23d955f9d964c2f/grant
`

### Example body
```
[
"29c81b7e03c6469a923fa2da0e09f8b2:user",
"7fdf17af1b7d4e57b100a498efdf88b2:manager"
]
```

### Example response
```
[
"29c81b7e03c6469a923fa2da0e09f8b2:user",
"7fdf17af1b7d4e57b100a498efdf88b2:manager",
"9cfaf79bc95b4a9e912314eb3db7a4ba:admin"
]
```

### Response explanation

The request result is an array of user roles. Each role represents as string with next structure "<site_id>:<role>". Site ids can be retreived from */sites/all*, role can take next values: *user*, *manager*, *admin*. For system administator role is admin, without site id.

---

# <a name="revoke-roles">POST /roles/:user_id/revoke</a>

Revoke roles for user. Can be revoked multiple roles at ones in string array.

### Request URL

`
http://tracker.pipservices.net:8080/api/v1/roles/:user_id/revoke
`

### Request Information

| Property | Value |
|----|----|
| Response formats | JSON |
| Requires authentication | YES |
| Requires body | Yes |

- ### Required headers
| Header name | Description | Example |
|----|----|----|
| x-session-id | Session id. This id can be retrived from */signin* | f053db945f924dfbbaf3710116acf7cb |

### Parameters

| Name | Required | Description | Default value | Examples |
|------|----------|-------------|---------------|---------|
| user_id | Yes | User ids can be retrieved from */accounts* | | 0984f44cbc6648b0b23d955f9d964c2f |

### Access security 

To execute this request needed system administrator role.

### Example Request

`
 POST http://tracker.pipservices.net:8080/api/v1/roles/0984f44cbc6648b0b23d955f9d964c2f/revoke
`

### Example body
```
[
"29c81b7e03c6469a923fa2da0e09f8b2:user",
"7fdf17af1b7d4e57b100a498efdf88b2:manager"
]
```

### Example response
```
[
"9cfaf79bc95b4a9e912314eb3db7a4ba:admin"
]
```

### Response explanation

The request result is an array of user roles. Each role represents as string with next structure "<site_id>:<role>". Site ids can be retreived from */sites/all*, role can take next values: *user*, *manager*, *admin*. For system administator role is admin, without site id.