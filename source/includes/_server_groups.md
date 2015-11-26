# Server Groups

## Server Groups list

```http
GET /stacks/{id}/server_groups HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": [
    {
      "id": 128,
      "name": "Rails Server",
      "type": "rails",
      "created_at": "2014-08-29T17:21:47Z",
      "updated_at": "2014-08-29T17:21:47Z"
    },
    {
      "id":129,
      "name":
      "PostgreSQL Server",
      "type": "postgresql",
      "created_at": "2014-08-29T17:21:47Z",
      "updated_at":"2014-08-29T17:21:47Z"
    }
  ],
  "count": 2,
  "pagination":
    {
      "previous": null,
      "next": null,
      "current": 1,
      "per_page": 30,
      "count":2,
      "pages":1
    }
}
```

Get list of all server groups of stack

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/server_groups`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`

## Server Group

```http
GET /stacks/{stack_id}/server_groups/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{

  "response":
    {
      "id": 128,
      "name": "Rails Server",
      "type": "rails",
      "created_at": "2014-08-29T17:21:47Z",
      "updated_at": "2014-08-29T17:21:47Z"
    }
}
```

Get information of a single server group

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/server_groups/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | integer | The setting group ID | `128`
