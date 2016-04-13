# Server Groups

## Server Groups list

```ruby
id = '5999b763474b0eafa5fafb64bff0ba80'
response = token.get("#{api_url}/stacks/#{id}/server_groups.json")

puts JSON.parse(response.body)['response']
```

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

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
id = 128
response = token.get("#{api_url}/stacks/#{stack_id}/server_groups/#{id}.json")

puts JSON.parse(response.body)['response']
```

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

## Scale up

```ruby
stack_id = '5999b763474b0eafa5fafb64bff0ba80'
id = 53
response = token.post("#{api_url}/stacks/#{stack_id}/server_groups/#{id}.json",  {body: {:subtype => 'docker', :server_size => 't2.small'}})

puts JSON.parse(response.body)['response']
```

```http
POST /stacks/{stack_id}/server_groups/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
     {
       "id":8,
       "user":"shab@shab.com",
       "resource_type":"stack",
       "action":"scale_up",
       "resource_id":"28",
       "started_via":"api",
       "started_at":"2016-04-04T18:13:14Z",
       "finished_at":null,
       "finished_success":null,
       "finished_message":null
     }
}
```

Scale-up a new server in server group. `subtype` and `server_size` must be passed as params.

<aside class="notice">
This api only works for <i>docker</i> and <i>web</i> server groups
</aside>

<aside class="notice">
<b>Scope:</b> <i>redeploy</i>
</aside>

### HTTP Request

`POST /stacks/{stack_id}/server_groups/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | integer | The server group id | `12345`
subtype | **required** | string | The server group type ( valid options are `web`, `process` and `docker` ) | `docker`
server_size | **required** | string | The server size base on your cloud | `t2.small`
server_count | optional | integer | The number of server to scale-up | `2`
server_availability_zone | optional | string | The availability zone which you want the servers fired into (AWS EC2 only) | `us-east-1d`
server_subnet_id | optional | string | The subnet_id which you want the servers fired into (AWS EC2 only) | `subnet-123456`
root_disk_type | optional | string |  Disk type, accepted values are `ssd` and `magnetic`.  (AWS EC2 and GCE only) | `ssd`
root_disk_size | optional | integer |  Default size of root disk (in GB) for servers.  (AWS EC2 and GCE only) | `40`
server_names | optional | string |  The name of the servers | `backend1,backend2`   