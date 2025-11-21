---
title: "How to filter albums using combined criteria"
layout: default
nav_order: 4
parent: "Tutorials"
has_children: false
permalink: /Tutorials/tutorial-get-album-filters
has_toc: false
description: "Tutorial outlining how to filter the `albums` endpoint using many query parameters"
tags:
  - api
categories:
  - api-reference
version: "v1.0"
last_updated: "2025-11-20"
---
## Tutorial: how to filter albums using combined criteria

In this tutorial, you'll learn how to query the rock-rankers database to retrieve
album information from the `/albums` endpoint using a combination of filters. You'll use query parameters to filter albums by both ranking and release
date range.

Expect this tutorial to take about 15 minutes to complete.

## Before you start

Make sure you've completed the
[Environment set-up tutorial](./rock-rankers%20environment%20set-up.md) topic on
the development system you'll use for the tutorial.

## Filter albums by ranking and release date

You use the `GET` method with range operators to filter `album` information from
the `albums` resource. Range operators allow you to search for albums within
specific numeric ranges, such as date ranges or ranking thresholds.

1. Make sure your local json server is running, or start it by using this command
   in the terminal, if it's not.

   ```shell
   cd <your-github-workspace>/rock-rankers-api/api
   json-server --watch api-ranks-db-source.json
   ```

2. Open a second terminal. Run a `GET` command to the `albums` resource using
   combined query parameters with range operators.

   **Request syntax:**

   ```shell
   http://localhost:3000/albums?global-album-ranking={ranking}&release-date_gte={start_year}&release-date_lte={end_year}
   ```

   Note: replace {ranking} with the global ranking you want to search for,
   {start_year} with the beginning of the date range, and {end_year} with the end
   of the date range. The `_gte` operator means "greater than or equal to" and
   `_lte` means "less than or equal to."

   **Request example:**  
   This request queries the rock-rankers database to retrieve information about
   albums that have a global ranking of 1 and released in the 1960&nbsp;s.

   ```shell
   curl "http://localhost:3000/albums?global-album-ranking=1&release-date_gte=1960&release-date_lte=1969"
   ```

3. Verify the response returns only albums matching all criteria.

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
     }
   ]
```

### Understanding range operators

Range operators are useful when working with numeric fields like dates, scores, or
rankings. In this example:

* `global-album-ranking=1` matches albums with an exact ranking of 1
* `release-date_gte=1960` matches albums released in 1960 or later
* `release-date_lte=1969` matches albums released in 1969 or earlier

When you combine query parameters with `&`, the API returns only albums that match
all the specified criteria.

### Available range operators

json-server supports these range operators for numeric fields:

* `_gte` - greater than or equal to
* `_lte` - less than or equal to
* `_gt` - greater than
* `_lt` - less than

### Try different filter combinations

Experiment with other filter combinations to explore the database:

**Example 1: find albums from the 1990&nbsp;s**

```shell
curl "http://localhost:3000/albums?release-date_gte=1990&release-date_lte=1999"
```

**Example 2: find albums with global ranking of 5 or better**

```shell
curl "http://localhost:3000/albums?global-album-ranking_lte=5"
```

**Example 3: find albums released after 1995**

```shell
curl "http://localhost:3000/albums?release-date_gte=1995"
```

### What you learned

After completing this tutorial, you now know how to:

* Filter albums using combined query parameters
* Use range operators, `_gte`, `_lte`, `_gt`, `_lt`, to filter numeric fields
* Combine search criteria to narrow down results from the rock-rankers database

## Troubleshooting

If you encounter errors while following this tutorial, refer to the following table:

| Status Code       | Problem                                        | Solution                                                                 |
|-------------------|------------------------------------------------|--------------------------------------------------------------------------|
| 200 OK            | Request successful                             | No action needed; the response contains the filtered album data          |
| 400 Bad Request   | Invalid query parameter format                 | Check that parameter names are correct, for example, `release-date_gte` not `release_date_gte, and values are valid numbers |
| 404 Not Found     | No albums match the filter criteria            | Verify your filter values are correct; try broadening your search criteria or check that your database contains matching records |
| 500 Internal Server Error | json-server encountered an error       | Ensure json-server is running; restart it using `json-server --watch api-ranks-db-source.json` |
| ECONNREFUSED      | Can't connect to json-server                  | Verify json-server is running on port 3000; check that no other service is using the port |

## Next steps

### Try more query combinations**

After doing this tutorial using curl, try more query combinations to further
explore the API, for example:

**Find top-ranked albums, with a ranking 1-3, from the 1990&nbsp;s:**

```shell
curl "http://localhost:3000/albums?global-album-ranking_lte=3&release-date_gte=1990&release-date_lte=1999"
```

**Find albums released in the 1980&nbsp;s:**

```shell
curl "http://localhost:3000/albums?release-date_gte=1980&release-date_lte=1989"
```

**Find albums with scores higher than 950:**

```shell
curl "http://localhost:3000/albums?album-score_gte=950"
```

**Find albums released before 1970:**

```shell
curl "http://localhost:3000/albums?release-date_lte=1970"
```

**Find albums ranked 2 or higher released after 1990:**

```shell
curl "http://localhost:3000/albums?global-album-ranking_lte=2&release-date_gte=1990"
```

### Try repeating this tutorial using Postman**

You can also try repeating these queries using the
[Postman](https://learning.postman.com/docs/sending-requests/requests/) GUI. To do
this, adapt the values from the tutorial to Postman's Params section to make REST
API calls. You can add many query parameters in Postman's **Params** section.
