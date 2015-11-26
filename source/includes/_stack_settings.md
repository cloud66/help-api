# Stack settings

## Settings list

```http
GET /stacks/{id}/settings HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":[
    {
      "id":"allowed-web-source",
      "key":"allowed.web.source",
      "value":null,
      "readonly":false,
      "warning_text":""
    },
    {
      "id":"asset-prefix",
      "key":"asset.prefix",
      "value":"assets",
      "readonly":false,
      "warning_text":""
    },
    {
      "id":"git-branch",
      "key":"git.branch",
      "value":"master",
      "readonly":false,
      "warning_text":""
    },
    {
      "id":"reconfigure-nginx",
      "key":"reconfigure.nginx",
      "value":false,
      "readonly":false,
      "warning_text":""
    },
    {
      "id":"stack-name",
      "key":"stack.name",
      "value":"test-elastic-1",
      "readonly":true,
      "warning_text":"Warning! Changing this value will also modify your Cloud 66 *.c66.me DNS values"
    },
    {
      "id":"maintenance-mode",
      "key":"maintenance.mode",
      "value":false,
      "readonly":false,
      "warning_text":""

    }
  ],
  "count":5,
  "pagination":
    {
      "previous":null,
      "next":null,
      "current":1,
      "per_page":30,
      "count":6,
      "pages":1
    }
}
```

Get list of all settings of stack

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/settings`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`

## Setting

```http
GET /stacks/{stack_id}/settings/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "key":"git.branch",
      "value":"master"
    }
}
```

Get information of a single setting item

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/settings/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | string | The setting item ID | `git-branch`

## Update Setting

```http
PUT /stacks/{stack_id}/notifications/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":7,
      "user":"test@cloud66.com",
      "resource_type":"stack",
      "action":"stack-set: git.branch",
      "resource_id":"280",
      "started_via":"api",
      "started_at":"2014-09-01T12:47:24Z",
      "finished_at":null,
      "finished_success":null,
      "finished_message":null
    }
}
```

Update value of a setting item

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`PUT /stacks/{stack_id}/settings/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | integer | The setting item ID | `git-branch`
value | **required** | string | The setting item new value | `staging`
