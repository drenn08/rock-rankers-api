---
title: "PUT: update a user"
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

Use the /users endpoint to update an existing `user` using the `PUT` method.

## URL

```shell

{server_url}/users?id={id}
```

## Query parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | number | Yes | The unique record ID of the user to replace |

## Request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

## Request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `lastName` | string | Yes | The user's last name |
| `firstName` | string | Yes | The user's first name |
| `email` | string | Yes | The user's email address |

## Request syntax

```bash
curl -X PUT http://localhost:3000/users?id={id} \
  -H "Content-Type: application/json" \
  -d '{
    "lastName": "{lastName}",
    "firstName": "{firstName}",
    "email": "{email}"
  }'
```

## Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `lastName` | string | The user's last name |
| `firstName` | string | The user's first name |
| `email` | string | The user's email address |
| `id` | number | The user's unique record ID |

## Request example

```bash
curl -X PUT http://localhost:3000/users?id=1 \
  -H "Content-Type: application/json" \
  -d '{
    "lastName": "Renn",
    "firstName": "David",
    "email": "david.renn@uw.edu"
  }'
```

## Response example

```json
{
  "lastName": "Renn",
  "firstName": "David",
  "email": "david.renn@uw.edu",
  "id": 1
}
```

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | User replaced successfully |
| 201 | Success | User created successfully, if user didn't exist |
| 400 | Error | Invalid request body or missing required fields |
| 404 | Error | Specified user record not found |
| 409 | Error | User with this email already exists |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
