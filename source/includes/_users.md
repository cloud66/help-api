# Users

## Users list

```http
GET /users HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": [
    {
      "id": 18,
      "email": "test@cloud66.com",
      "primary_account_id": 14,
      "accounts": [
        {
          "account": 14,
          "user": 18,
          "role": "owner",
          "can_create_stack": true,
          "can_admin_users": true,
          "default_permission_level": 60
        }
      ],
      "access_rights": [
        {
          "user": 18,
          "stack": "5acd43412ea412e32897c40d46f91183",
          "access_level":
            {
              "code": 60,
              "meaning":"admin"
            }
        },
        {
          "user": 18,
          "stack": "8cc984959ebe28bcb75d6bd6d810767e",
          "access_level":
            {
              "code": 60,
              "meaning": "admin"
            }
        }],
      "locked": false,
      "uses_tfa": false,
      "timezone": "UTC",
      "has_valid_phone": false,
      "developer_program": true,
      "github_login": false,
      "last_login": "2014-08-29T17:17:11Z",
      "devices": [
        {
          "device_type": 1,
          "sub_type": 2,
          "token": "wertqy",
          "enabled": true,
          "created_at": "2014-08-04 11:57:36 UTC",
          "updated_at": "2014-08-04 12:03:22 UTC",
          "created_at_iso": "2014-08-04T11:57:36Z",
          "updated_at_iso": "2014-08-04T12:03:22Z"
        }
      ],
      "created_at": "2013-06-19T11:08:02Z",
      "updated_at": "2014-09-01T08:11:34Z",
      "cloud_status": "partial"
    }
  ],
    "count":1,
    "pagination":{
      "previous": null,
      "next": null,
      "current": 1,
      "per_page": 30,
      "count": 1,
      "pages": 1
    }
}
```

Get list of users that caller has access to.

<aside class="notice">
<b>Scope:</b> <i>users</i>
</aside>

### HTTP Request

`GET /users`

## User

```http
GET /users/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id": 18,
      "email": "test@cloud66.com",
      "primary_account_id": 14,
      "accounts": [
        {
          "account": 14,
          "user": 18,
          "role": "owner",
          "can_create_stack":true,
          "can_admin_users":true, "default_permission_level":60
        }
      ],
      "access_rights": [
        {
          "user": 18,
          "stack": "5acd43412ea412e32897c40d46f91183",
          "access_level":
            {
              "code": 60,
              "meaning": "admin"
            }
        }
      ],
      "locked": false,
      "uses_tfa": false,
      "timezone": "UTC",
      "has_valid_phone": false,
      "developer_program": true,
      "github_login": false,
      "last_login": "2014-08-29T17:17:11Z",
      "devices":[
        {
          "device_type": 1,
          "sub_type": 2,
          "token": "wertqy",
          "enabled": true,
          "created_at": "2014-08-04 11:57:36 UTC",
          "updated_at": "2014-08-04 12:03:22 UTC",
          "created_at_iso": "2014-08-04T11:57:36Z",
          "updated_at_iso": "2014-08-04T12:03:22Z"
        }
      ],
      "created_at": "2013-06-19T11:08:02Z",
      "updated_at": "2014-09-01T08:33:43Z",
      "cloud_status": "partial"
    }
}
```

Get detailed information about a user.

<aside class="notice">
<b>Scope:</b> <i>users</i>
</aside>

### HTTP Request

`GET /users/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The user UID | `1`

## Add Device

```http
POST /users/{id}/devices HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "device_type": 1,
      "sub_type": 1,
      "token": "mmccdd",
      "enabled": true,
      "created_at": "2014-09-01 09:15:50 UTC",
      "updated_at": "2014-09-01 09:15:50 UTC",
      "created_at_iso": "2014-09-01T09:15:50Z",
      "updated_at_iso": "2014-09-01T09:15:50Z"
    }
}
```

Add a new device for the user.

<aside class="notice">
<b>Scope:</b> <i>users</i>
</aside>

### HTTP Request

`POST /users/{id}/devices`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The user UID | `1`
device_type | **required** | integer | Device type (`1` = iOS, `2` = Android) | `1`
sub_type | **required** | integer | Device subtype (`1` = iPhone, `2` = iPad, `3` = iPod) | `1`
token | **required** | string | The token of the device | `htyukjbnnmshthkr`

## Update Device

```http
PUT /users/{id}/devices HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

Update device_type/sub_type of a device

<aside class="notice">
<b>Scope:</b> <i>users</i>
</aside>

### HTTP Request

`PUT /users/{id}/devices`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The user UID | `1`
device_type | **required** | integer | Device type (`1` = iOS, `2` = Android) | `1`
sub_type | **required** | integer | Device subtype (`1` = iPhone, `2` = iPad, `3` = iPod) | `1`
token | **required** | string | The token of the device | `htyukjbnnmshthkr`

## Delete Device

```http
DELETE /stacks/{stack_id}/environments/{key} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

Delete a device

<aside class="notice">
<b>Scope:</b> <i>users</i>
</aside>

### HTTP Request

`DELETE /users/{id}/devices/token`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The user UID | `1`
token | **required** | string | The token of the device | `htyukjbnnmshthkr`
