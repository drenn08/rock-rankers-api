---
title: "PATCH: partially update a band"
layout: default
nav_order: 3
parent: "Bands Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/bands/patch-band/
has_toc: false
description: "Partially update a band using the PATCH method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-17"
---

## `PATCH`: partially update a band

Use the /bands endpoint to partially update an existing `band` using the `PATCH` method. `PATCH` only updates the fields included in the request body. All other fields remain unchanged.

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
| `name` | string | No | The band name |
| `genre` | string | No | The band genre |
| `years-active` | string | No | The years the band was/is active |
| `origin` | string | No | The origin location of the band |

> **Note:** Include only the fields you want to update. All fields are optional.

## Request syntax

```bash
curl -X PATCH "http://localhost:3000/bands/{id}" \
  -H "Content-Type: application/json" \
  -d '{
    "{property}": "{value}"
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

This example updates only the **years-active** field:

```bash
curl -X PATCH "http://localhost:3000/bands/5" \
  -H "Content-Type: application/json" \
  -d '{
    "years-active": "1984-1997; 2010-2017"
  }'
```

## Response example

```json
{
  "id": 5,
  "name": "Soundgarden",
  "genre": "rock, alternative, grunge, metal",
  "years-active": "1984-1997; 2010-2017",
  "origin": "Seattle, Washington, USA"
}
```

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | Band updated successfully |
| 400 | Error | Invalid request body |
| 404 | Error | Specified band not found |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
