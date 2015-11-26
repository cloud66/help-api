# Environment Variables

## Environment Variable list

```http
GET /stacks/{id}/environments HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": [
    {
      "id": 4152,
      "key": "STACK_GIT_BRANCH",
      "value": "master",
      "readonly": true,
      "created_at": "2014-08-29T17:21:25Z",
      "updated_at": "2014-08-29T17:21:25Z",
      "is_password":false,
      "is_generated": true,
              "history" : [{ "key" : 1, "value" : "develop", "created_at" : "2015-05-08T15:09:50Z", "updated_at" : "2015-05-08T15:09:50Z" }]
    },
    {
      "id": 4153,
      "key": "STACK_PATH",
      "value": "/var/deploy/test-elastic-1/web_head/current",
      "readonly": true,
      "created_at": "2014-08-29T17:21:25Z",
      "updated_at": "2014-08-29T17:21:25Z",
      "is_password": false,
      "is_generated": true,
              "history" : [{ "key" : 2, "value" : "/var/deploy/test-elastic-1/web_head/somethingold", "created_at" : "2015-05-08T14:01:50Z", "updated_at" : "2015-05-08T14:01:50Z" }]                    
    },
    {
      "id": 4167,
      "key": "POSTGRESQL_USERNAME",
      "value": "tja",
      "readonly": false,
      "created_at": "2014-08-29T17:21:26Z",
      "updated_at":"2014-08-29T17:21:26Z",
      "is_password":false,
      "is_generated":true,
              "history" : [{ "key" : 5, "value" : "xyz", "created_at" : "2015-05-08T14:01:50Z", "updated_at" : "2015-05-08T14:01:50Z" }, { "key" : 6, "value" : "123", "created_at" : "2015-05-08T14:02:50Z", "updated_at" : "2015-05-08T14:02:50Z" }]
    },
    {
      "id":4168,
      "key": "POSTGRESQL_PASSWORD",
      "value": "tjena",
      "readonly":false,
      "created_at":"2014-08-29T17:21:26Z",
      "updated_at":"2014-08-29T17:21:26Z",
      "is_password":true,
      "is_generated":true,
              "history" : []
    }
  ],
  "count":30,
  "pagination":
    {
      "previous":null,
      "next":null,
      "current":1,
      "per_page":30,
      "count":4,
      "pages":1
    }
}
```

Get list of all environment variables of stack

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`GET /stacks/{id}/environments`

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`

## Environment Variable

```http
GET /stacks/{stack_id}/environments/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id": 4153,
      "key":
      "STACK_PATH",
      "value":"/var/deploy/test-elastic-1/web_head/current",
      "readonly":true,
      "created_at":"2014-08-29T17:21:25Z",
      "updated_at":"2014-08-29T17:21:25Z",
      "is_password":false,
      "is_generated":true,
                "history" : [{ "key" : 5, "value" : "xyz", "created_at" : "2015-05-08T14:01:50Z", "updated_at" : "2015-05-08T14:01:50Z" }, { "key" : 6, "value" : "123", "created_at" : "2015-05-08T14:02:50Z", "updated_at" : "2015-05-08T14:02:50Z" }]
    }
}
```

Get information of a single environment variable

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/environments/{id}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
key | true | string | The new environment variable key | `MY_ENVIRONMENT_VALUE`
value | true | string | The new environment variable new value | `SOME_VALUE`

## Add Environment Variable

```http
POST /stacks/{stack_id}/environments HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":5,
      "user":"test@cloud66.com",
      "resource_type": "stack",
      "action": "env-var-new",
      "resource_id": "280",
      "started_via":"api",
      "started_at": "2014-09-01T10:56:57Z",
      "finished_at": null,
      "finished_success":null,
      "finished_message":null
    }
}
```

Add a new environment variable

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`POST /stacks/{stack_id}/environments`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
key | true | string | The new environment variable key | `MY_ENVIRONMENT_VALUE`
value | true | string | The new environment variable new value | `SOME_VALUE`

## Update Environment Variable

```http
PUT /stacks/{stack_id}/environments/{key} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":3,
      "user": "test@cloud66.com",
      "resource_type": "stack",
      "action": "env-var-update",
      "resource_id":"280",
      "started_via":"api",
      "started_at": "2014-09-01T10:44:52Z",
      "finished_at": null,
      "finished_success":null,
      "finished_message":null
    }
}
```

Update value of an environment variable if it is not readonly

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`PUT /stacks/{stack_id}/environments/{key}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
key | true | string | The environment variable key | `POSTGRESQL_SLAVE_ADDRESSES`
value | true | string | The environment variable new value | `127.0.0.1`

## Delete Environment Variable

```http
DELETE /stacks/{stack_id}/environments/{key} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

Delete an environment variable if it is not readonly or generated by cloud66

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`DELETE /stacks/{stack_id}/environments/{key}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
key | true | string | The environment variable key | `MY_ENV_1`
