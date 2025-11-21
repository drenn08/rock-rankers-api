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

In this tutorial, you'll learn
how to query the rock-rankers
 database to retrieve album information
from the `/albums` endpoint.
You'll use the `album` query parameter to:

* Find all albums.
* Filter albums by their album name.
  
Expect this tutorial to take about 10 minutes to complete.

### Before you start

Make sure you've completed the [Environment set-up tutorial](./rock-rankers%20environment%20set-up.md) topic on the development system you'll use for the tutorial.

### Find all albums

You use the `GET` method to retrieve `album` information from the `albums` resource.

1. Make sure your local json server is running, or start it by using this command in the terminal, if it's not.

   ```shell
   cd <your-github-workspace>/rock-rankers-api/api
   json-server --watch api-ranks-db-source.json
   ```

2. Open a second terminal and run a `GET` command to the `albums` resource. Note: `GET` is the default method used by `curl`, so you don't have to add `GET` to the request.

   ```shell
   curl http://localhost:3000/albums
   ```

3. Verify the response returns information for all `albums` within the rock-rankers database.

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

Retrieve information for a single album with a `GET` request using the `album` query parameter.

1. Make sure your local json server is running, or start it by using this command in the terminal, if it's not.

   ```shell
   cd <your-github-workspace>/rock-rankers-api/api
   json-server --watch api-ranks-db-source.json
   ```

2. Open a second terminal and run a `GET` command to the `albums` resource using the `album` query parameter.

   **Request syntax:**

   ```shell
   http://localhost:3000/albums?album={album-name}
   ```

   Note: replace {album-name}
   with the actual album name.
   If the album name has
   spaces, use
   %20 for each space, like Ok%20Computer.

   **Request example:**  
   This request queries the rock-rankers database
   to retrieve information
   about the album Ok Computer.

   ```shell
   curl "http://localhost:3000/albums?album=Ok%20Computer"
   ```

3. Verify the response. The expected response syntax for this query is as follows.

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

### What you learned

After completing this tutorial, you now know how to:

* Retrieve information
  for all albums in the
  rock-rankers database.
* Find albums by name
  using the `album` query
  parameter with curl.

  ## Troubleshooting

| Status Code       | Problem                                        | Solution                                                                 |
|-------------------|------------------------------------------------|--------------------------------------------------------------------------|
| 200 OK            | Request successful                             | No action needed; the response contains the album data           |
| 400 Bad Request   | Invalid query parameter format                 | Check that parameter names are correct, for example, `album` not `album-name`, and values are properly formatted |
| 404 Not Found     | No albums match the filter criteria             | Verify your album name is correct; check spelling and that space encoding contains `%20`. Try retrieving all albums first to confirm the album exists in the database |
| 500 Internal Server Error | json-server encountered an error       | Ensure json-server is running; restart it using `json-server --watch api-ranks-db-source.json` |
| ECONNREFUSED      | Can't connect to json-server                  | Verify json-server is running on port 3000; check that no other service is using the port |

### Next steps

After doing this tutorial
using curl, try repeating
it using the
[Postman](https://learning.postman.com/docs/sending-requests/requests/) GUI. To do this,
adapt the values from
the tutorial to
Postman's `GET` request
format to make REST API calls.
