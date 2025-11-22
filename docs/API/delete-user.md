---
title: "`DELETE`: delete a user"
layout: default
nav_order: 4
parent: "Users Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/users/delete-user/
has_toc: false
description: "Delete a user using the `DELETE` method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-17"
---

## `DELETE`: delete a user

Use the /users endpoint to delete an existing `user` using the `DELETE` method. This permanently removes the user from the database.

## URL

```shell
{server_url}/users/{id}
```

When testing, the {server_url} is the local host: <http://localhost:3000/users/{id}>

## Path parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | integer | Yes | The unique identifier of the user to delete |

## Request headers

None required for delete operation.

## Request body

None required for delete operation.

## Request syntax

```bash
curl -X DELETE "http://localhost:3000/users/{id}"
```

## Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `id` | integer | The unique identifier of the user |
| `last-name` | string | The last name of the user |
| `first-name` | string | The first name of the user |
| `email` | string | The email address of the user |

## Request example

**Delete this user**

```json
{
  "id": 4,
  "last-name": "Plan",
  "first-name": "Robert",
  "email": "robertplant@gmail.com"
}
```

Delete the user Robert Plan:

```bash
curl -X DELETE "http://localhost:3000/users/4"
```

## Response example

No response body returned.

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | User deleted successfully |
| 404 | Error | Specified user not found |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
