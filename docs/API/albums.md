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
last_updated: "2025-11-11"
---

## `albums` resource

Base endpoint:

```shell

{server_url}/albums
```

Contains information about the albums in the rock-rankers service.

The album resource cotains music albums released by [bands](../API/bands.md). Each album links with it's band through the `name` field. The `name` field references the band's name. Rock-rankers ranks albums both globally and within their band's catalog. [Users](../API/users.md) can search for albums and their rankings within the service.

## Resource properties

Sample `albums` resource

```js

{
    "name": "The Beatles",
    "album": "Rubber Soul",
    "release date": "1965",
    "album score": "987",
    "global album ranking": "1",
    "band catalog album ranking": "1",
    "id": 1
}
```

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `name` | string | The name of the [band](../API/bands.md) that released this album |
| `album` | string | The album name |
| `release date` | string | The album release date |
| `album score` | string | The album's score |
| `global album ranking` | string | The album's ranking across all albums |
| `band catalog album ranking` | string | The album's ranking within the band's catalog |
| `id` | number | The album's unique record ID |

## Supported operations

* `GET`
* [`POST: create a new album`](../API/post-album.md)
* `PUT`
* `PATCH`

## Related resources

* [Bands resource](../API/bands.md) - The band that released this album
* [Users resource](../API/users.md) - Users who can view and interact with albums
