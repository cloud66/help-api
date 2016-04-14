# Jobs

## Jobs list

```ruby
stack_id = '5999b763474b0eafa5fafb64bff0ba80'
response = token.get("#{api_url}/stacks/#{stack_id}/jobs.json")

puts JSON.parse(response.body)['response']
```

```http
GET /stacks/{id}/jobs HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "response":[
     {
       "uid":"98ee5a9b93919d9b63bd5377636675bd",
       "name":"rake_test",
       "type":"RakeJob",
       "cron":null,
       "status":2,
       "params":{"task":"db:migrate"},
       "created_at":"2016-02-01 13:37:07 UTC",
       "updated_at":"2016-02-01 13:37:07 UTC"
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

Get list of all jobs of a stack.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/jobs`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | stack UID | `5999b763474b0eafa5fafb64bff0ba80`

## Run a job

```ruby
stack_id = '5999b763474b0eafa5fafb64bff0ba80'
id = 98ee5a9b93919d9b63bd5377636675bd
response = token.get("#{api_url}/stacks/#{stack_id}/jobs/{job_id}/run_now.json")

puts JSON.parse(response.body)['response']
```

```http
POST /stacks/{stack_id}/jobs/{job_id}/run_now HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":2593,
      "user":"test@example.com",
      "resource_type":"stack",
      "action":"job_run_now",
      "resource_id":"1602",
      "started_via":"api",
      "started_at":"2016-02-04T12:52:24Z",
      "finished_at":null,
      "finished_success":null,
      "finished_message":null
    }
}
```

Run the job.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`POST /stacks/{stack_id}/jobs/{job_id}/run_now`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
job_id | **required** | string | Job ID | `98ee5a9b93919d9b63bd5377636675bd`
job_args | **optional** | string | Arguments passed to the command | `Arg1`