---
title: "Users Resource"
layout: default
nav_order: 3
parent: "API Reference Docs"
has_children: true
permalink: /api-reference-docs/users/
has_toc: false
description: "Information about the `users` resource"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-14"
---

## `users` resource

Base endpoint:

```shell
{server_url}/users
```

Provides information about users in the Rock Rankers service.

The user resource contains the users who subscribe to the Rock Rankers service.
Users can view and interact with [bands resource](./bands.md) and [albums resource](./albums.md) resources.

## Resource properties

Sample `user` resource

```js
{
    "id": 1,
    "last-name": "Renn",
    "first-name": "David",
    "email": "drenn08@uw.edu"
}
```

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `id` | integer | The user's unique record ID |
| `last-name` | string | The user's last name |
| `first-name` | string | The user's first name |
| `email` | string | The user's email address |

## Supported operations

* `GET`
* [`POST`: create a new user](./post-user.md)
* [`PUT`: update an existing user](./put-user.md)
* [`PATCH`: partially update a user](./patch-user.md)
* [`DELETE`: delete a user](./delete-user.md)

## Related resources

* [bands resource](./bands.md) - Bands in the Rock Rankers service
* [albums resource](./albums.md) - Albums in the Rock Rankers service
