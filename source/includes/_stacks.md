# Stacks
<aside class="notice">
Most interactions with the Cloud 66 API are performed at the stack level. Using the Stacks resource, you can list stacks and view stack details, but you can only create, update, or delete stacks using the UI dashboard.
</aside>

### Methods

Using the Stacks endpoint, you can submit requests using the following methods.

* List all stacks
* View a stack
* Create a new stack
* List all stack actions
* View a stack action
* Perform a stack action


## Stack List

```http
GET /stacks HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "response": [
        {
            "uid": "5999b763474b0eafa5fafb64bff0ba80",
            "name": "Awesome App",
            "git": "http://github.com/cloud66-samples/awesome-app.git",
            "git_branch": "fig",
            "environment": "production",
            "cloud": "DigitalOcean",
            "fqdn": "awesome-app.dev.c66.me",
            "language": "ruby",
            "framework": "rails",
            "status": 1,
            "health": 3,
            "last_activity": "2014-08-14T01:46:53+00:00",
            "last_activity_iso": "2014-08-14T01:46:53+00:00",
            "maintenance_mode": false,
            "has_loadbalancer": false,
            "created_at": "2014-08-14 00:38:14 UTC",
            "updated_at": "2014-08-14 01:46:52 UTC",
            "deploy_directory": "/var/deploy/awesome_app",
            "cloud_status": "partial",
            "created_at_iso": "2014-08-14T00:38:14Z",
            "updated_at_iso": "2014-08-14T01:46:52Z",
            "redeploy_hook": "http://hooks.cloud66.com/stacks/redeploy/b806f1c3344eb3aa2a024b23254b75b3/6d677352a6b2eefec6e345ee2b491521"
        }
    ],
    "count": 1,
    "pagination": {
        "previous": null,
        "next": null,
        "current": 1,
        "per_page": 30,
        "count": 1,
        "pages": 1
    }
}
```

Retrieves a paged list of all the stack objects the user can access.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks`

### The stack object

| Property | Data type | Description | Sample value |
| ---------- | ------------ | -------------------------------- | ------------- |
| uid | string | The unique identifier of the stack. | 5999b763474b0eafa5fafb64bff0ba80 |
| name | string | The name defined for the stack. | My Awesome App |
| git | string | The git repository URL associated with the stack. | http://github.com/mysamples/awesome-app.git |
| git_branch | string | The git repository branch associated with the stack. | fig |
| environment | string | The environment associated with the stack. | production |
| cloud | string | The cloud provider associated with the stack. | DigitalOcean |
| fqdn | string | The fully qualified namespace of the stack. | awesome-app.dev.c66.me |
| language | string | The programming language of the stack. | ruby |
| framework | string | The framework used for the stack. | rails |
| status | int | The current status code for the stack. | 1 |
| health | int | The current health code for the stack. | 3 |
| last_activity | datetime | The date and time the last action was performed for the stack, in UTC datetime. | 2014-08-14T01:46:53+00:00 |
| last_activity_iso | datetime | The date and time the last action was performed for the stack, in UTC datetime | 2014-08-14T01:46:53+00:00 |
| maintenance mode | bool | Whether the stack currently has maintenance mode enabled. | false |
| has_loadbalancer | bool | Whether the stack has an associated load balancer add-in. | false |
| created_at | datetime | The date and time the stack was created, in iso8601 format | 2014-09-01T19:08:05Z |
| updated_at | datetime | The date and time the stack was last modified, in iso8601 format | 2014-09-01T19:18:05Z |
| deploy_directory | string | The target directory for stack deployment. | /var/deploy/awesome_app |
| cloud_status | string | The current cloud provider status associated with the stack. | partial |
| redeploy_hook | string | If applicable, the deploy hook URL associated with the stack. | http://hooks.cloud66.com/stacks/redeploy/ b806f1c3344eb3aa2a024b23254b75b3/ 6d677352a6b2eefec6e345ee2b491521 |

## Stack

```http
GET /stacks HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
"response":
  {
    "uid": "5999b763474b0eafa5fafb64bff0ba80",
      "name": "Awesome App",
      "git": "http://github.com/cloud66-samples/awesome-app.git",
      "git_branch": "fig",
      "environment": "production",
      "cloud": "DigitalOcean",
      "fqdn": "awesome-app.dev.c66.me",
      "language": "ruby",
      "framework": "rails",
      "status": 1,
      "health": 3,
      "last_activity": "2014-08-14T01:46:53+00:00",
      "last_activity_iso": "2014-08-14T01:46:53+00:00",
      "maintenance_mode": false,
      "has_loadbalancer": false,
      "created_at": "2014-08-14 00:38:14 UTC",
      "updated_at": "2014-08-14 01:46:52 UTC",
      "deploy_directory": "/var/deploy/awesome_app",
      "cloud_status": "partial",
      "created_at_iso": "2014-08-14T00:38:14Z",
      "updated_at_iso": "2014-08-14T01:46:52Z",
      "redeploy_hook": "http://hooks.cloud66.com/stacks/redeploy/b806f1c3344eb3aa2a024b23254b75b3/6d677352a6b2eefec6e345ee2b491521"
  }
}
```

Retrieve the details of the stack specified in the request.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | true | string | Unique identifier of the stack | `5999b763474b0eafa5fafb64bff0ba80`

### Stack status values

| Status | Code | Description |
| ----------- | :---: | ----------------------------------------- |
| STK_QUEUED | 0 | Pending analysis |
| STK_SUCCESS | 1 | Deployed successfully |
| STK_FAILED | 2 | Deployment failed |
| STK_ANALYSING | 3 | Analyzing |
| STK_ANALYSED | 4 | Analyzed |
| STK_QUEUED_FOR_DEPLOYING | 5 | Queued for deployment |
| STK_DEPLOYING | 6 | Deploying |
| STK_TERMINAL_FAILURE | 7 | Unable to analyze |

### Stack health status values

| Status | Code | Description |
| ----------- | :---: | ------------------------------------------ |
| HLT_UNKNOWN | 0 | Unknown |
| HLT_BUILDING | 1 | Building |
| HLT_PARTIAL | 2 | Impaired |
| HLT_OK | 3 | Healthy |
| HLT_BROKEN | 4 | Failed |

## Stack Create

```http
POST /stacks HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{ "response":
    {
        "id":10,
        "user":"test@cloud66.com",
        "resource_type":"stack",
        "action":"stack_create",
        "resource_id":"283",
        "started_via":"api",
        "started_at":"2015-09-01T19:08:05Z",
        "finished_at":null,
        "finished_success":null,
        "finished_message":null
    }
}
```

Create and build a new docker stack. Either manifest definition, or cloud, region, size and buildtype must be passed as params.

<aside class="notice">
<b>Scope:</b> <i>redeploy</i>
</aside>

### HTTP Request

`POST /stacks`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
name | true | string | New stack name | `new_stack_name`
environment | true | string | New stack environment | `production`
service_yaml | true | string | The services definition of the new docker stack | `service_yaml_serialised`
manifest_yaml | false | string | The manifest definition of the new docker stack | `manifest_yaml_serialised`
cloud | false | string | Cloud provider to create servers in | `aws`
region | false | string | Region within the cloud to create servers in | `us-east-1`
build_type | false | string | Deploy all services to "single" or "multi" servers | `multi`

## Stack Action list

```http
GET /stacks/{id}/actions HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
        [
    {
      "id":10,
      "user":"test@cloud66.com",
      "resource_type":"stack",
      "action":"clear_caches",
      "resource_id":"283",
      "started_via":"api",
      "started_at":
      "2014-09-01T19:08:05Z",
      "finished_at":"2014-09-01T19:08:09Z",
      "finished_success":true,
      "finished_message":null
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

Retrieve a paged list of all asynchronous actions performed for the stack specified in the request.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/actions`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | true | string | Unique identifier of the stack | `5999b763474b0eafa5fafb64bff0ba80`

### The stack action object

| Property | Data type | Description | Sample value |
| ------------- | --------- | ----------------------------------- | ---------------- |
| id | int | The numeric identifier of the stack action. Identifiers increment by one for each performed action. | 10 |
| user | string | The email address of the user who performed the stack action. | hello@cloud66.com |
| resource_type | string | The resource for which the action was performed, which is stack in this case. | stack |
| action | string | The action that was performed for the stack. | restart |
| resource_id | int | The unique ID of the resource | 283 |
| started_via | string | The process that initiated the action, which is the UI, API, or command line. | api |
| started_at | datetime | The date and time the action was initiated, in UTC datetime. | 2014-09-01T19:08:05Z |
| finished_at | datetime | The date and time the action was completed, in UTC datetime. | 2014-09-01T19:08:09Z |
| finished_success | bool | Whether the action completed successfully. | true |
| finished_message | string | If applicable, the system message associated with the completed action. | null |

## Stack Action

```http
GET /stacks/{stack_id}/actions/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":10,
      "user":"test@cloud66.com",
      "resource_type":"stack",
      "action":"clear_caches",
      "resource_id":"283",
      "started_via":"api",
      "started_at":
      "2014-09-01T19:08:05Z",
      "finished_at":"2014-09-01T19:08:09Z",
      "finished_success":true,
      "finished_message":null
    }
}
```

Retrieve the details of an asynchronous action performed for the the stack specified in the request based on the supplied action ID.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/actions/{id}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | Unique identifier of the stack | `5999b763474b0eafa5fafb64bff0ba80`
id | true | integer | Identifier of the asynchronous action | `4153`

## Run Stack action

```http
POST /stacks/{stack_id}/actions HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":10,
      "user":"test@cloud66.com",
      "resource_type":"stack",
      "action":"clear_caches",
      "resource_id":"283",
      "started_via":"api",
      "started_at":"2014-09-01T19:08:05Z",
      "finished_at":null,
      "finished_success":null,
      "finished_message":null
    }
}
```

Perform an asynchronous action for the stack specified in the request. You can use this method to restart the stack, clear the stack's cache, or enable maintenance mode.

<aside class="notice">
<b>Scope:</b> <i>redeploy</i>
</aside>

### HTTP Request

`POST /stacks/{stack_id}/actions`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | Unique identifier of the stack | `5999b763474b0eafa5fafb64bff0ba80`
command | true | string | The action to perform for the stack. Valid values are clear_caches, maintenance_mode, and restart. | `restart`

| Command | Comments | Extra Parameters |
| ---------- | ---------- | ---------------- |
| maintenance_mode | Enable to Disable maintenance mode for a stack. | value=1 for enable, value=0 for disable |
| clear_caches | Clear git caches for the stack | None |
| restart | Restarts all stack components (nginx, db, etc.) | None |
