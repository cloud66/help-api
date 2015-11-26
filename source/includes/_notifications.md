# Notifications

## Notifications list

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

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
alert_type | false | string | Type of alert | `server.stopped`

## Notification

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

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | true | integer | The notification id | `4153`

## Update Notification

```http
PUT /stacks/{stack_id}/notifications/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

Update channel/params of a notification

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`PUT /stacks/{stack_id}/notifications/{id}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | true | integer | The notification id | `4153`
channels | false | string | Notification channels (valid channels are: email, ios, hipchat, webhook, slack) | `[email,ios]`
params | false | string | Notification channel parameters (as JSON string with valid keys: hipchat_token, hipchat_room, slack_url, slack_channel, webhook_url) | `{'hipchat_room' : 'test'}`
