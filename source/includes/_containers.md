# Containers

## Containers list

```http
POST /stacks/{id}/containers HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "response":[
      {
         "uid":"cba44fa6b6acf57fb0ef6c2ce385f6a129867df544dae7181d2410e9f9cc32bc",
         "server_uid":"c6014897b8c8e9f2fc204a3a9efdae05",
         "server_name":"Gazelle",
         "service_name":"web",
         "image":"quay.io/cloud66/sample-rails",
         "command":"bundle exec rackup -p 3000",
         "started_at":"2015-02-10T17:41:31Z",
         "ports":[
            {
               "container":3000,
               "http":80,
               "https":443
            }
         ],
         "private_ip":"25.0.0.2",
         "docker_ip":null,
         "health_state":1,
         "health_message":null,
         "health_source":"system",
         "capture_output":true,
         "restart_on_deploy":true,
         "created_at":"2015-02-10T17:41:37Z",
         "updated_at":"2015-02-17T14:40:17Z"
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

Get a list of all the containers of the stack

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/containers`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
server_uid | optional | string | Server UID | `c6014897b8c8e9f2fc204a3a9efdae05`

## Container show

```http
GET /stacks/{stack_id}/containers/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "response":{
      "uid":"cba44fa6b6acf57fb0ef6c2ce385f6a129867df544dae7181d2410e9f9cc32bc",
      "server_uid":"c6014897b8c8e9f2fc204a3a9efdae05",
      "server_name":"Gazelle",
      "service_name":"web",
      "image":"quay.io/cloud66/sample-rails",
      "command":"bundle exec rackup -p 3000",
      "started_at":"2015-02-10T17:41:31Z",
      "ports":[
         {
            "container":3000,
            "http":80,
            "https":443
         }
      ],
      "private_ip":"25.0.0.2",
      "docker_ip":"172.0.2.12",
      "health_state":1,
      "health_message":null,
      "health_source":"system",
      "capture_output":true,
      "restart_on_deploy":true,
      "created_at":"2015-02-10T17:41:37Z",
      "updated_at":"2015-02-17T14:40:17Z",
      "runtime":{
         "AppArmorProfile":"",
         "Args":[
            "bundle",
            "exec",
            "rackup",
            "-p",
            "3000"
         ],
         "Config":{
            "AttachStderr":true,
            "AttachStdin":false,
            "AttachStdout":true,
            "Cmd":[
               "bundle",
               "exec",
               "rackup",
               "-p",
               "3000"
            ],
            "CpuShares":0,
            "Cpuset":"",
            "Domainname":"",
            "Entrypoint":[
               "/etc/cloud66/tools/docker_network.sh"
            ],
            "Env":[
               "STACK_GIT_BRANCH=",
               "STACK_PATH=/var/deploy/lv_dev_service_download/web_head/current",
               "STACK_BASE=/var/deploy/lv_dev_service_download/web_head",
               "SECRET_KEY_BASE=f30c0e5da0cb4467e4cae0f315a664d023b1782f791e682dbe2dc100d3b010cd6b3d899c01138470c10892cf31732b7bb83a31b4907296ad985e8f55663629c1",
               "WEB_ADDRESS_INT=10.132.130.135",
               "WEB_ADDRESS_EXT=104.236.242.128",
               "WEB_ADDRESSES_INT=10.132.130.135",
               "WEB_ADDRESSES_EXT=104.236.242.128",
               "MYSQL_USERNAME=uacru9",
               "MYSQL_PASSWORD=FBfgULSTlfjruP3",
               "MYSQL_DATABASE=lv_dev_service_download_production",
               "MYSQL_ADDRESS_INT=10.132.130.135",
               "MYSQL_ADDRESS_EXT=104.236.242.128",
               "MYSQL_URL_INT=mysql://uacru9:FBfgULSTlfjruP3@10.132.130.135:3306/lv_dev_service_download_production",
               "MYSQL_URL_EXT=mysql://uacru9:FBfgULSTlfjruP3@104.236.242.128:3306/lv_dev_service_download_production",
               "MYSQL_SLAVE_ADDRESSES_INT=",
               "MYSQL_SLAVE_ADDRESSES_EXT=",
               "WEB_ADDRESS=10.132.130.135",
               "WEB_ADDRESSES=10.132.130.135",
               "MYSQL_ADDRESS=10.132.130.135",
               "MYSQL_URL=mysql://uacru9:FBfgULSTlfjruP3@10.132.130.135:3306/lv_dev_service_download_production",
               "MYSQL_SLAVE_ADDRESSES=",
               "SERVER_NAME=Gazelle",
               "PRIMARY=true",
               "CONTAINER_NOTIFY_URL=http://vic.local.cldblx.com/stacks/87bc318604208618a01817bf4442befb/servers/c6014897b8c8e9f2fc204a3a9efdae05/services/web/notification/4911055bcf0b5d7a31ebfbdff4043c31",
               "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
               "RUBY_MAJOR=2.1",
               "RUBY_VERSION=2.1.3"
            ],
            "ExposedPorts":{
               "3000/tcp":{

               }
            },
            "Hostname":"cba44fa6b6ac",
            "Image":"quay.io/cloud66/sample-rails",
            "MacAddress":"",
            "Memory":0,
            "MemorySwap":0,
            "NetworkDisabled":false,
            "OnBuild":null,
            "OpenStdin":false,
            "PortSpecs":null,
            "StdinOnce":false,
            "Tty":false,
            "User":"",
            "Volumes":null,
            "WorkingDir":"/usr/src/app"
         },
         "Created":"2015-02-10T17:41:36.988310784Z",
         "Driver":"aufs",
         "ExecDriver":"native-0.2",
         "HostConfig":{
            "Binds":[
               "/etc/cloud66/tools:/etc/cloud66/tools",
               "/var/log/containers:/usr/src/app/log",
               "/tmp:/tmp_host:rw"
            ],
            "CapAdd":null,
            "CapDrop":null,
            "ContainerIDFile":"",
            "Devices":[

            ],
            "Dns":[
               "172.17.42.1"
            ],
            "DnsSearch":null,
            "ExtraHosts":null,
            "IpcMode":"",
            "Links":null,
            "LxcConf":[

            ],
            "NetworkMode":"bridge",
            "PortBindings":{

            },
            "Privileged":false,
            "PublishAllPorts":false,
            "RestartPolicy":{
               "MaximumRetryCount":0,
               "Name":""
            },
            "SecurityOpt":null,
            "VolumesFrom":null
         },
         "HostnamePath":"/var/lib/docker/containers/cba44fa6b6acf57fb0ef6c2ce385f6a129867df544dae7181d2410e9f9cc32bc/hostname",
         "HostsPath":"/var/lib/docker/containers/cba44fa6b6acf57fb0ef6c2ce385f6a129867df544dae7181d2410e9f9cc32bc/hosts",
         "Id":"cba44fa6b6acf57fb0ef6c2ce385f6a129867df544dae7181d2410e9f9cc32bc",
         "Image":"f3443abc9c9e1595d1e039bf0c060f259d318e57910a80efee2e34895b10e749",
         "MountLabel":"",
         "Name":"/stoic_nobel",
         "NetworkSettings":{
            "Bridge":"docker0",
            "Gateway":"172.17.42.1",
            "IPAddress":"172.17.0.4",
            "IPPrefixLen":16,
            "MacAddress":"02:42:ac:11:00:04",
            "PortMapping":null,
            "Ports":{
               "3000/tcp":null
            }
         },
         "Path":"/etc/cloud66/tools/docker_network.sh",
         "ProcessLabel":"",
         "ResolvConfPath":"/var/lib/docker/containers/cba44fa6b6acf57fb0ef6c2ce385f6a129867df544dae7181d2410e9f9cc32bc/resolv.conf",
         "State":{
            "Error":"",
            "ExitCode":0,
            "FinishedAt":"0001-01-01T00:00:00Z",
            "OOMKilled":false,
            "Paused":false,
            "Pid":25739,
            "Restarting":false,
            "Running":true,
            "StartedAt":"2015-02-10T17:41:37.915288589Z"
         },
         "Volumes":{
            "/etc/cloud66/tools":"/etc/cloud66/tools",
            "/tmp_host":"/tmp",
            "/usr/src/app/log":"/var/log/containers"
         },
         "VolumesRW":{
            "/etc/cloud66/tools":true,
            "/tmp_host":true,
            "/usr/src/app/log":true
         }
      }
   }
}
```

Get information of a container of the stack (includes container runtime information)

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/containers/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | string | The container UID | `cba44fa6b6acf57fb0ef6c2ce385f6a129867df544dae7181d2410e9f9cc32bc`

## Container stop

```http
DELETE /stacks/{stack_id}/containers/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response": {
    "id": 1234,
    "user": "theuser@yourdomain.com",
    "resource_type": "stack",
    "action": "container_stop",
    "resource_id": "15633",
    "started_via": "api",
    "started_at": "2014-09-30T11:36:58Z",
    "finished_at": null,
    "finished_success": null,
    "finished_message": null
  }
}
```

Stop the given container

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`DELETE /stacks/{stack_id}/containers/{id}`

### Query parameters

Parameter | Presence | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | **required** | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | **required** | string | The container UID | `cba44fa6b6acf57fb0ef6c2ce385f6a129867df544dae7181d2410e9f9cc32bc`
