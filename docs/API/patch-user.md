---
title: "PATCH: partially update a user"
layout: default
nav_order: 3
parent: "Users Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/users/patch-user/
has_toc: false
description: "Partially update a user using the PATCH method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-17"
---

## `PATCH`: partially update a user

Use the /users endpoint to partially update an existing `user` using the `PATCH` method. `PATCH` only updates the fields included in the request body. All other fields remain unchanged.

## URL

```shell
{server_url}/users/{id}
```

When testing, the {server_url} is the local host: <http://localhost:3000/users/{id}>

## Path parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | integer | Yes | The unique identifier of the user to update |

## Request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

## Request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `last-name` | string | No | The last name of the user |
| `first-name` | string | No | The first name of the user |
| `email` | string | No | The email address of the user |

> **Note:** Include only the fields you want to update. All fields are optional.

## Request syntax

```bash
curl -X PATCH "http://localhost:3000/users/{id}" \
  -H "Content-Type: application/json" \
  -d '{
    "{property}": "{value}"
  }'
```

## Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `id` | integer | The unique identifier of the user |
| `last-name` | string | The last name of the user |
| `first-name` | string | The first name of the user |
| `email` | string | The email address of the user |

## Request example

**Original Resource:**

```json
{
  "id": 4,
  "last-name": "Plan",
  "first-name": "Robert",
  "email": "ledzeppelin@aol.com"
}
```

This example updates only the **email** field:

```bash
curl -X PATCH "http://localhost:3000/users/4" \
  -H "Content-Type: application/json" \
  -d '{
    "email": "robertplant@gmail.com"
  }'
```

## Response example

```json
{
  "id": 4,
  "last-name": "Plan",
  "first-name": "Robert",
  "email": "robertplant@gmail.com"
}
```

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | User updated successfully |
| 400 | Error | Invalid request body |
| 404 | Error | Specified user not found |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
