---
title: API Reference

language_tabs:
  - shell: cURL
  - ruby: Ruby

toc_footers:
  - <a href='https://app.cloud66.com/api/3'> https://app.cloud66.com/api/3</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - cloud_vendor_instances
  - stacks
  - deployments

search: true
---

# Introduction
[Cloud 66](http://www.cloud66.com) is a full stack container management as a service. It allows you to build, provision, configure and manage Docker containers on your own server on any cloud. You can find more information on Cloud 66 on [our help site](http://help.cloud66.com/).

## Resource model
The Cloud 66 API is organised around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). It is designed to have predictable, resource-oriented URLs and to use HTTP response codes to indicate API errors.

We use built-in HTTP features, like HTTP authentication and HTTP verbs, which can be understood by off-the-shelf HTTP clients.

[JSON](http://www.json.org/) will be returned in all responses from the API, including errors (though if you're using API bindings, we will convert the response to the appropriate language-specific object).

## Authentication
Cloud 66 uses [OAuth2](http://oauth.net/2/) to authenticate users and grant access to stacks and redeployments. To use it, you need an OAuth 2.0 compatible client. To submit API requests, you must pass an OAuth token. An OAuth token functions as a complete authentication request, acting as a substitute for a username and password pair. Because of this, it is absolutely essential that you keep your OAuth tokens secure.

To authenticate your requests with OAuth you need to send a bearer authorization header with your request. This is the preferred method of authenticating because it completes the authorization request in the header portion, away from the actual request.

Usually, you use a language binding (like a [Ruby gem](https://rubygems.org/) or [Go package](http://golang.org/pkg/)) to deal with the OAuth authentication. Alternatively, you can include the OAuth authentication token in the header of each request:

`Authorization: bearer 5262d64b892e8d4341000001`

You can generate an OAuth token by visiting the [Apps](https://app.cloud66.com/oauth/authorized_applications) , under your Account.

### How to authenticate with OAuth2
You can generate an OAuth token using the Your Account > [Apps](https://app.cloud66.com/oauth/authorized_applications) area of the Cloud 66 user interface or using the API.

**Step 1 - Redirect users to request Cloud 66 access**

`GET https://app.cloud66.com/oauth/authorize`

| Parameter | Description | Presence |
| ----------- | ---------------------------- | --------- |
| client_id | The client ID you received from Cloud 66 when you registered. | Required |
| redirect_url | URL in your app where users will be sent after authorization. | Required |
| scope | Comma separated list of scopes. | Optional |

**Step 2 - Cloud 66 redirects back to your site**

If the user accepts your request, Cloud 66 redirects back to your site with a temporary code in a code parameter as well as the state you provided in the previous step in a state parameter. If the states don’t match, the request has been created by a third party and the process should be aborted.

Exchange this for an access token:

`POST https://app.cloud66.com/oauth/token`

| Parameter | Description | Presence |
| ----------- | ---------------------------- | --------- |
| client_id | The client ID you received from Cloud 66 when you registered. | Required |
| redirect_url | URL in your app where users will be sent after authorization. | Optional |
| client_secret | The client secret you received from Cloud 66 when you registered. | Required |

**Response**
By default, the response will take the following form:

`access_token=e72e16c7e42f292c6912e7710c838347ae178b4a&amp;token_type=bearer`  
`Accept: application/json {"access_token":"e72e16c7e42f292c6912e7710c838347ae178b4a","token_type":"bearer"}`

**Step 3 - Use the access token to access the API**

The access token allows you to make requests to the API on behalf of a user.

`GET "https://app.cloud66.com/api/3/stack.json" -H "Authorization: Bearer e72e...b4a"`

## Scoped access
A user’s scope defines the limits of the actions the user can perform with the Cloud 66 API. The user’s scope is encrypted as part of the OAuth access token. Users cannot submit requests not allowed by their defined scopes.

For the web flow, requested scopes be displayed to the user on the authorize form.

**(no scope)**
Users with this scope have public read-only access and can view limited stack information.

**public**
Users with this scope have public read-only access and can view limited stack information.

**redeploy**
Users with this scope can redeploy any stacks they can access.

**jobs**
Users with this scope can view the scheduled jobs for the stacks they can access.

**users**
Users with this scope can manage other users’ mobile devices.

**admin**
Users with this scope can set and manage settings for the servers they can access.

_NOTE: Your application can request scopes in the initial redirection. You can specify multiple scopes by separating them with a space character._

`
https://app.cloud66.com/oauth/authorize?client_id=...&scope=public+redeploy
`

## Example

```ruby
require 'rubygems'
require 'oauth2'
require 'json'

base = 'https://app.cloud66.com'
api_url = 'https://app.cloud66.com/api/3'

if File.exists? '/tmp/cloud66_oauth_test.json'
    config = JSON.parse(File.read('/tmp/cloud66_oauth_test.json'))
    client = OAuth2::Client.new(config['app_id'], config['app_secret'], :site => base)
    token = OAuth2::AccessToken.new(client, config['token'])
else
    client = OAuth2::Client.new(ENV['APP_ID'], ENV['APP_SECRET'], :site => base)
    puts client.auth_code.authorize_url(:redirect_uri => 'urn:ietf:wg:oauth:2.0:oob', :scope => 'public admin redeploy')

    puts "Enter the code:"
    code = gets.strip

    token = client.auth_code.get_token(code, :redirect_uri => "urn:ietf:wg:oauth:2.0:oob")

    # save it
    File.write('/tmp/cloud66_oauth_test.json', { :app_id => ENV['APP_ID'], :app_secret => ENV['APP_SECRET'], :token => token.token }.to_json)
end

# Now you can use the token to call API methods, like:

# List all the stacks
response = token.get("#{api_url}/stacks.json")

# list all the servers in the stack
stack_uid = 'ENTER_STACK_UID'
response = token.get("#{api_url}/stacks/#{stack_uid}/servers.json")

# show the response (no error handling)
puts JSON.parse(response.body)['response']
```

```shell
# Simple GET
# Get list of stacks:
curl -X GET "https://app.cloud66.com/api/3/stacks.json" -H "Authorization: Bearer 4c9c9b1111"

# GET with some params
# Get list of all `mysql` backups in `1345` backup group:
curl -X GET "https://app.cloud66.com/api/3/stacks/f196c5b41758cb7977620d49eb1492ef/backups.json" -H "Authorization: Bearer 4c9c9b1111" -d group=1345 -d db_type=mysql

# POST
# Add a new iPhone application to user ID 18 with 'wertqy' as a token:
curl -X POST "https://app.cloud66.com/api/3/users/18/devices.json" -H "Authorization: Bearer 4c9c9b1111" -d token=wertqy -d device_type=1 -d sub_type=1

# PUT
# Update the type of device with token 'wertqy' to iPad:
curl -X PUT "https://app.cloud66.com/api/3/users/18/devices/wertqy.json" -H "Authorization: Bearer 4c9c9b1111" -d device_type=1 -d sub_type=2

# DELETE
# Delete device with token 'wertqy':
curl -X DELETE "https://app.cloud66.com/api/3/users/18/devices/wertqy.json" -H "Authorization: Bearer 4c9c9b1111"
```

### Ruby

This example shows how to get the first token using the Application (Client) ID and Secret. This is using `urn:ietf:wg:oauth:2.0:oob` for commandline tools.

Once you have the code, you can apply for a token. Tokens issued by the API server do not expire and are valid until the user revokes their access. You can see how to store and retrieve the token for future use in this example.

### cURL

For example, you can get lists of stacks with this command:

`curl -X GET "https://app.cloud66.com/api/3/stacks.json"  -H "Authorization: Bearer PERSONAL_ACCESS_TOKEN"``

You can use your **personal access token** to call the API with cURL - it just needs to be passed in as a header.

<aside class="notice">
You can find your <b>personal access token</b> in your Cloud 66 Accounts page, under <i>Authorized Applications</i>.
</aside>

Assuming that your personal access token is `4c9c9b1111`, these are some examples for using cURL:

### Go Example

You can use the [Cloud 66 Go library repository](https://github.com/cloud66/cloud66) if you want to use Go.

## Synchronous vs. asynchronous requests
The Cloud 66 API uses both synchronous and asynchronous methods. Asynchronous methods are specified in the documentation for the associated calls; all others are generally considered synchronous.

**Synchronous** methods will wait for the server to return a response for the request before it will continue processing. Your application will not perform any additional actions until it receives a response from the server.

**Asynchronous** methods will submit the request to the server, but the application will not wait for a response from the server to continue processing. When the server returns a response, the application can execute a callback function to retrieve the response object, but will continue processing until the response is received.

## Date formats
Cloud 66 accepts and returns date values according to the ISO 8601 standard. Combined date and time values appear in UTC including local time zone offsets. For example: `2014-06-15T14:13:18+00:00`

## Rate limiting
The Cloud 66 API can receive a maximum of 3,000 requests per user per hour. When the request level reaches the maximum rate, subsequent requests will return a `503: throttled` HTTP status message and the user must retry the request in the next hourly interval.

## Standard HTTP response statuses
Requests made using the Cloud 66 API can return any of the following response status codes.

| Code | Message | Description |
| :---: | ---------- | ---------------------------------------------------- |
| 200 | ok | The request completed successfully. |
| 400 | bad_request | The system cannot parse the request syntax. It might be missing required parameters or include an invalid value. |
| 401 | unauthenticated | No authentication token was passed in the request. |
| 402 | trial_expired | The user’s Cloud 66 trial period has expired. |
| 403 | forbidden | The user does not have the scope required to submit this request. |
| 404 | not_found | The system cannot find a response for this request URI. |
| 408 | time_out | The system did not return a response before the server timed out. |
| 409 | conflict | The system did not return a response because there is a current conflict with the resource. |
| 503 | not_implemented | This resource is not actively implemented in this version of the Cloud 66 API. |
| 503 | throttled | The user has reached or exceeded the maximum rate limit and must wait until the next hourly interval to retry the request. |

## Stack UID retrieval
Many requests in the Cloud 66 API rely on the Stack UID value, an alphanumeric string that uniquely identifies your stack. You can retrieve this value by accessing the _Stack information_ page from the right sidebar of your stack page or by submitting an API request to list all stacks. The Stack UID appears in the response body for each stack you maintain.
