---
title: "`POST`: create a new user"
layout: default
nav_order: 1
parent: "Users Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/users/post-user/
has_toc: false
description: "Create a new user using the `POST` method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---

## Create a new user

Use the /users endpoint to create a new `user` using the `POST` method.

### URL

```shell
{server_url}/users
```

### `POST` user request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

### Request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `last-name` | string | Yes | The user's last name |
| `first-name` | string | Yes | The user's first name |
| `email` | string | Yes | The user's email address |

**Note:** the server auto generates the `id` field. Don't include in the request.

### `POST` user request syntax

```bash
curl -X POST http://localhost:3000/users \
  -H "Content-Type: application/json" \
  -d '{
    "last-name": "{last-name}",
    "first-name": "{first-name}",
    "email": "{email}"
  }'
```

### Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `last-name` | string | The user's last name |
| `first-name` | string | The user's first name |
| `email` | string | The user's email address |
| `id` | integer | Unique identifier assigned by the server |

### Request example

```bash
curl -X POST http://localhost:3000/users \
  -H "Content-Type: application/json" \
  -d '{
    "last-name": "Meere",
    "first-name": "John",
    "email": "johnm@gmail.com"
  }'
```

### Response example

```json
{
  "last-name": "Meere",
  "first-name": "John",
  "email": "johnm@gmail.com",
  "id": 5
}
```

### Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 201 | Success | User created successfully |
| 400 | Error | Invalid request body or missing required fields |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |

---
