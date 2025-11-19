---
title: "PATCH: partially update an album"
layout: default
nav_order: 3
parent: "Albums Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/albums/patch-album/
has_toc: false
description: "Partially update an album using the PATCH method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-17"
---

## `PATCH`: partially update an album

Use the /albums endpoint to partially update an existing `album` using the `PATCH` method. `PATCH` only updates the fields included in the request body. All other fields remain unchanged.

## URL

```shell
{server_url}/albums/{id}
```

When testing, the {server_url} is the local host: <http://localhost:3000/albums/{id}>

## Path parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | integer | Yes | The unique identifier of the album to update |

## Request headers

| Header | Type | Required | Description |
|--------|------|----------|-------------|
| `Content-Type` | string | Yes | Must be `application/json` |

## Request body

| Property name | Type | Required | Description |
| ------------- | ----------- | ----------- | ----------- |
| `name` | string | No | The name of the band that created the album |
| `album` | string | No | The name of the album |
| `release-date` | integer | No | The release year of the album |
| `album-score` | integer | No | The score rating of the album |
| `global-album-ranking` | integer | No | The global ranking of the album |
| `band-catalog-album-ranking` | integer | No | The ranking of the album within the band's catalog |

> **Note:** Include only the fields you want to update. All fields are optional.

## Request syntax

```bash
curl -X PATCH "http://localhost:3000/albums/{id}" \
  -H "Content-Type: application/json" \
  -d '{
    "{property}": {value}
  }'
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

**Original Resource:**

```json
{
  "id": 3,
  "name": "Soundgarden",
  "album": "Superunknown",
  "release-date": 1994,
  "album-score": 900,
  "global-album-ranking": 5,
  "band-catalog-album-ranking": 1
}
```

This example updates only the **album-score** and **global-album-ranking** fields:

```bash
curl -X PATCH "http://localhost:3000/albums/3" \
  -H "Content-Type: application/json" \
  -d '{
    "album-score": 950,
    "global-album-ranking": 4
  }'
```

## Response example

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

## Return status

| Status value | Return status | Description |
| ------------- | ----------- | ----------- |
| 200 | Success | Album updated successfully |
| 400 | Error | Invalid request body |
| 404 | Error | Specified album not found |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
