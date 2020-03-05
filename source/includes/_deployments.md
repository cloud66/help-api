# Deployments

## Deployment list

```ruby
id = 'a6b583684833a2cf4845079c9d9350a8'
response = token.get("#{api_url}/stacks/#{id}/deployments.json")

puts JSON.parse(response.body)['response']
```

```http
GET /stacks/{id}/deployments HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":[
    {
      "id":107,
      "triggered_by":"test@cloud66.com",
      "triggered_via":
        {
          "code":0,
          "meaning":"web"
        },
      "started_at":"2014-08-29T17:46:16Z",
      "finished_at":"2014-08-29T17:58:23Z",
      "outcome":
        {
          "code":1,
          "meaning":"success"
        },
      "git_hash":"5675fcd8f9e6dc534ecf1410c0661c066097e310",
      "deploy_session":"OhBHNzkXSl",
      "deploy_type":
        {
          "code":0,
          "meaning":"build"
        },
      "is_head":true,
      "is_live":true,
      "reverted":null,
      "reverted_by":null,
      "reverted_at":null,
      "is_deploying":false,
      "commit_url":"https://github.com/cloud66-samples/rails-test/commit/5675fcd8f9e6dc534ecf1410c0661c066097e310"
    }
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

Get list of all deployments of a stack

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/deployments`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`

## Deployment

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
id = '3608'
response = token.get("#{api_url}/stacks/#{stack_id}/deployments/#{id}.json")

puts JSON.parse(response.body)['response']
```

```http
GET /stacks/{stack_id}/deployments/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":107,
      "triggered_by":"test@cloud66.com",
      "triggered_via":
        {
          "code":0,
          "meaning":"web"
        },
      "started_at":"2014-08-29T17:46:16Z",
      "finished_at":"2014-08-29T17:58:23Z",
      "outcome":
        {
          "code":1,
          "meaning":"success"
        },
      "git_hash":"5675fcd8f9e6dc534ecf1410c0661c066097e310",
      "deploy_session":"OhBHNzkXSl",
      "deploy_type":
        {
          "code":0,
          "meaning":"build"
        },
      "is_head":true,
      "is_live":true,
      "reverted":null,
      "reverted_by":null,
      "reverted_at":null,
      "is_deploying":false,
      "commit_url":"https://github.com/cloud66-samples/rails-test/commit/5675fcd8f9e6dc534ecf1410c0661c066097e310"
    }
}
```

Get information of a single deployment

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/deployments/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | integer | The deployment ID | `107`

## Redeploy

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
response = token.post("#{api_url}/stacks/#{stack_id}/deployments.json")

puts JSON.parse(response.body)['response']
```

```http
POST /stacks/{stack_id}/deployments HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "ok":true,
      "message":"Stack queued for redeployment"
    }
}
```

Redeploy a stack

<aside class="notice">
<b>Scope:</b> <i>redeploy</i>
</aside>

### HTTP Request

`POST /stacks/{stack_id}/deployments`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
git_ref | optional | string | Git reference (branch, tag or hash). Non-docker only. | `a_git_tag_or_hash`
services | optional | string | Deploy only the service(s) specified. Docker only. | `service1,service2`

## Cancel deployment

```ruby
stack_id = 'a6b583684833a2cf4845079c9d9350a8'
id = '3649'
response = token.delete("#{api_url}/stacks/#{stack_id}/deployments/#{id}.json")

puts JSON.parse(response.body)['response']
```

```http
DELETE /stacks/{stack_id}/deployments/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "ok":true,
      "message":"Cancelling deployment"
    }
}
```

Cancel a live stack deployment

<aside class="notice">
<b>Scope:</b> <i>redeploy</i>
</aside>

### HTTP Request

`DELETE /stacks/{stack_id}/deployments/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | integer | The deployment ID | `112`
