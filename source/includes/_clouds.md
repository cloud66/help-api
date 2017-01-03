# Clouds

## Cloud list

```ruby
response = token.get("#{api_url}/clouds.json")

puts JSON.parse(response.body)['response']
```

```http
GET /clouds HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "response":[
       {
          "name":"aws",
          "display_name":"AWS",
          "regions":[
             {
                "id":"us-east-1",
                "name":"US East (Northern Virginia)"
             },
             {
                "id":"us-east-2",
                "name":"US East (Ohio)"
             },
             {
                "id":"us-west-1",
                "name":"US West (Northern California)"
             },
             {
                "id":"us-west-2",
                "name":"US West (Oregon)"
             },
             {
                "id":"ca-central-1",
                "name":"Canada (Central)"
             },
             {
                "id":"sa-east-1",
                "name":"South America (Sao Paulo, Brazil)"
             },
             {
                "id":"eu-central-1",
                "name":"Europe (Frankfurt, Germany)"
             },
             {
                "id":"eu-west-1",
                "name":"Europe (Dublin, Ireland)"
             },
             {
                "id":"eu-west-2",
                "name":"Europe (London)"
             },
             {
                "id":"ap-southeast-1",
                "name":"Asia Pacific (Singapore)"
             },
             {
                "id":"ap-northeast-1",
                "name":"Asia Pacific (Tokyo)"
             },
             {
                "id":"ap-southeast-2",
                "name":"Asia Pacific (Sydney)"
             },
             {
                "id":"ap-south-1",
                "name":"Asia Pacific (Mumbai)"
             }
          ],
          "server_sizes":[
             {
                "id":"t1.micro",
                "name":"Micro instance (t1.micro)"
             },
             {
                "id":"t2.micro",
                "name":"General purpose (t2.micro)"
             },
             {
                "id":"t2.small",
                "name":"General purpose (t2.small)"
             },
             {
                "id":"t2.medium",
                "name":"General purpose (t2.medium)"
             },
             {
                "id":"m1.small",
                "name":"General purpose (m1.small)"
             },
             {
                "id":"m1.medium",
                "name":"General purpose (m1.medium)"
             },
             {
                "id":"m1.large",
                "name":"General purpose (m1.large)"
             },
             {
                "id":"m1.xlarge",
                "name":"General purpose (m1.xlarge)"
             },
             {
                "id":"m3.medium",
                "name":"General purpose (m3.medium)"
             },
             {
                "id":"m3.large",
                "name":"General purpose (m3.large)"
             },
             {
                "id":"m3.xlarge",
                "name":"General purpose (m3.xlarge)"
             },
             {
                "id":"m3.2xlarge ",
                "name":"General purpose (m3.2xlarge )"
             },
             {
                "id":"c1.medium",
                "name":"Compute optimized (c1.medium)"
             },
             {
                "id":"c1.xlarge",
                "name":"Compute optimized (c1.xlarge)"
             },
             {
                "id":"c3.large",
                "name":"Compute optimized (c3.large)"
             },
             {
                "id":"c3.xlarge",
                "name":"Compute optimized (c3.xlarge)"
             },
             {
                "id":"c3.2xlarge",
                "name":"Compute optimized (c3.2xlarge)"
             },
             {
                "id":"c3.4xlarge",
                "name":"Compute optimized (c3.4xlarge)"
             },
             {
                "id":"c3.8xlarge",
                "name":"Compute optimized (c3.8xlarge)"
             },
             {
                "id":"cc2.8xlarge",
                "name":"Compute optimized (cc2.8xlarge)"
             },
             {
                "id":"m2.xlarge",
                "name":"Memory optimized (m2.xlarge)"
             },
             {
                "id":"m2.2xlarge",
                "name":"Memory optimized (m2.2xlarge)"
             },
             {
                "id":"m2.4xlarge",
                "name":"Memory optimized (m2.4xlarge)"
             },
             {
                "id":"cr1.8xlarge",
                "name":"Memory optimized (cr1.8xlarge)"
             },
             {
                "id":"hi1.4xlarge",
                "name":"Storage optimized (hi1.4xlarge)"
             },
             {
                "id":"hs1.8xlarge",
                "name":"Storage optimized (hs1.8xlarge)"
             },
             {
                "id":"cg1.4xlarge",
                "name":"GPU instances (cg1.4xlarge)"
             },
             {
                "id":"g2.2xlarge",
                "name":"GPU instances (g2.2xlarge)"
             },
             {
                "id":"i2.xlarge",
                "name":"Storage optimized (i2.xlarge)"
             },
             {
                "id":"i2.2xlarge",
                "name":"Storage optimized (i2.2xlarge)"
             },
             {
                "id":"i2.4xlarge",
                "name":"Storage optimized (i2.4xlarge)"
             },
             {
                "id":"i2.8xlarge",
                "name":"Storage optimized (i2.8xlarge)"
             },
             {
                "id":"r3.large",
                "name":"Memory optimized (r3.large)"
             },
             {
                "id":"r3.xlarge",
                "name":"Memory optimized (r3.xlarge)"
             },
             {
                "id":"r3.2xlarge",
                "name":"Memory optimized (r3.2xlarge)"
             },
             {
                "id":"r3.4xlarge",
                "name":"Memory optimized (r3.4xlarge)"
             },
             {
                "id":"r3.8xlarge",
                "name":"Memory optimized (r3.8xlarge)"
             }
          ]
       },
       {
          "name":"digitalocean",
          "display_name":"DigitalOcean",
          "regions":[
             {
                "id":"ams1",
                "name":"Amsterdam, Netherlands",
                "old_id":"2"
             },
             {
                "id":"ams2",
                "name":"Amsterdam 2, Netherlands",
                "old_id":"5"
             },
             {
                "id":"ams3",
                "name":"Amsterdam 3, Netherlands",
                "old_id":"9"
             },
             {
                "id":"nyc1",
                "name":"New York, US",
                "old_id":"1"
             },
             {
                "id":"nyc2",
                "name":"New York 2, US",
                "old_id":"4"
             },
             {
                "id":"nyc3",
                "name":"New York 3, US",
                "old_id":"8"
             },
             {
                "id":"sfo1",
                "name":"San Francisco, US",
                "old_id":"3"
             },
             {
                "id":"sgp1",
                "name":"Singapore",
                "old_id":"6"
             },
             {
                "id":"lon1",
                "name":"London, UK",
                "old_id":"7"
             }
          ],
          "server_sizes":[
             {
                "id":"512mb",
                "name":"512MB - 1 CPU"
             },
             {
                "id":"1gb",
                "name":"1GB - 1 CPU"
             },
             {
                "id":"2gb",
                "name":"2GB - 2 CPU"
             },
             {
                "id":"4gb",
                "name":"4GB - 2 CPU"
             },
             {
                "id":"8gb",
                "name":"8GB - 4 CPU"
             },
             {
                "id":"16gb",
                "name":"16GB - 8 CPU"
             },
             {
                "id":"32gb",
                "name":"32GB - 12 CPU"
             },
             {
                "id":"48gb",
                "name":"48GB - 16 CPU"
             },
             {
                "id":"64gb",
                "name":"64GB - 20 CPU"
             }
          ]
       }
    ],
    "count":2,
    "pagination":{
       "previous":null,
       "next":null,
       "current":1,
       "per_page":30,
       "count":2,
       "pages":1
    }
}
```

Get list of all clouds of account

<aside class="notice">
<b>Scope:</b> <i>redeploy</i>
</aside>

### HTTP Request

`GET /clouds`

## Cloud

```ruby
cloud_id = 'digitalocean'
response = token.get("#{api_url}/clouds/#{cloud_id}.json")

puts JSON.parse(response.body)['response']
```

```http
GET /clouds/{cloud_id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
     {
        "name":"digitalocean",
        "display_name":"DigitalOcean",
        "regions":[
           {
              "id":"ams1",
              "name":"Amsterdam, Netherlands",
              "old_id":"2"
           },
           {
              "id":"ams2",
              "name":"Amsterdam 2, Netherlands",
              "old_id":"5"
           },
           {
              "id":"ams3",
              "name":"Amsterdam 3, Netherlands",
              "old_id":"9"
           },
           {
              "id":"nyc1",
              "name":"New York, US",
              "old_id":"1"
           },
           {
              "id":"nyc2",
              "name":"New York 2, US",
              "old_id":"4"
           },
           {
              "id":"nyc3",
              "name":"New York 3, US",
              "old_id":"8"
           },
           {
              "id":"sfo1",
              "name":"San Francisco, US",
              "old_id":"3"
           },
           {
              "id":"sgp1",
              "name":"Singapore",
              "old_id":"6"
           },
           {
              "id":"lon1",
              "name":"London, UK",
              "old_id":"7"
           }
        ],
        "server_sizes":[
           {
              "id":"512mb",
              "name":"512MB - 1 CPU"
           },
           {
              "id":"1gb",
              "name":"1GB - 1 CPU"
           },
           {
              "id":"2gb",
              "name":"2GB - 2 CPU"
           },
           {
              "id":"4gb",
              "name":"4GB - 2 CPU"
           },
           {
              "id":"8gb",
              "name":"8GB - 4 CPU"
           },
           {
              "id":"16gb",
              "name":"16GB - 8 CPU"
           },
           {
              "id":"32gb",
              "name":"32GB - 12 CPU"
           },
           {
              "id":"48gb",
              "name":"48GB - 16 CPU"
           },
           {
              "id":"64gb",
              "name":"64GB - 20 CPU"
           }
        ]
     }
}
```

Get information about a single cloud of an account

<aside class="notice">
<b>Scope:</b> <i>redeploy</i>
</aside>

### HTTP Request

`GET /clouds/{cloud_id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
cloud_id | **required** | string | The cloud ID (name) | `digitalocean`
