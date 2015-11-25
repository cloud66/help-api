# Backups

## Backups list

> Headers

```http
GET /stacks/{id}/backups HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

> Body

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":[
    {
      "id":4,
      "server_uid":"e63e859d5ab72b0bcf14321f0ffb013d",
      "db_type":"mysql",
      "database_name":"test-db",
      "file_base":"",
      "backup_date_iso":"2014-09-01T19:00:33Z",
      "backup_status":0,
      "backup_result":"",
      "restore_status":0,
      "restore_result":null,
      "created_at_iso":"2014-09-01T19:00:33Z",
      "updated_at_iso":"2014-09-01T19:00:33Z",
      "verify_status":0,
      "verify_result":null,
      "storage_path":"2aad2bb5a70e621ecf251fbd85af6927/backups/3c656a1bcc160769762763c6276c18b9/mysql/test_db_11/2014.09.01.19.00.31",
      "skip_tables":"","backup_size":0
    },
    {
      "id":1,
      "server_uid":"e63e859d5ab72b0bcf14321f0ffb013d",
      "db_type":"mysql",
      "database_name":"test-db",
      "file_base":"",
      "backup_date_iso":"2014-09-01T18:16:16Z",
      "backup_status":0,
      "backup_result":"",
      "restore_status":0,
      "restore_result":null,
      "created_at_iso":"2014-09-01T18:16:16Z",
      "updated_at_iso":"2014-09-01T18:16:16Z",
      "verify_status":0,
      "verify_result":null,
      "storage_path":"2aad2bb5a70e621ecf251fbd85af6927/backups/3c656a1bcc160769762763c6276c18b9/mysql/test_db_11/2014.09.01.18.16.14",
      "skip_tables":"","backup_size":0
    }
  ],
  "count":2,
  "pagination":
    {
      "previous":null,
      "next":null,
      "current":1,
      "per_page":30,
      "count":2,
      "pages":1
    }
}
```

Get list of all backups of stack.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{id}/backups`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
group | false | integer | Backup group ID | `15`
db_type | false | string | Backup database type (valid options are: mysql, postgresql, redis, mongodb) | `mysql`

## Backup

> Headers

```http
GET /stacks/{stack_id}/backups/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

> Body

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "id":1,
      "server_uid":"e63e859d5ab72b0bcf14321f0ffb013d",
      "db_type":"mysql",
      "database_name":"shab-test-db",
      "file_base":"",
      "backup_date_iso":"2014-09-01T18:16:16Z",
      "backup_status":0,
      "backup_result":"",
      "restore_status":0,
      "restore_result":null,
      "created_at_iso":"2014-09-01T18:16:16Z",
      "updated_at_iso":"2014-09-01T18:16:16Z",
      "verify_status":0,
      "verify_result":null,
      "storage_path":"2aad2bb5a70e621ecf251fbd85af6927/backups/3c656a1bcc160769762763c6276c18b9/mysql/test_db_11/2014.09.01.18.16.14",
      "skip_tables":"",
      "backup_size":0
    }
}
```

Get information about a single backup.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/backups/{id}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
id | true | integer | Backup id | `4153`

## New Backup

> Headers

```http
POST /stacks/{stack_id}/backups HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

> Body

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "ok":true,
      "message":"queued for creation"
    }
}
```

Create a new backup task.

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`POST /stacks/{stack_id}/backups`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
db_type | false | string | Comma separated list of Database types which need backup tasks (valid options: all,mysql, postgresql, redis, mongodb) | `mysql,redis`
frequency | false | string | Frequency of backup task in cron schedule format | `0 */1 * * *`
keep_count | false | integer | Number of previous backups to keep | `10`
gzip | false | boolean | Compress your backups with gzip. | `false`
excluded_tables | false | string | Tables that must be excluded from the backup | `my_log_table`
run_on_replica_server | false | boolean | Run backup task on replica server if available | `false`

## Import Backup

> Headers

```http
POST /stacks/{stack_id}/backups HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

> Body

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "ok":true,
      "message":"Your external backup queued for upload"
    }
}
```

Import an external backup.

<aside class="notice">
<b>Scope:</b> <i>admin</i>
</aside>

### HTTP Request

`POST /stacks/{stack_id}/backups`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
group | true | integer | The group id of backups that imported backup must restored in | `5`
db_type | true | string | Comma separated list of Database types which need backup tasks (valid options: mysql, postgresql, redis, mongodb) | `mysql`
remote_url | true | string | A URL to backup file to be imported | `https://s3.amazonaws.com/c66-managed-backup-non-prod/2aad2bb5a70e621ecf251fbd85af6927/backups/09a7dec0efdaa19b44148fccbf6128ec/redis/redis_23/2014.07.01.07.00.46/redis_23.tar`

## Backups files list

> Headers

```http
GET /stacks/{stack_id}/backups/{backup_id}/files HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

> Body

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":[
    {
      "id":"tar",
      "name":"test_db_11.tar"
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
```

Get list of all backup files of a stack.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/backups/{backup_id}/files`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
backup_id | true | integer | Backup ID | `4153`

## Backup file

> Headers

```http
GET /stacks/{stack_id}/backups/{backup_id}/files/{id} HTTP/1.1
X-RateLimit-Limit: 3600
X-RateLimit-Remaining: 3597
```

> Body

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "response":
    {
      "ok":true,
      "public_url":"https://c66-managed-backup-non-prod.s3.amazonaws.com/2aad2bb5a70e621ecf251fbd85af6927/backups/3c656a1bcc160769762763c6276c18b9/mysql/test_db_11/2014.09.01.18.16.14/test_db_11.tar?AWSAccessKeyId=AKIAIKCYITLQBEJDIETQ\u0026Expires=1409603570\u0026Signature=C2au7Jq%252F1m6uHGHRfGJPn%252F2GSS8%253D"
    }
}
```

Get the public URL to a backup file.

<aside class="notice">
<b>Scope:</b> <i>public</i>
</aside>

### HTTP Request

`GET /stacks/{stack_id}/backups/{backup_id}/files/{id}`

### Query parameters

Parameter | Required | Data type | Description |  Sample value
--------- | ------- | ------- |----------- |  -------
stack_id | true | string | The stack UID | `5999b763474b0eafa5fafb64bff0ba80`
backup_id | true | integer | Backup ID | `4153`
id | true | string | The file ID | `tar-aa`
