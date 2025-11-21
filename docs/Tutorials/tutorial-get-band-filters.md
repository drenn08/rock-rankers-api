---
title: "How to filter bands using combined criteria"
layout: default
nav_order: 3
parent: "Tutorials"
has_children: false
permalink: /Tutorials/tutorial=get-bands-filter.md/
has_toc: false
description: "Tutorial outlining how to filter the `bands` endpoint using many query parameters"
tags:
  - api
categories:
  - tutorials
version: "v1.0"
last_updated: "2025-11-20"
---
## Tutorial: how to filter bands using combined criteria

In this tutorial, you'll learn how to query the rock-rankers database to retrieve
band information from the `/bands` endpoint using a combination of filters.
You'll use query parameters to filter bands by both genre and origin.

Expect this tutorial to take about 15 minutes to complete.

### Before you start

Make sure you've completed the
[Environment set-up tutorial](./rock-rankers%20environment%20set-up.md) topic on
the development system you'll use for the tutorial.

### Filter bands by genre and origin

You use the `GET` method with the `_like` operator to filter `band` information
from the `bands` resource. The `_like` operator performs partial text matching,
allowing you to search for bands that contain specific text in their fields.

1. Make sure your local json server is running, or start it by using this command
   in the terminal, if it's not.

   ```shell
   cd <your-github-workspace>/rock-rankers-api/api
   json-server --watch api-ranks-db-source.json
   ```

2. Open a second terminal. Run a `GET` command to the `bands` resource using
   combined query parameters with the `_like` operator.

   **Request syntax:**

   ```shell
   http://localhost:3000/bands?genre_like={genre}&origin_like={location}
   ```

   Note: replace {genre} with the genre you want to search for and {location} with
   the origin location. The `_like` operator matches any band where the search
   text appears anywhere in the field.

   **Request example:**  
   This request queries the rock-rankers database to retrieve information about
   bands that have "rock" in their genre and "California" in their origin.

   ```shell
   curl "http://localhost:3000/bands?genre_like=rock&origin_like=California"
   ```

3. Verify the response returns only bands matching both criteria.

```json
   [
     {
       "id": 4,
       "name": "Rage Against the Machine",
       "genre": "rock, alternative, metal, rap, funk",
       "years-active": "1991-2000; 2008-2011; 2019-2024",
       "origin": "Los Angeles, California, USA"
     }
   ]
```

### Understanding the `_like` operator

The `_like` operator is useful when working with fields that contain many values
or descriptive text. In this example:

* `genre_like=rock` matches any band where "rock" appears in the genre field, even
  if the genre also includes other styles like "alternative" or "metal"
* `origin_like=California` matches any band where "California" appears in the
  origin field

When you combine query parameters with `&`, the API returns only bands that match
all the specified criteria.

### Try different filter combinations

Experiment with other filter combinations to explore the database:

**Example 1: find alternative bands from Seattle**

```shell
curl "http://localhost:3000/bands?genre_like=alternative&origin_like=Seattle"
```

**Example 2: find bands from England**

```shell
curl "http://localhost:3000/bands?origin_like=England"
```

**Example 3: find metal bands**

```shell
curl "http://localhost:3000/bands?genre_like=metal"
```

### What you learned

After completing this tutorial, you now know how to:

* Filter bands using combined query parameters
* Use the `_like` operator to perform partial text matching
* Combine search criteria to narrow down results from the rock-rankers database

### Next steps

After doing this tutorial using curl, try more query combinations to further
explore the API, for example:

**Find grunge bands from the USA:**

```shell
curl "http://localhost:3000/bands?genre_like=grunge&origin_like=USA"
```

**Find blues bands from England:**

```shell
curl "http://localhost:3000/bands?genre_like=blue&origin_like=England"
```

**Find bands from Los Angeles:**

```shell
curl "http://localhost:3000/bands?origin_like=Los%20Angeles"
```

**Find alternative rock bands:**

```shell
curl "http://localhost:3000/bands?genre_like=alternative&genre_like=rock"
```

**Find bands from London:**

```shell
curl "http://localhost:3000/bands?origin_like=London"
```

You can also try repeating these queries using the
[Postman](https://learning.postman.com/docs/sending-requests/requests/) GUI. To do
this, adapt the values from the tutorial to Postman's Params section to make REST
API calls. You can add many query parameters in Postman's Params section.
