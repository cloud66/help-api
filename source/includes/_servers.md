# Servers

## Servers list

> Headers

```http
GET /stacks/{id}/servers HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

> Body

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": [
    {
      "uid": "f8468fc145ea49bac474b30a8fea888d",
      "vendor_uid": "2492780",
      "name": "Caribou",
      "address": "146.185.133.183",
      "distro": "ubuntu",
      "distro_version": "14.04",
      "dns_record": "caribou.sb-elastic-1.dev.c66.me",
      "user_name": "root",
      "server_type": "Cloud (DigitalOcean) ",
      "server_roles": [
        "rails",
        "postgresql",
        "elasticsearch",
        "web",
        "app",
        "db"
      ],
      "server_group_id": 128,
      "stack_uid": "5acd43412ea412e32897c40d46f91183",
      "has_agent": true,
      "params":
        {
          "availability_zone": "2",
          "size": "63",
          "region": "2",
          "ips":["146.185.133.183"],
          "was_baselined": true,
          "cached_cores":1,
          "cached_memory": 1042336972,
          "passenger_version": "4.0.48",
          "passenger_enterprise": false,
          "supports_nginx_realip": true,
          "passenger_pool_max": 4
        },
      "created_at": "2014-08-29T17:21:47Z",
      "updated_at": "2014-08-29T17:54:41Z",
      "region":"2",
      "availability_zone": "2",
      "ext_ipv4": "146.185.133.183",
      "health_state": 3,
      "int_ipv4": "146.185.133.183",
      "int_ipv6": null,
      "ext_ipv6": null
    }
  ],
  "count":1,
  "pagination":
    {
      "previous": null,
      "next": null,
      "current": 1,
      "per_page": 30,
      "count": 1,
      "pages": 1
    }
}
```

Get list of all servers of stack

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/servers`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`

## Servers

> Headers

```http
GET /stacks/{stack_id}/servers/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

> Body

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "uid": "f8468fc145ea49bac474b30a8fea888d",
      "vendor_uid": "2492780",
      "name": "Caribou",
      "address": "146.185.133.183",
      "distro": "ubuntu",
      "distro_version": "14.04",
      "dns_record": "caribou.sb-elastic-1.dev.c66.me",
      "user_name": "root",
      "server_type": "Cloud (DigitalOcean) ",
      "server_roles":[
        "rails",
        "postgresql",
        "elasticsearch",
        "web",
        "app",
        "db"
      ],
      "server_group_id": 128,
      "stack_uid": "5acd43412ea412e32897c40d46f91183",
      "has_agent": true,
      "params":
        {
          "availability_zone": "2",
          "size": "63",
          "region": "2",
          "ips":["146.185.133.183"],
          "was_baselined": true,
          "cached_cores": 1,
          "cached_memory": 1042336972,
          "passenger_version": "4.0.48",
          "passenger_enterprise": false,
          "supports_nginx_realip": true,
          "passenger_pool_max":4
        },
       "created_at": "2014-08-29T17:21:47Z",
       "updated_at": "2014-08-29T17:54:41Z",
       "region": "2",
       "availability_zone": "2",
       "ext_ipv4": "146.185.133.183",
       "health_state":3,
       "int_ipv4": "146.185.133.183",
       "int_ipv6": null,
       "ext_ipv6": null
    }
}
```

Get information of a single server

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/servers/{id}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | true | string | The server id | `f8468fc145ea49bac474b30a8fea888d`
include_private_key | false | integer | if set to 1 then private_key will included in response | `1`
