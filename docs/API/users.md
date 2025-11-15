---
title: "Users"
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
last_updated: "2025-11-11"
---

## `users` resource

Base endpoint:

```shell

{server_url}/users
```

Contains information about the users of the service.

A user resource describes the users who subscribe to the Rock Rankers service.
Users can view and interact with [bands](../API/bands.md) and [albums](../API/albums.md) resources.

## Resource properties

Sample `user` resource

```js

{
    "lastName": "Renn",
    "firstName": "David",
    "email": "drenn08@uw.edu",
    "id": 1
}
```

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `lastName` | string | The user's last name |
| `firstName` | string | The user's first name |
| `email` | string | The user's email address |
| `id` | number | The user's unique record ID |

## Read operations

* [Get all users](../API/users-get-all-users.md)
* [Get users by ID](.//users-get-user-by-id.md)

## Related resources

* [Bands resource](../API/bands.md) - Bands in the Rock Rankers service
* [Album resource](../API/albums.md) - Albums in the Rock Rankers service
