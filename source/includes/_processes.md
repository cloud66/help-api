# Processes

## Processes list

```ruby
stack_id = '5999b763474b0eafa5fafb64bff0ba80'
response = token.get("#{api_url}/stacks/#{stack_id}/processes.json")

puts JSON.parse(response.body)['response']
```

```http
GET /stacks/{id}/processes HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":[
    {
      "md5":"5999b763474b0eafa5fafb64bff0ba80",
      "name":"worker",
      "command":"bundle exec rake jobs:work",
      "servers":{"server_name":1}
    },
    {
      "md5":"1230fd91f8c9e4e56c1b14dd0391702",
      "name":"scheduler",
      "command":"bundle exec rake jobs:schedule",
      "servers":{"server_name":1}
    }
  ],
  "count":2,
  "pagination":
    {
      "previous":null,
      "next":null,
      "current":1,
      "per_page":30,
      "count":2,
      "pages":1
    }
}
```

Get list of all processes of stack.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/processes`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | stack UID | `5999b763474b0eafa5fafb64bff0ba80`
server_uid | optional | integer | server UID | `e63e859d5ab72b0bcf14321f0ffb013d`

## Process Single one

```ruby
stack_id = '5999b763474b0eafa5fafb64bff0ba80'
id = 4153
response = token.get("#{api_url}/stacks/#{stack_id}/processes.json")

puts JSON.parse(response.body)['response']
```

```http
GET /stacks/{stack_id}/processes/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":[
    {
      "md5":"5999b763474b0eafa5fafb64bff0ba80",
      "name":"worker",
      "command":"bundle exec rake jobs:work",
      "servers":{"server_name1":1}
    },
    {
      "md5":"1230fd91f8c9e4e56c1b14dd0391702",
      "name":"scheduler",
      "command":"bundle exec rake jobs:schedule",
      "servers":{"server_name1":3}
    }
  ],
  "count":2,
  "pagination":
    {
      "previous":null,
      "next":null,
      "current":1,
      "per_page":30,
      "count":2,
      "pages":1
    }
}
```

Get information about a single process.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/processes/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | string | Process Name | `worker`
server_uid | **optional** | integer | Server ID | `e63e859d5ab72b0bcf14321f0ffb013d`

## Scale a Process

```ruby
stack_id = '5999b763474b0eafa5fafb64bff0ba80'
response = token.post("#{api_url}/stacks/#{stack_id}/processes.json")

puts JSON.parse(response.body)['response']
```

```http
POST /stacks/{stack_id}/processes HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Accept: application/json
Content-Type: application/json

{
  "response": [
    {
      "id":10,
      "user":"test@cloud66.com",
      "resource_type":"stack",
      "action":"Process_scale",
      "resource_id":"283",
      "started_via":"api",
      "started_at":"2016-01-01T19:08:05Z",
      "finished_at":null,
      "finished_success":null,
      "finished_message":null
    }
  ]
}
```

Scale up a process.

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`POST /stacks/{stack_id}/processes`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
process_name | **required** | string | process name | `scheduler`
server_count | **required** | string | hash of {server_uid:count} | `e63e859d5ab72b0bcf14321f0ffb013d:4`