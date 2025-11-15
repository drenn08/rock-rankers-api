---
title: "POST a user"
layout: default
nav_order: 1
parent: "Users"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/users/POST-user/
has_toc: false
description: "Create a new user using the POST method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---

## `POST` a new user

Use the /users endpoint to POST a new `user` to the system.

### `POST` user `URL`

```shell

{server_url}/users
```

### `POST` user query parameters

None

### `POST` user request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

### `POST` user request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `lastName` | string | Yes | The user's last name |
| `firstName` | string | Yes | The user's first name |
| `email` | string | Yes | The user's email address |

### `POST` user request syntax

```bash
curl -X POST http://localhost:3000/users \
  -H "Content-Type: application/json" \
  -d '{
    "lastName": "{lastName}",
    "firstName": "{firstName}",
    "email": "{email}"
  }'
```

### `POST` user response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `lastName` | string | user last name |
| `firstName` | string | user first name |
| `email` | string | user email address |
| `id` | number | unique user record ID |

### `POST` user request example

```bash
curl -X POST http://localhost:3000/users \
  -H "Content-Type: application/json" \
  -d '{
    "lastName": "Meere",
    "firstName": "John",
    "email": "johnm@gmail.com"
  }'
```

### `POST` user response example

```json
{
  "lastName": "Meere",
  "firstName": "John",
  "email": "johnm@gmail.com",
  "id": 1
}
```

### `POST` user return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 201 | Success | User created successfully |
| 400 | Error | Invalid request body or missing required fields |
| 409 | Error | User with this email already exists |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
