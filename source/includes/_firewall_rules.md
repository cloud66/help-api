# Firewall rules

## Firewall rules list

```ruby
id = '5999b763474b0eafa5fafb64bff0ba80'
response = token.get("#{api_url}/stacks/#{id}/firewalls.json")

puts JSON.parse(response.body)['response']
```

```http
GET /stacks/{id}/firewalls HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": [
    {
      "id": 5027,
      "from_ip": "0.0.0.0/0",
      "from_group_id": null,
      "from_server_id": null,
      "to_ip": null,
      "to_group_id": 128,
      "to_server_id": null,
      "protocol": "tcp",
      "port": 80,
      "rule_type": "dynamic",
      "comments":null,
      "created_at": "2014-08-29T17:58:23Z",
      "updated_at": "2014-08-29T17:58:23Z"
    },
    {
      "id":5028,
      "from_ip":"0.0.0.0/0",
      "from_group_id":null,
      "from_server_id":null,
      "to_ip":null,
      "to_group_id":128,
      "to_server_id":null,
      "protocol":"tcp",
      "port":443,"rule_type":
      "dynamic",
      "comments":null,
      "created_at":
      "2014-08-29T17:58:23Z",
      "updated_at":"2014-08-29T17:58:23Z"
    }
  ],
  "count":2,
  "pagination":
    {
      "previous":null,
      "next":null,
      "current":1,
      "per_page":30,
      "count":11,
      "pages":1
    }
}
```

Get list of all firewall rules of stack

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/firewalls`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`

## Firewall rule

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
id = 4153
response = token.get("#{api_url}/stacks/#{stack_id}/firewalls/#{id}.json")

puts JSON.parse(response.body)['response']
```

```http
GET /stacks/{stack_id}/firewalls/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":5027,
      "from_ip":"0.0.0.0/0",
      "from_group_id":null,
      "from_server_id":null,
      "to_ip":null,
      "to_group_id":128,
      "to_server_id":null,
      "protocol":"tcp",
      "port":80,
      "rule_type":"dynamic",
      "comments":null,
      "created_at":"2014-08-29T17:58:23Z",
      "updated_at":"2014-08-29T17:58:23Z"
    }
}
```

Get information of a single firewall rule

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/firewalls/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | integer | The firewall rule ID | `4153`

## Add Firewall rule

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
response = token.post("#{api_url}/stacks/#{stack_id}/firewalls.json", {body: {:from_ip => '123.123.123.123', :protocol => 1, :port => 80, :ttl => 20}})

puts JSON.parse(response.body)['response']
```

```http
POST /stacks/{stack_id}/firewalls HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":1851,
      "user":"test@cloud66.com",
      "resource_type":"stack",
      "action":"open_lease",
      "resource_id":"1268",
      "started_via":"api",
      "started_at":"2015-12-08T18:01:21Z",
      "finished_at":null,
      "finished_success":null,
      "finished_message":null
    }
}
```

One of the from/to params must be specified.
If you specify `ttl` , `from_ip` can be set as `AUTO`, then caller IP will be set as `from_ip`

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`POST /stacks/{stack_id}/firewalls`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
ttl | optional | integer | Time that firewall rule will be expires in | `20`
from_ip | optional | string | From IP value of rule | `123.123.123.123`
from_group_id | optional | integer | You can specify a server group ID as From | `19`
from_server_id | optional | integer | You can specify a server ID as From | `193`
to_ip | optional | string | To IP value of rule | `123.123.123.123`
to_group_id | optional | integer | You can specify a server group ID as To | `19`
to_server_id | optional | integer | You can specify a server ID as To | `1`
protocol | **required** | integer | Protocol of firewall rule . `1`=TCP , `2`=UDP , `3`=ICMP | `1`
port | **required** | integer | Port of firewall rule | `80`
