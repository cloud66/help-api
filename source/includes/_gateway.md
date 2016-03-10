# Gateways

## Gateways list

```ruby
account_id = '1234'
response = token.get("#{api_url}/accounts/#{account_id}/gateways.json")

puts JSON.parse(response.body)['response']
```

```http
GET /accounts/{account_id}/gateways HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "response":[
      {
        "id"=>1,
        "name"=>"aws_bastion",
        "username"=>"ec2-usr",
        "address"=>"1.1.1.1",
        "private_ip"=>"2.2.2.2",
        "ttl"=>"2016-02-01T14:46:38Z",
        "content"=>"N/A",
        "created_at_iso"=>"2016-02-01T14:37:05Z",
        "updated_at_iso"=>"2016-02-01T14:47:01Z",
        "created_by"=>"user1@cloud66.com",
        "updated_by"=>"user1@cloud66.com"
      }
   ],
   "count":1,
   "pagination":{
      "previous":null,
      "next":null,
      "current":1,
      "per_page":30,
      "count":1,
      "pages":1
   }
}
```

Get a list of all the gateways of the account

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /accounts/{account_id}/gateways`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
account_id | **required** | string | The account id | `12345`

## Gateway Create

```ruby
account_id = '1234'
response = token.post("#{api_url}/accounts/#{account_id}/gateways.json", {body: {:name => 'aws_test', :username => 'ec2-usr', :address => '1.1.1.1', :ttl => 3600, :private_ip => '2.2.2.2', :content => 'xxxxxxxxxxxxx'}})

puts JSON.parse(response.body)['response']
```

```http
POST /accounts/{account_id}/gateways HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{ "response":
    {
        "ok": true
    }
}

```

Create a new gateway under the account.  `name` must be passed as params. You can also specify `username` , `address`, `ttl`, `private_ip` and `content` as params.

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`POST /accounts/{account_id}/gateways`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
account_id | **required** | string | The account id | `12345`
name | **required** | string | New gateway name | `new_gateway_name`
username | optional | string | Username of bastion server | `ec2-usr`
address | optional | string | Public IP or DNS address of bastion server | `1.1.1.1`
ttl | optional | integer | The number of seconds you want the gateway available | `3600`
private_ip | optional | string | Private IP or DNS address of bastion server | `2.2.2.2`
content | optional | string | The content of private key of bastion server | `xxxxxxxx`

## Update Gateway

```ruby
account_id = '1234'
id = 1

response = token.put("#{api_url}/accounts/#{account_id}/gateways/#{id}.json", {body: { :name => 'new_name', :username => 'ubuntu' , :address => '1.2.3.4' }})

puts JSON.parse(response.body)['response']

```

```http
PUT /accounts/{account_id}/gateways/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
{ "response":
    {
        "ok": true
    }
}
```

Update gateway information.

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`PUT /accounts/{account_id}/gateways/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The gateway id | `1`
account_id | **required** | string | The account id | `12345`
name | optional | string | Gateway name | `new_gateway_name`
username | optional | string | Username of bastion server | `ec2-usr`
address | optional | string | Public IP or DNS address of bastion server | `1.1.1.1`
ttl | optional | integer | The number of seconds you want the gateway available | `3600`
private_ip | optional | string | Private IP or DNS address of bastion server | `2.2.2.2`
content | optional | string | The content of private key of bastion server | `xxxxxxxx`

## Delete Gateway

```ruby
account_id = '1234'
id = 1
response = token.delete("#{api_url}/accounts/#{account_id}/gateways/#{id}.json")
puts JSON.parse(response.body)['response']
```

```http
DELETE /accounts/{account_id}/gateways/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

Delete a gateway

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`DELETE /accounts/{account_id}/gateways/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | integer | The gateway id | `1`
account_id | **required** | string | The account id | `12345`
