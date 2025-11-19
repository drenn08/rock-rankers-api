---
title: "Albums Resource"
layout: default
nav_order: 2
parent: "API Reference Docs"
has_children: true
permalink: /api-reference-docs/albums/
has_toc: false
description: "Information about the `albums` resource"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---

## `albums` resource

Base endpoint:

```shell
{server_url}/albums
```

Provides information about albums in the Rock Rankers service.

The album resource contains music albums released by the [bands resource](./bands.md). Each album links with its band through the `name` field. The `name` field references the band's name.

 Rock Rankers ranks albums both globally and within their band's catalog. [Users](./users.md) can search for albums and their rankings within the service.

## Resource properties

Sample `albums` resource

```js
{
    "name": "The Beatles",
    "album": "Rubber Soul",
    "release-date": 1965,
    "album-score": 987,
    "global-album-ranking": 1,
    "band-catalog-album-ranking": 1,
    "id": 1
}
```

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `name` | string | The name of the [bands resource](./bands.md) that released this album |
| `album` | string | The album name |
| `release-date` | integer | The album release year |
| `album-score` | integer | The album's score |
| `global-album-ranking` | integer | The album's ranking across all albums |
| `band-catalog-album-ranking` | integer | The album's ranking within the band's catalog |
| `id` | integer | The album's unique record ID |

## Supported operations

* `GET`
* [`POST`: create a new album](./post-album.md)
* [`PUT`: update an existing album](./put-album.md)
* [`PATCH`: partially update an album](./patch-album.md)
* [`DELETE`: delete an album](./delete-album.md)

## Related resources

* [bands resource](./bands.md) - The band that released this album
* [users resource](./users.md) - Users who can view and interact with albums
