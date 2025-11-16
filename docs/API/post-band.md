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

## `POST`: create a new band

Use the /bands endpoint to create a new `band` using the `POST` method.

### `POST` band URL

```shell

{server_url}/bands
```

### `POST` band query parameters

None

### `POST` band request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

### `POST` band request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `name` | string | Yes | The band name |
| `genre` | string | Yes | The band genre |
| `years active` | string | Yes | The years the band was/is active |
| `origin` | string | Yes | The origin location of the band |

### `POST` band request syntax

```bash
curl -X POST http://localhost:3000/bands \
  -H "Content-Type: application/json" \
  -d '{
    "name": "{name}",
    "genre": "{genre}",
    "years active": "{years active}",
    "origin": "{origin}"
  }'
```

### `POST` band response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `name` | string | The band name |
| `genre` | string | The band genre |
| `years active` | string | The years the band was/is active |
| `origin` | string | The origin location of the band |

### `POST` band request example

```bash
curl -X POST http://localhost:3000/bands \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Soundgarden",
    "genre": "rock, alternative, grunge",
    "years active": "1984-1997; 2010-2017",
    "origin": "Seattle, Washington, USA"
  }'
```

### `POST` band response example

```json
{
  "name": "Soundgarden",
  "genre": "rock, alternative, grunge",
  "years active": "1984-1997; 2010-2017 ",
  "origin": "Seattle, Washington, USA"
}
```

### `POST` band return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 201 | Success | Band created successfully |
| 400 | Error | Invalid request body or missing required fields |
| 409 | Error | Band with this name already exists |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |

---
