---
title: "How to retrieve band information"
layout: default
nav_order: 1
parent: "Tutorials"
has_children: false
permalink: /Tutorials/Tutorial_GET-band.md/
has_toc: false
description: "Tutorial outlinig how to query the `bands` endpoint"
tags:
  - api
categories:
  - tutorials
version: "v1.0"
last_updated: "2025-11-19"
---
## Tutorial: how to retrieve band information

In this tutorial, you'll learn
how to query the rock-rankers
 database to retrieve band information
from the `/bands` endpoint.
You'll use the `band` query parameter to:

* Find all bands.
* Filter bands by their band name.
  
Expect this tutorial to take about 10 minutes to complete.

### Before you start

Make sure you've completed the [Environment set-up tutorial](./rock-rankers%20environment%20set-up.md) topic on the development system you'll use for the tutorial.

### Find all bands

You use the `GET` method to retrieve `band` information from the `bands` resource.

1. Make sure your local json server is running, or start it by using this command in the terminal, if it's not.

   ```shell
   cd <your-github-workspace>/rock-rankers-api/api
   json-server --watch api-ranks-db-source.json
   ```

2. Open a second terminal and run a `GET` command to the `bands` resource. Note: `GET` is the default method used by `curl`, so you don't have to add `GET` to the request.

   ```shell
   curl http://localhost:3000/bands
   ```

3. Verify the response returns information for all `bands` within the rock-rankers database.

```json
   [
     {
       "id": 1,
       "name": "The Beatles",
       "genre": "rock, pop, psychedelia",
       "years-active": "1960-1970",
       "origin": "Liverpool, England"
     },
     {
       "id": 2,
       "name": "Led Zeppelin",
       "genre": "rock, blues, folk, metal",
       "years-active": "1968-1980",
       "origin": "London, England"
     },
     {
       "id": 3,
       "name": "Radiohead",
       "genre": "rock, alternative, electronica",
       "years-active": "1985-present",
       "origin": "Abingdon, Oxfordshire, England"
     },
     {
       "id": 4,
       "name": "Rage Against the Machine",
       "genre": "rock, alternative, metal, rap, funk",
       "years-active": "1991-2000; 2008-2011; 2019-2024",
       "origin": "Los Angeles, California, USA"
     },
     {
       "id": 5,
       "name": "Soundgarden",
       "genre": "rock, alternative, grunge",
       "years-active": "1984-1997; 2010-2017",
       "origin": "Seattle, Washington, USA"
     }
   ]
```

### Find a band by name

Retrieve information for a single band with a `GET` request using the `name` query parameter.

1. Make sure your local json server is running, or start it by using this command in the terminal, if it's not.

   ```shell
   cd <your-github-workspace>/rock-rankers-api/api
   json-server --watch api-ranks-db-source.json
   ```

2. Open a second terminal and run a `GET` command to the `bands` resource using the `name` query parameter.

   **Request syntax:**

   ```shell
   http://localhost:3000/bands?name={band-name}
   ```

   Note: replace {band-name}
   with the actual band name.
   If the band name has
   spaces, use
   %20 for each space, like Led%20Zeppelin.

   **Request example:**  
   This request queries the rock-rankers database
   to retrieve information
   about the band Led Zeppelin.

   ```shell
   curl "http://localhost:3000/bands?name=Led%20Zeppelin"
   ```

3. Verify the response. The expected response syntax for this query is as follows.

```json
   {
     "id": 2,
     "name": "Led Zeppelin",
     "genre": "rock, blues, folk, metal",
     "years-active": "1968-1980",
     "origin": "London, England"
   }
```

### What you learned

After completing this tutorial, you now know how to:

* Retrieve information
  for all bands in the
  rock-rankers database.
* Find bands by name
  using the `name` query
  parameter with curl.

### Next steps

After doing this tutorial
using curl, try repeating
it using the
[Postman](https://learning.postman.com/docs/sending-requests/requests/) GUI. To do this,
adapt the values from
the tutorial to
Postman's `GET` request
format to make REST API calls.
