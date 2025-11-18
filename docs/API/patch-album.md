---
title: "PATCH: delete an album"
layout: default
nav_order: 3
parent: "Albums Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/albums/patch-album/
has_toc: false
description: "Delete an album using the `PATCH` method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---

## `PATCH`: delete an album

Use the /albums endpoint to delete an existing `album` using the `PATCH` method.

## URL

```shell

{server_url}/albums?name={name}&album={album}
```

## Query parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `name` | string | Yes | The name of the band that created the album |
| `album` | string | Yes | The name of the album to update |

## Request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

## Request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `name` | string | No | The name of the band that created the album |
| `album` | string | No | The name of the album |
| `release-date` | string | No | The release date of the album |
| `album-score` | string | No | The score rating of the album |
| `global-album-ranking` | string | No | The global ranking of the album |
| `band-catalog-album-ranking` | string | No | The ranking of the album within the band's catalog |

## Request syntax

```bash
curl -X PATCH http://localhost:3000/albums?name={name}&album={album} \
  -H "Content-Type: application/json" \
  -d '{
    "name": "{name}",
    "album": "{album}",
    "release-date": "{release-date}",
    "album-score": "{album-score}",
    "global-album-ranking": "{global-album-ranking}",
    "band-catalog-album-ranking": "{band-catalog-album-ranking}"
  }'
```

## Response format

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `name` | string | The name of the band that created the album |
| `album` | string | The name of the album |
| `release-date` | string | The release date of the album |
| `album-score` | string | The score rating of the album |
| `global-album-ranking` | string | The global ranking of the album |
| `band-catalog-album-ranking` | string | The ranking of the album within the band's catalog |

## Request example

```bash
curl -X PATCH http://localhost:3000/albums?name=Soundgarden&album=Superunknown \
  -H "Content-Type: application/json" \
  -d '{
    "album-score": "950",
    "global-album-ranking": "4"
  }'
```

## Response example

```json
{
  "name": "Soundgarden",
  "album": "Superunknown",
  "release-date": "1994",
  "album-score": "950",
  "global-album-ranking": "4",
  "band-catalog-album-ranking": "1"
}
```

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | Album updated successfully |
| 400 | Error | Invalid request body |
| 404 | Error | Specified album not found |
| 409 | Error | Album with this name already exists for this band |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
