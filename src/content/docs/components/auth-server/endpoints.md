---
title: Endpoints
lastUpdated: 2025-10-28
---

## User Endpoints
If any errors occur a `logMessage` key in the data container will contain the error message

##### GET `/api/get/uuid/<username>`

```json
{
  "type": "success",
  "data": {
    "user_id": "<uuid>"
  }
}
```

##### GET `/api/get/<uuid>`

```json
{
	"type": "success",
	"data": {
		"created_at": int, // UNIX Timestamp
		"username": "<username>",
		"display": "<display name>",
		"avatar": "<base64 avatar>",
		"about": "<base64 about>",
		"status": "<status>",
		"public_key": "<base64 public key>",
		"sub_level": int,
		"sub_end": int
	}
}
```

##### POST `/api/change/<uuid>`

`REQ`

```json
{
	[ "username" | "display" | "avatar" | "about" | "status" ]: [ "<username>" | "<display>" |  "<avatar>" | "<about>" | "<status>" ],
	"private_key_hash": "<sha256 private key hash>"
}
```

`RES`

```json
{
  "type": "success"
}
```

##### POST `/api/change/iota-id/<uuid>`

`REQ`

```json
{
  "iota_id": "<uuid>",
  "reset_token": "<base64 random bytes>",
  "new_token": "<base64 random bytes>"
}
```

`RES`

```json
{
  "type": "success"
}
```

##### POST `/api/change/keys/<uuid>`

`REQ`

```json
{
  "private_key_hash": "<sha256 private key hash>",
  "public_key": "<base64 public key>",
  "reset_token": "<base64 random bytes>",
  "new_token": "<base64 random bytes>"
}
```

`RES`

```json
{
  "type": "success"
}
```

## Iota Endpoints

##### GET `/api/register/init`

The user creation process timeouts after 1 hour.

```json
{
  "type": "success",
  "data": {
    "user_id": "<uuid>"
  }
}
```

##### POST `/api/register/complete`

`REQ`

```json
{
  "uuid": "",
  "username": "",
  "public_key": "",
  "private_key_hash": "",
  "username": "",
  "iota_id": "",
  "reset_token": ""
}
```

`RES`

```json
{
  "type": "success"
}
```

##### POST `/api/delete/<uuid>`

`REQ`

```json
{
  "reset_token": ""
}
```

`RES`

```json
{
  "type": "success"
}
```

## Omikron Endpoints

##### GET `/api/get/private-key-hash/<uuid>`

**Header:** `Authorization <omikron uuid>`
**Header:** `PrivateKeyHash <sha256 private key hash>`

```json
{
	"type": "success",
	"data": {
		"matches": boolean
	}
}
```

##### GET `/api/get/iota-id/<uuid>`

**Header:** `Authorization <omikron uuid>`

```json
{
  "type": "success",
  "data": {
    "iota_id": "<uuid>"
  }
}
```
