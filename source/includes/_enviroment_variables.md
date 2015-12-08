# Environment Variables

## Environment Variable list

```ruby
id = '5999b763474b0eafa5fafb64bff0ba80'
response = token.get("#{api_url}/#{id}/environments.json")

puts JSON.parse(response.body)['response']
```

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

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`

## Environment Variable

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
id = 4153
response = token.get("#{api_url}/stacks/#{stack_id}/environments/#{id}.json")

puts JSON.parse(response.body)['response']
```

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

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | integer | The environment variable ID | `4153`

## Add Environment Variable

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
response = token.post("#{api_url}/stacks/#{stack_id}/environments.json", {body: {:key => 'MY_ENVIRONMENT_VALUE', :value => 'SOME_VALUE'}})

puts JSON.parse(response.body)['response']
```

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

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
key | **required** | string | The new environment variable key | `MY_ENVIRONMENT_VALUE`
value | **required** | string | The new environment variable new value | `SOME_VALUE`

## Update Environment Variable

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
key = 'POSTGRESQL_SLAVE_ADDRESSES'
response = token.put("#{api_url}/stacks/#{stack_id}/environments/#{key}.json", {body: {:value => '127.0.0.1'}})

puts JSON.parse(response.body)['response']
```

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

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
key | **required** | string | The environment variable key | `POSTGRESQL_SLAVE_ADDRESSES`
value | **required** | string | The environment variable new value | `127.0.0.1`

## Delete Environment Variable

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
key = 'MY_ENV_1'
response = token.delete("#{api_url}/stacks/#{stack_id}/environments/#{key}.json)

puts JSON.parse(response.body)['response']
```

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

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
key | **required** | string | The environment variable key | `MY_ENV_1`
