---
title: "How to retrieve album information"
layout: default
nav_order: 2
parent: "Tutorials"
has_children: false
permalink: /Tutorials/tutorial-GET-album/
has_toc: false
description: "Tutorial outlining how to query the `albums` endpoint"
tags:
  - api
categories:
  - tutorials
version: "v1.0"
last_updated: "2025-11-19"
---
## Tutorial: how to retrieve album information

This tutorial shows how to query the rock-rankers database to get album information from
the `/albums` endpoint. The tutorial uses the `album` query parameter to:

* Find all albums.
* Filter albums by album name.
  
This tutorial takes about 10 minutes to complete.

### Before starting

Complete the [Environment set-up tutorial](./rock-rankers%20environment%20set-up.md) topic on
the development system before starting this tutorial.

### Find all albums

The `GET` method retrieves `album` information from the `albums` resource.

1. Check that the local json server is running. Start the server with this command in the terminal.

   ```shell
   cd <your-github-workspace>/rock-rankers-api/api
   json-server --watch api-ranks-db-source.json
   ```

2. Open a second terminal. Run a `GET` command to the `albums` resource. Note: `GET` is the
   default method for `curl`. No need to add `GET` to the request.

   ```shell
   curl http://localhost:3000/albums
   ```

3. Check the response. The response returns information for all `albums` in the rock-rankers
   database.

```json
   [
     {
       "id": 1,
       "name": "The Beatles",
       "album": "Rubber Soul",
       "release-date": 1965,
       "album-score": 987,
       "global-album-ranking": 1,
       "band-catalog-album-ranking": 1
     },
     {
       "id": 2,
       "name": "Led Zeppelin",
       "album": "Led Zeppelin I",
       "release-date": 1969,
       "album-score": 961,
       "global-album-ranking": 2,
       "band-catalog-album-ranking": 1
     },
     {
       "id": 3,
       "name": "Radiohead",
       "album": "Ok Computer",
       "release-date": 1997,
       "album-score": 955,
       "global-album-ranking": 3,
       "band-catalog-album-ranking": 1
     },
     {
       "id": 4,
       "name": "Rage Against the Machine",
       "album": "Rage Against the Machine",
       "release-date": 1992,
       "album-score": 879,
       "global-album-ranking": 4,
       "band-catalog-album-ranking": 1
     },
     {
       "id": 5,
       "name": "Soundgarden",
       "album": "Superunknown",
       "release-date": 1994,
       "album-score": 945,
       "global-album-ranking": 5,
       "band-catalog-album-ranking": 1
     }
   ]
```

### Find an album by name

Retrieve information for a single album with a `GET` request. Use the `album` query parameter.

1. Check that the local json server runs. Start the server with this command in the terminal.

   ```shell
   cd <your-github-workspace>/rock-rankers-api/api
   json-server --watch api-ranks-db-source.json
   ```

2. Open a second terminal. Run a `GET` command to the `albums` resource. Use the `album` query
   parameter.

   **Request syntax:**

   ```shell
   http://localhost:3000/albums?album={album-name}
   ```

   Note: replace {album-name} with the actual album name. Album names with spaces need %20 for
   each space, like Ok%20Computer.

   **Request example:**  
   This request queries the rock-rankers database to get information about the album
   Ok Computer.

   ```shell
   curl "http://localhost:3000/albums?album=Ok%20Computer"
   ```

3. Check the response. The expected response syntax for this query follows.

```json
   {
     "id": 3,
     "name": "Radiohead",
     "album": "Ok Computer",
     "release-date": 1997,
     "album-score": 955,
     "global-album-ranking": 3,
     "band-catalog-album-ranking": 1
   }
```

### What this tutorial covered

After completing this tutorial, you now know how to:

* Retrieve information for all albums in the rock-rankers database.
* Find albums by name using the `album` query parameter with curl.

### Next steps

Try this tutorial again using the [Postman](https://learning.postman.com/docs/sending-requests/requests/)
GUI. Adapt the values from the tutorial to Postman's `GET` request format to make REST API calls.
