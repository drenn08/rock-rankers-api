---
title: "`DELETE`: delete a band"
layout: default
nav_order: 4
parent: "Bands Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/bands/delete-band/
has_toc: false
description: "Delete a band using the `DELETE` method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-17"
---

## `DELETE`: delete a band

Use the /bands endpoint to delete an existing `band` using the `DELETE` method. This permanently removes the band from the database.

## URL

```shell
{server_url}/bands/{id}
```

When testing, the {server_url} is the local host: <http://localhost:3000/bands/{id}>

## Path parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | integer | Yes | The unique identifier of the band to delete |

## Request headers

None required for delete operation.

## Request body

None required for delete operation.

## Request syntax

```bash
curl -X DELETE "http://localhost:3000/bands/{id}"
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

**delete this resource**

```json
{
  "id": 5,
  "name": "Soundgarden",
  "genre": "rock, alternative, grunge, metal",
  "years-active": "1984-1997; 2010-2019",
  "origin": "Seattle, Washington, USA"
}
```

Delete the Soundgarden band:

```bash
curl -X DELETE "http://localhost:3000/bands/5"
```

## Response example

No response body returned.

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | Band deleted successfully |
| 404 | Error | Specified band not found |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
