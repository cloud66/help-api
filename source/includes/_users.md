# Users

## Users list

```ruby
response = token.get("#{api_url}/users.json")

puts JSON.parse(response.body)['response']
```

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
      "id": 1,
      "email": "jack@gmail.com",
      "primary_account_id": 1,
      "locked": false,
      "access_profile": {
        "account_profile": {
          "can_create_stack": true,
          "can_admin_users": true,
          "can_payment": true,
          "can_add_cloud_key": true,
          "can_del_cloud_key": true,
          "can_view_acc_notifications": true,
          "can_edit_acc_notifications": true,
          "can_view_audit": true,
          "can_view_docker_img_key": true,
          "can_del_ssh_key": true,
          "can_edit_personal_token": true,
          "can_del_authorized_app": true,
          "can_view_custom_env": true,
          "can_edit_custom_env": true,
          "can_add_developers_app": true,
          "can_del_developers_app": true,
          "can_edit_git_key": true,
          "can_edit_gateway": true,
          "default_roles": [
            "Administrator"
          ]
        },
        "stack_profiles": [
          {
            "stack_uid": "d1f1d43bb86ff3e97c9f6ff2841e42cb",
            "role": "Administrator"
          },
          {
            "stack_uid": "740f81b98eb847fab0df538ea8780d9d",
            "role": "Administrator"
          },
          {
            "stack_uid": "b5f4eaaf56b5768f272ab875d2ba48b1",
            "role": "Administrator"
          }
        ]
      },
      "uses_tfa": false,
      "timezone": "UTC",
      "has_valid_phone": false,
      "developer_program": false,
      "github_login": false,
      "last_login": "2016-01-29T15:25:20Z",
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
      "created_at": "2015-08-14T19:45:28Z",
      "updated_at": "2016-02-01T11:23:38Z",
      "cloud_status": "healthy"
    },
    {
      "id": 2,
      "email": "jim@gmail.com",
      "primary_account_id": 2,
      "locked": false,
      "access_profile": {
        "account_profile": {
          "can_create_stack": true,
          "can_admin_users": false,
          "can_payment": false,
          "can_add_cloud_key": false,
          "can_del_cloud_key": true,
          "can_view_acc_notifications": false,
          "can_edit_acc_notifications": true,
          "can_view_audit": false,
          "can_view_docker_img_key": false,
          "can_del_ssh_key": false,
          "can_edit_personal_token": false,
          "can_del_authorized_app": false,
          "can_view_custom_env": false,
          "can_edit_custom_env": false,
          "can_add_developers_app": false,
          "can_del_developers_app": false,
          "can_edit_git_key": false,
          "can_edit_gateway": false,
          "default_roles": [
            "Viewer"
          ]
        },
        "stack_profiles": [
          {
            "stack_uid": "740f81b98eb847fab0df538ea8780d9d",
            "role": "Deployer"
          },
          {
            "stack_uid": "b5f4eaaf56b5768f272ab875d2ba48b1",
            "role": "Viewer"
          },
          {
            "stack_uid": "740f81b98eb847fab0df538ea8780d9d",
            "role": "Administrator"
          },
          {
            "stack_uid": "b5f4eaaf56b5768f272ab875d2ba48b1",
            "role": "Administrator"
          }
        ]
      },
      "uses_tfa": false,
      "timezone": "UTC",
      "has_valid_phone": false,
      "developer_program": false,
      "github_login": false,
      "last_login": "2016-01-28T13:12:16Z",
      "devices": [],
      "created_at": "2016-01-28T13:12:13Z",
      "updated_at": "2016-01-28T13:12:16Z",
      "cloud_status": "healthy"
    }
  ],
  "count": 2,
  "pagination": {
    "previous": null,
    "next": null,
    "current": 1,
    "per_page": 30,
    "count": 2,
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

```ruby
id = 1
response = token.get("#{api_url}/users/#{id}.json")

puts JSON.parse(response.body)['response']
```

```http
GET /users/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": {
    "id": 2,
    "email": "jim@gmail.com",
    "primary_account_id": 2,
    "locked": false,
    "access_profile": {
      "account_profile": {
        "can_create_stack": true,
        "can_admin_users": false,
        "can_payment": false,
        "can_add_cloud_key": false,
        "can_del_cloud_key": true,
        "can_view_acc_notifications": false,
        "can_edit_acc_notifications": true,
        "can_view_audit": false,
        "can_view_docker_img_key": false,
        "can_del_ssh_key": false,
        "can_edit_personal_token": false,
        "can_del_authorized_app": false,
        "can_view_custom_env": false,
        "can_edit_custom_env": false,
        "can_add_developers_app": false,
        "can_del_developers_app": false,
        "can_edit_git_key": false,
        "can_edit_gateway": false,
        "default_roles": [
          "Viewer"
        ]
      },
      "stack_profiles": [
        {
          "stack_uid": "740f81b98eb847fab0df538ea8780d9d",
          "role": "Deployer"
        },
        {
          "stack_uid": "b5f4eaaf56b5768f272ab875d2ba48b1",
          "role": "Viewer"
        },
        {
          "stack_uid": "740f81b98eb847fab0df538ea8780d9d",
          "role": "Administrator"
        },
        {
          "stack_uid": "b5f4eaaf56b5768f272ab875d2ba48b1",
          "role": "Administrator"
        }
      ]
    },
    "uses_tfa": false,
    "timezone": "UTC",
    "has_valid_phone": false,
    "developer_program": false,
    "github_login": false,
    "last_login": "2016-01-28T13:12:16Z",
    "devices": [],
    "created_at": "2016-01-28T13:12:13Z",
    "updated_at": "2016-01-28T13:12:16Z",
    "cloud_status": "healthy"
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

## Update User

```ruby
id = 1
response = token.put("#{api_url}/users/#{id}.json", {body: { payload }})
# payload is a the same as the result of GET /user/{id}.json
```

```http
PUT /users/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": 2,
    "email": "jim@gmail.com",
    "primary_account_id": 2,
    "locked": false,
    "access_profile": {
      "account_profile": {
        "can_create_stack": true,
        "can_admin_users": false,
        "can_payment": false,
        "can_add_cloud_key": false,
        "can_del_cloud_key": true,
        "can_view_acc_notifications": false,
        "can_edit_acc_notifications": true,
        "can_view_audit": false,
        "can_view_docker_img_key": false,
        "can_del_ssh_key": false,
        "can_edit_personal_token": false,
        "can_del_authorized_app": false,
        "can_view_custom_env": false,
        "can_edit_custom_env": false,
        "can_add_developers_app": false,
        "can_del_developers_app": false,
        "can_edit_git_key": false,
        "can_edit_gateway": false,
        "default_roles": [
          "Viewer"
        ]
      },
      "stack_profiles": [
        {
          "stack_uid": "740f81b98eb847fab0df538ea8780d9d",
          "role": "Deployer"
        },
        {
          "stack_uid": "b5f4eaaf56b5768f272ab875d2ba48b1",
          "role": "Viewer"
        },
        {
          "stack_uid": "740f81b98eb847fab0df538ea8780d9d",
          "role": "Administrator"
        },
        {
          "stack_uid": "b5f4eaaf56b5768f272ab875d2ba48b1",
          "role": "Administrator"
        }
      ]
    },
    "uses_tfa": false,
    "timezone": "UTC",
    "has_valid_phone": false,
    "developer_program": false,
    "github_login": false,
    "last_login": "2016-01-28T13:12:16Z",
    "devices": [],
    "created_at": "2016-01-28T13:12:13Z",
    "updated_at": "2016-01-28T13:12:16Z",
    "cloud_status": "healthy"
}
```

Update user information. Currently only access profile section changes are applied.

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`GET /users/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The user UID | `1`

## Add Device

```ruby
id = 1
token = 'htyukjbnnmshthkr'
response = token.post("#{api_url}/users/#{id}/devices.json", {body: {:device_type => 1, :sub_type => 1, :token => token}})

puts JSON.parse(response.body)['response']
```

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

<aside class="warning">
Unfortunately, a Cloud 66 app for Android is not currently available!</i>
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

```ruby
id = 1
token = 'htyukjbnnmshthkr'
response = token.put("#{api_url}/users/#{id}/devices.json", {body: {:device_type => 1, :sub_type => 1, :token => token}})

puts JSON.parse(response.body)['response']
```

```http
PUT /users/{id}/devices HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

Update `device_type` or `sub_type` of a device

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

```ruby
id = 1
token = 'htyukjbnnmshthkr'
response = token.delete("#{api_url}/users/#{id}/devices/#{token}.json")

puts JSON.parse(response.body)['response']
```

```http
DELETE /users/{id}/devices/{token} HTTP/1.1
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

`DELETE /users/{id}/devices/{token}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The user UID | `1`
token | **required** | string | The token of the device | `htyukjbnnmshthkr`
