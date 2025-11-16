---
title: "POST: create a new album"
layout: default
nav_order: 1
parent: "Albums Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/albums/post-album/
has_toc: false
description: "Create a new album using the POST method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---
## `POST`: create a new album

Use the /albums endpoint to create a new `album` using the `POST` method.

### URL

```shell

{server_url}/albums
```

### Request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

### Request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `name` | string | Yes | The name of the band that created the album |
| `album` | string | Yes | The name of the album |
| `release date` | string | Yes | The release date of the album |
| `album score` | string | Yes | The score rating of the album |
| `global album ranking` | string | No | The global ranking of the album |
| `band catalog album ranking` | string | No | The ranking of the album within the band's catalog |

### Request syntax

```bash
curl -X POST http://localhost:3000/albums \
  -H "Content-Type: application/json" \
  -d '{
    "name": "{name}",
    "album": "{album}",
    "release date": "{release date}",
    "album score": "{album score}",
    "global album ranking": "{global album ranking}",
    "band catalog album ranking": "{band catalog album ranking}"
  }'
```

### Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `name` | string | The name of the band that created the album |
| `album` | string | The name of the album |
| `release date` | string | The release date of the album |
| `album score` | string | The score rating of the album |
| `global album ranking` | string | The global ranking of the album |
| `band catalog album ranking` | string | The ranking of the album within the band's catalog |
| `id` | integer | Unique identifier assigned by the server |

### Request example

```bash
curl -X POST http://localhost:3000/albums \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Soundgarden",
    "album": "Superunknown",
    "release date": "1994",
    "album score": "945",
    "global album ranking": "5",
    "band catalog album ranking": "1"
  }'
```

### Response example

```json
{
  "name": "Soundgarden",
  "album": "Superunknown",
  "release date": "1994",
  "album score": "945",
  "global album ranking": "5",
  "band catalog album ranking": "1",
  "id": 5
}
```

### Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 201 | Success | Album created successfully |
| 400 | Error | Invalid request body or missing required fields |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |

---
