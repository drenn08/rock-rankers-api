---
title: "POST: create a new band"
layout: default
nav_order: 1
parent: "Bands Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/bands/post-band/
has_toc: false
description: "Create a new band using the POST method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---

## Create a new band

Use the /bands endpoint to create a new `band` using the `POST` method.

### URL

```shell
{server_url}/bands
```

When testing, the {server_url} is the local host: <http://localhost:3000/bands>

### Path parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| None | - | - | This endpoint uses the base `/bands` path |

### Request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

### Request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `name` | string | Yes | The band name |
| `genre` | string | Yes | The band genre |
| `years-active` | string | Yes | The years the band was/is active |
| `origin` | string | Yes | The origin location of the band |

**Note:** the server auto generates the `id` field. Don't include in the request.

### Request syntax

```bash
curl -X POST http://localhost:3000/bands \
  -H "Content-Type: application/json" \
  -d '{
    "name": "{name}",
    "genre": "{genre}",
    "years-active": "{years-active}",
    "origin": "{origin}"
  }'
```

### Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `name` | string | The band name |
| `genre` | string | The band genre |
| `years-active` | string | The years the band was/is active |
| `origin` | string | The origin location of the band |
| `id` | integer | Unique identifier assigned by the server |

### Request example

```bash
curl -X POST http://localhost:3000/bands \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Soundgarden",
    "genre": "rock, alternative, grunge",
    "years-active": "1984-1997; 2010-2017",
    "origin": "Seattle, Washington, USA"
  }'
```

### Response example

```json
{
  "name": "Soundgarden",
  "genre": "rock, alternative, grunge",
  "years-active": "1984-1997; 2010-2017",
  "origin": "Seattle, Washington, USA",
  "id": 5
}
```

### Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 201 | Success | Band created successfully |
| 400 | Error | Invalid request body or missing required fields |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |

---
