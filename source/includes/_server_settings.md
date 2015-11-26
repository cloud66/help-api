# Server Settings settings

## Server Settings list

```http
GET /stacks/{stack_id}/servers/{server_id}/settings HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":[
    {
      "key":"server.name",
      "value":"Caribou",
      "readonly":true,
      "warning_text":"Warning! Changing this value will also modify your Cloud 66 *.c66.me DNS values"}
  ],
  "count":1,
  "pagination":
    {
      "previous":null,
      "next":null,
      "current":1,
      "per_page":30,
      "count":1,
      "pages":1
    }
}
```

Get list of all settings of a server

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/servers/{server_id}/settings`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
server_id | true | string | The server UID | `f8468fc145ea49bac474b30a8fea888d`

## Server Setting

```http
GET stacks/{stack_id}/servers/{server_id}/settings/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "key":"server.name",
      "value":"Caribou"
    }
}
```

Get information of a single server setting item

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET stacks/{stack_id}/servers/{server_id}/settings/{id}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
server_id | true | string | The server uid | `f8468fc145ea49bac474b30a8fea888d`
id | true | string | The server setting item id | `server-name`

## Update Server Setting

```http
PUT /stacks/{stack_id}/servers/{server_id}/settings/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":9,
      "user":"test@cloud66.com",
      "resource_type":"server",
      "action":"server-set: server.name",
      "resource_id":"445",
      "started_via":"api",
      "started_at":"2014-09-01T13:07:35Z",
      "finished_at":null,
      "finished_success":null,
      "finished_message":null
    }
}
```

Update value of a server setting item

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`PUT /stacks/{stack_id}/servers/{server_id}/settings/{id}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
server_id | true | string | The server UID | `f8468fc145ea49bac474b30a8fea888d`
id | true | string | The server setting item id | `server-name`
value | true | string | The server setting item new value | `newname`
