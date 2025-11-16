---
title: "PUT: update a band"
layout: default
nav_order: 2
parent: "Bands Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/bands/put-band/
has_toc: false
description: "Update an existing band using the PUT method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---

## `PUT`: update an existing band

Use the /bands endpoint to update an existing `band` using the `PUT` method.

## URL

```shell
{server_url}/bands/{id}
```

When testing, the {server_url} is the local host: <http://localhost:3000/bands/{id}>

## Path parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | integer | Yes | The unique identifier of the band to update |

## Request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

## Request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `name` | string | Yes | The band name |
| `genre` | string | Yes | The band genre |
| `years-active` | string | Yes | The years the band was/is active |
| `origin` | string | Yes | The origin location of the band |

## Request syntax

```bash
curl -X PUT "http://localhost:3000/bands/{id}" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "{name}",
    "genre": "{genre}",
    "years-active": "{years-active}",
    "origin": "{origin}"
  }'
```

## Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `id` | integer | Unique band identifier |
| `name` | string | The band name |
| `genre` | string | The band genre |
| `years-active` | string | The years the band was/is active |
| `origin` | string | The origin location of the band |

## Request example

**Original Resource:**

```json
{
  "id": 5,
  "name": "Soundgarden",
  "genre": "rock, alternative, grunge, metal",
  "years-active": "1984-1997; 2010-2019",
  "origin": "Seattle, Washington, USA"
}
```

This example removes the **genre: grunge**.

```bash
curl -X PUT "http://localhost:3000/bands/5" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Soundgarden",
    "genre": "rock, alternative",
    "years-active": "1984-1997; 2010-2019",
    "origin": "Seattle, Washington, USA"
  }'
```

## Response example

```json
{
  "id": 5,
  "name": "Soundgarden",
  "genre": "rock, alternative",
  "years-active": "1984-1997; 2010-2019",
  "origin": "Seattle, Washington, USA"
}
```

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | Band updated successfully |
| 400 | Error | Invalid request body or missing required fields |
| 404 | Error | Specified band not found |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
