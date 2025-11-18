---
title: "PUT: update an existing user"
layout: default
nav_order: 2
parent: "Users Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/users/put-user/
has_toc: false
description: "Update an existing user using the PUT method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---

## `PUT`: update an existing user

Use the /users endpoint to update an existing `user` using the `PUT` method. Provide all fields, even if unchanged.

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
| `last-name` | string | Yes | The user's last name |
| `first-name` | string | Yes | The user's first name |
| `email` | string | Yes | The user's email address |

## Request syntax

```bash
curl -X PUT "http://localhost:3000/users/{id}" \
  -H "Content-Type: application/json" \
  -d '{
    "last-name": "{last-name}",
    "first-name": "{first-name}",
    "email": "{email}"
  }'
```

## Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `id` | integer | The user's unique identifier |
| `last-name` | string | The user's last name |
| `first-name` | string | The user's first name |
| `email` | string | The user's email address |

## Request example

**Original Resource:**

```json
{
  "id": 1,
  "last-name": "Renn",
  "first-name": "David",
  "email": "drenn08@uw.edu"
}
```

This example updates the **email** address.

```bash
curl -X PUT "http://localhost:3000/users/1" \
  -H "Content-Type: application/json" \
  -d '{
    "last-name": "Renn",
    "first-name": "David",
    "email": "david.renn@uw.edu"
  }'
```

## Response example

```json
{
  "id": 1,
  "last-name": "Renn",
  "first-name": "David",
  "email": "david.renn@uw.edu"
}
```

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | User updated successfully |
| 400 | Error | Invalid request body or missing required fields |
| 404 | Error | Specified user not found |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
