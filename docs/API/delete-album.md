---
title: "`DELETE`: delete an album"
layout: default
nav_order: 4
parent: "Albums Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/albums/delete-album/
has_toc: false
description: "Delete an album using the `DELETE` method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-17"
---

## `DELETE`: delete an album

Use the /albums endpoint to delete an existing `album` using the `DELETE` method. This permanently removes the album from the database.

## URL

```shell
{server_url}/albums/{id}
```

When testing, the {server_url} is the local host: <http://localhost:3000/albums/{id}>

## Path parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | integer | Yes | The unique identifier of the album to delete |

## Request headers

None required for delete operation.

## Request body

None required for delete operation.

## Request syntax

```bash
curl -X DELETE "http://localhost:3000/albums/{id}"
```

## Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `id` | integer | Unique album identifier |
| `name` | string | The name of the band that created the album |
| `album` | string | The name of the album |
| `release-date` | integer | The release year of the album |
| `album-score` | integer | The score rating of the album |
| `global-album-ranking` | integer | The global ranking of the album |
| `band-catalog-album-ranking` | integer | The ranking of the album within the band's catalog |

## Request example

**delete this album :**

```json
{
  "id": 3,
  "name": "Soundgarden",
  "album": "Superunknown",
  "release-date": 1994,
  "album-score": 950,
  "global-album-ranking": 4,
  "band-catalog-album-ranking": 1
}
```

Delete the Superunknown album:

```bash
curl -X DELETE "http://localhost:3000/albums/3"
```

## Response example

No response body returned.

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | Album deleted successfully |
| 404 | Error | Specified album not found |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
