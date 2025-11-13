---
title: "Bands"
layout: default
nav_order: 1
parent: "API Reference Docs"
permalink: /api-reference-docs/bands/
has_toc: false
description: "Information about the `bands` resource"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-11"
---

## `bands` resource

Base endpoint:

```shell

{server_url}/bands
```

Contains information about the bands in the Rock Rankers service.

A band resource describes musical bands and their information. Each band can have many [albums](../API/albums.md) associated with it. [Users](../API/users.md) can explore and rank bands in the rock-rankers service.

## Resource properties

Sample `bands` resource

```js

{
    "name": "The Beatles",
    "genre": "rock, pop, psychedelia",
    "years active": "1960-1970",
    "origin": "Liverpool, England",
    "id": 1
}
```

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `name` | string | The band's name |
| `genre` | string | The band's genre, comma-separated |
| `years active` | string | The years the band was active |
| `origin` | string | The band's place of origin |
| `id` | number | The band's unique record ID |

## Related resources

* [Album resource](../API/albums.md) - Albums released by this band
* [User resource](../API/users.md) - Users who can view and interact
with the bands.
