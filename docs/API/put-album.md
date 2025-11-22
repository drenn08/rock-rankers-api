---
title: "`PUT`: update an existing album"
layout: default
nav_order: 2
parent: "Albums Resource"
grand_parent: "API Reference Docs"
permalink: /api-reference-docs/albums/put-album/
has_toc: false
description: "Update an existing album using the `PUT` method"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---

## `PUT`: update an existing album

Use the /albums endpoint to update an existing `album` using the `PUT` method. Provide all fields, even if unchanged

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
| `name` | string | Yes | The name of the band that created the album |
| `album` | string | Yes | The name of the album |
| `release-date` | integer | Yes | The release year of the album |
| `album-score` | integer | Yes | The score rating of the album |
| `global-album-ranking` | integer | No | The global ranking of the album |
| `band-catalog-album-ranking` | integer | No | The ranking of the album within the band's catalog |

## Request syntax

```bash
curl -X PUT "http://localhost:3000/albums/{id}" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "{name}",
    "album": "{album}",
    "release-date": {release-date},
    "album-score": {album-score},
    "global-album-ranking": {global-album-ranking},
    "band-catalog-album-ranking": {band-catalog-album-ranking}
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
  "id": 5,
  "name": "Soundgarden",
  "album": "Superunknown",
  "release-date": 1994,
  "album-score": 945,
  "global-album-ranking": 5,
  "band-catalog-album-ranking": 1
}
```

This example updates the **album-score** and **global-album-ranking**.

```bash
curl -X PUT "http://localhost:3000/albums/5" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Soundgarden",
    "album": "Superunknown",
    "release-date": 1994,
    "album-score": 950,
    "global-album-ranking": 4,
    "band-catalog-album-ranking": 1
  }'
```

## Response example

```json
{
  "id": 5,
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
| 400 | Error | Invalid request body or missing required fields |
| 404 | Error | Specified album not found |
| ECONNREFUSED | N/A | Service is offline. Start the service and try again. |
