# Accounts

## Accounts list

```ruby
response = token.get("#{api_url}/accounts.json")

puts JSON.parse(response.body)['response']
```

```http
GET /accounts HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": [
    {
      "id": 139,
      "owner": "test@cloud66.com",
      "created_at_iso": "2013-06-19T11:08:03Z",
      "updated_at_iso": "2014-02-20T12:55:58Z",
      "stack_count": 2,
      "used_clouds": ["digitalocean","rackspace"]
    }
  ],
  "count":1,
  "pagination":{
    "previous": null,
    "next": null,
    "current": 1,
    "per_page": 30,
    "count": 1,
    "pages": 1
  }
}
```

Get a list of accounts that caller belongs to.

<aside class="notice">
<b>Scope:</b> <i>users</i>
</aside>

### HTTP Request

`GET /accounts`

## Account

```ruby
id = 1
response = token.get("#{api_url}/accounts/#{id}.json")

puts JSON.parse(response.body)['response']
```

```http
GET /accounts/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
          "id": 139,
          "owner": "test@cloud66.com",
          "created_at_iso": "2013-06-19T11:08:03Z",
          "updated_at_iso": "2014-02-20T12:55:58Z",
          "stack_count": 2,
          "used_clouds": ["digitalocean","rackspace"]
    }
}
```

Get information about an account.

<aside class="notice">
<b>Scope:</b> <i>users</i>
</aside>

### HTTP Request

`GET /accounts/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The account ID | `1`
