# Firewall rules

## Firewall rules list

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

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`

## Firewall rule

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

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | true | integer | The firewall rule id | `4153`

## Add Firewall rule

```http
POST /stacks/{stack_id}/firewalls HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

One of the from/to params must be specified.
If you specify ttl , from_ip can be set as 'AUTO', then caller IP will be set as from_ip

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`POST /stacks/{stack_id}/firewalls`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
ttl | false | integer | Time that firewall rule will be expires in | `20`
from_ip | false | string | From IP value of rule | `123.123.123.123`
from_group_id | false | integer | You can specify a server group id as From | `19`
from_server_id | false | integer | You can specify a server id as From | `193`
to_ip | false | string | To IP value of rule | `123.123.123.123`
to_group_id | false | integer | You can specify a server group id as To | `19`
to_server_id | false | integer | You can specify a server id as To | `1`
protocol | true | integer | Protocol of firewall rule . TCP = 1 , UDP = 2 , ICMP = 3 | `1`
port | true | integer | Port of firewall rule | `80`
