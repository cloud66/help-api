# Docker Image Repositories

## Docker Image Repository list

```ruby
response = token.get("#{api_url}/image_repositories.json")

puts JSON.parse(response.body)['response']
```

```http
GET /image_repositories HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": [
    {
      "id": 2,
      "url": "https://quay.io",
      "username": "cloud66",
      "email": "kickass@company.com",
      "created_at_iso": "2015-12-03T14:29:51Z",
      "updated_at_iso": "2015-12-03T14:29:51Z"
    },
    {
      "id": 3,
      "url": "https://index.dockerub.com",
      "username": "cloud66",
      "email": "eng@company.com",
      "created_at_iso": "2015-12-03T14:30:17Z",
      "updated_at_iso": "2015-12-03T14:30:17Z"
    }
  ],
  "count": 2,
  "pagination": {
    "previous": null,
    "next": null,
    "current": 1,
    "per_page": 30,
    "count": 2,
    "pages": 1
  }
}
```

Get list of all Docker image repositories for an account

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`GET /image_repositories`

## Docker Image Repository

```ruby
id = 3
response = token.get("#{api_url}/image_repositories/#{id}.json")

puts JSON.parse(response.body)['response']
```

```http
GET /image_repositories/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": {
    "id": 3,
    "url": "https://index.dockerub.com",
    "username": "cloud66",
    "email": "eng@company.com",
    "created_at_iso": "2015-12-03T14:30:17Z",
    "updated_at_iso": "2015-12-03T14:30:17Z"
  }
}
```

Get information of a single Docker image repository

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`GET /image_repositories/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The Docker image repository ID | `3`

## Add Docker Image Repository

```ruby
response = token.post("#{api_url}/image_repositories.json", {body: {:url => 'https://quay.io', :email => 'kickass@company.com', :username => 'Kickass', :password => 'supersecret'}})

puts JSON.parse(response.body)['response']
```

```http
POST /image_repositories HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": {
    "id": 283,
    "url": "https://quay.io",
    "username": "Kickass",
    "email": "kickass@company.com",
    "created_at_iso": "2015-12-03T14:30:17Z",
    "updated_at_iso": "2015-12-03T14:30:17Z"
  }
}
```

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`POST /image_repositories`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
url | **required** | string | Repository URL | `https://quay.io`
email | **required** | string | User email address | `kickass@company.com`
username | **required** | string | Username | `Kickass`
password | **required** | string | Password | `supersecret`

## Edit Docker Image Repository

```ruby
id = 283
response = token.put("#{api_url}/image_repositories/#{id}.json", {body: {:url => 'https://quay.io', :email => 'kickass_squared@company.com', :username => 'KickassSquared', :password => 'supersecret'}})

puts JSON.parse(response.body)['response']
```

```http
PUT /image_repositories/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": {
    "id": 283,
    "url": "https://quay.io",
    "username": "KickassSquared",
    "email": "kickass_squared@company.com",
    "created_at_iso": "2015-12-03T14:30:17Z",
    "updated_at_iso": "2015-12-03T14:30:17Z"
  }
}
```

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`PUT /image_repositories/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The Docker image repository ID | `283`
url | **required** | string | Repository URL | `https://quay.io`
email | **required** | string | User email address | `kickass_squared@company.com`
username | **required** | string | Username | `KickassSquared`
password | **required** | string | Password | `supersecret`

## Delete Docker Image Repository

```ruby
id = 283
response = token.delete("#{api_url}/image_repositories/#{id}.json")

puts JSON.parse(response.body)['response']
```

```http
DELETE /image_repositories/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": {
    "ok": true
  }
}
```

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`DELETE /image_repositories/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The Docker image repository ID | `283`
