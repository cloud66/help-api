# Notifications

## Notifications list

```ruby
id = '5999b763474b0eafa5fafb64bff0ba80'
response = token.get("#{api_url}/stacks/#{id}/notifications.json")

puts JSON.parse(response.body)['response']
```

```http
GET /stacks/{id}/notifications HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":[
    {
      "id":1189,
      "user_id":18,
      "alert_type":"stack.provision.ok",
      "channels":["email"],
      "stack_id":"5acd43412ea412e32897c40d46f91183",
      "params":{},
      "created_at":"2014-05-29T17:29:54Z",
      "updated_at":"2014-05-29T17:29:54Z"
    },
    {
      "id":1190,
      "user_id":18,
      "alert_type":"stack.provision.fail",
      "channels":["email"],
      "stack_id":"5acd43412ea412e32897c40d46f91183",
      "params":{},
      "created_at":"2014-05-29T17:29:54Z",
      "updated_at":"2014-05-29T17:29:54Z"
    },
    {
      "id":1191,
      "user_id":18,
      "alert_type":"stack.redeploy.ok",
      "channels":["email"],
      "stack_id":"5acd43412ea412e32897c40d46f91183",
      "params":{},
      "created_at":"2014-05-29T17:29:54Z",
      "updated_at":"2014-05-29T17:29:54Z"
    }
  ],
  "count":30,
  "pagination":
    {
      "previous":null,
      "next":2,
      "current":1,
      "per_page":30,
      "count":48,
      "pages":2
    }
}
```

Get list of all environment variables of stack

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/notifications`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
alert_type | optional | string | Type of alert | `server.stopped`

## Notification

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
id = 1191
response = token.get("#{api_url}/stacks/#{stack_id}/notifications/#{id}.json")

puts JSON.parse(response.body)['response']
```

```http
GET /stacks/{stack_id}/notifications/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":1191,
      "user_id":18,
      "alert_type":
      "stack.redeploy.ok",
      "channels":["email"],
      "stack_id":"5acd43412ea412e32897c40d46f91183",
      "params":{},
      "created_at":"2014-05-29T17:29:54Z",
      "updated_at":"2014-05-29T17:29:54Z"
    }
}
```

Get information of a single notification

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/notifications/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | integer | The notification ID | `1191`

## Update Notification

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
id = 1191

channels = ['email','hipchat']
params = {:hipchat_room => 'test', :hipchat_token => 'YOUR_TOKEN'}

response = token.put("#{api_url}/stacks/#{stack_id}/notifications/#{id}.json", {body: {:channels => channels, :params => params}})

puts JSON.parse(response.body)['response']
```

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
    "id":85,
    "user_id":1,
    "alert_type":"active.protect.block",
    "channels":["email","hipchat"],
    "stack_id":"3ee97c150d95a9dc4fc801783d18087c",
    "params":{},
    "created_at":"2015-11-16T18:14:04Z",
    "updated_at":"2015-12-09T13:06:14Z"
  }
}

```

Update `channels` or `params` of a notification

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`PUT /stacks/{stack_id}/notifications/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | integer | The notification ID | `1191`
channels | optional | string | Notification channels (valid channels are: `email`, `ios`, `hipchat`, `webhook`, `slack`) | `[email,ios]`
params | optional | string | Notification channel parameters (as JSON string with valid keys: `hipchat_token`, `hipchat_room`, `slack_url`, `slack_channel`, `webhook_url`) | `{'hipchat_room' : 'test'}`
