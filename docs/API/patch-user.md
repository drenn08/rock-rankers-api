---
title: "PATCH: delete a user"
layout: default
nav_order: 3
parent: "Users Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/users/delete-user/
has_toc: false
description: "Delete a user using the `PATCH` method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---
## `PATCH`: delete a user

Use the /users endpoint to delete an existing `user` using the `PATCH` method.

## URL

```shell
{server_url}/users/{id}
```

## Path parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | integer | Yes | The unique identifier of the user to delete |

## Request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

## Request body

None required for delete operation.

## Request syntax

```bash
curl -X PATCH http://localhost:3000/users/{id} \
  -H "Content-Type: application/json"
```

## Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `id` | integer | The unique identifier of the user |
| `last-name` | string | The last name of the user |
| `first-name` | string | The first name of the user |
| `email` | string | The email address of the user |

## Request example

```bash
curl -X PATCH http://localhost:3000/users/4 \
  -H "Content-Type: application/json"
```

## Response example

```json
{
  "id": 4,
  "last-name": "Plan",
  "first-name": "Robert",
  "email": "ledzeppelin@aol.com"
}
```

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | User deleted successfully |
| 404 | Error | Specified user not found |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
