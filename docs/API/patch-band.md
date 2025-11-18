---
title: "PATCH: delete a band"
layout: default
nav_order: 3
parent: "Bands Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/bands/patch-band/
has_toc: false
description: "Delete a band using the PATCH method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---

## `Patch`: delete a band

Use the /bands endpoint to delete an existing `band` using the `PATCH` method.

### URL

```shell

{server_url}/bands?name={name}
```

## Query parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `name` | string | Yes | The name of the band to update |

## Request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

## Request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `name` | string | No | band name |
| `genre` | string | No | band genre |
| `years-active` | string | No | The years the band was/is active |
| `origin` | string | No | The origin location of the band |

## Request syntax

```bash
curl -X PATCH http://localhost:3000/bands?name={name} \
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
| `name` | string | band name|
| `genre` | string | band genre |
| `years-active` | string | The years the band was/is active |
| `origin` | string | The origin location of the band |

## Request example

```bash
curl -X PATCH http://localhost:3000/bands?name=Soundgarden \
  -H "Content-Type: application/json" \
  -d '{
    "genre": "rock, alternative, grunge, metal"
  }'
```

## Response example

```json
{
  "name": "Soundgarden",
  "genre": "rock, alternative, grunge, metal",
  "years-active": "1984-1997; 2010-2019",
  "origin": "Seattle, Washington, USA"
}
```

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | Band updated successfully |
| 400 | Error | Invalid request body |
| 404 | Error | Specified band not found |
| 409 | Error | Band with this name already exists |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
