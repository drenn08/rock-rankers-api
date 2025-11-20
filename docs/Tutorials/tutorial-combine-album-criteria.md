---
title: "How to filter albums by multiple criteria"
layout: default
nav_order: 4
parent: "Tutorials"
has_children: false
permalink: /Tutorials/Tutorial_GET-albums-filter.md/
has_toc: false
description: "Tutorial outlining how to filter the `albums` endpoint using multiple query parameters"
tags:
  - api
categories:
  - tutorials
version: "v1.0"
last_updated: "2025-11-19"
---
## Tutorial: how to filter albums by multiple criteria

In this tutorial, you'll learn how to query the rock-rankers database to retrieve album information from the `/albums` endpoint using multiple filter criteria. You'll use query parameters to filter albums by both global ranking and release date decade simultaneously.

Expect this tutorial to take about 10 minutes to complete.

### Before you start

Make sure you've completed the [Environment set-up tutorial](./rock-rankers%20environment%20set-up.md) topic on the development system you'll use for the tutorial.

### Filter albums by global ranking and release decade

You use the `GET` method with query parameters to filter `album` information from the `albums` resource. You can combine exact match filters (for numeric values like ranking) with the `_like` operator (for partial text matching on dates).

1. Make sure your local json server is running, or start it by using this command in the terminal, if it's not.
```shell
   cd <your-github-workspace>/rock-rankers-api/api
   json-server --watch api-ranks-db-source.json
```

2. Open a second terminal and run a `GET` command to the `albums` resource using multiple query parameters.

   **Request syntax:**
   ```shell
   http://localhost:3000/albums?global-album-ranking={ranking}&release-date_like={decade}
   ```

   Note: Replace {ranking} with the numeric ranking value and {decade} with the decade prefix (like "199" for the 1990s). The `_like` operator matches any album where the search text appears in the release-date field.

   **Request example:**  
   This request queries the rock-rankers database to retrieve information about albums that have a global ranking of 1 and were released in the 1990s.
   ```shell
   curl "http://localhost:3000/albums?global-album-ranking=1&release-date_like=199"
```

3. Verify the response. If no albums match both criteria, the response will return an empty array:
```json
   []
```

   Note: This result indicates there are no albums in the database with both a global ranking of 1 and a 1990s release date.

### Understanding the filter parameters

This query combines two different types of filters:

* `global-album-ranking=1` uses exact match filtering to find albums with a specific numeric ranking
* `release-date_like=199` uses the `_like` operator to match any album where the release date starts with "199" (covering years 1990-1999)

When you combine multiple query parameters with `&`, the API returns only albums that match all the specified criteria.

### Try different filter combinations

Experiment with other filter combinations to explore the database:

**Example 1: Find top-ranked albums from the 1960s**
```shell
curl "http://localhost:3000/albums?global-album-ranking=1&release-date_like=196"
```

**Example 2: Find albums released in the 1990s**
```shell
curl "http://localhost:3000/albums?release-date_like=199"
```

**Example 3: Find albums with a global ranking of 3**
```shell
curl "http://localhost:3000/albums?global-album-ranking=3"
```

**Example 4: Find albums from the 1960s**
```shell
curl "http://localhost:3000/albums?release-date_like=196"
```

**Example 5: Find top-ranked band catalog albums**
```shell
curl "http://localhost:3000/albums?band-catalog-album-ranking=1"
```

### What you learned

After completing this tutorial, you now know how to:

* Filter albums using multiple query parameters simultaneously
* Combine exact match filters with the `_like` operator
* Search for albums by release decade using partial date matching
* Interpret empty result sets when no albums match your criteria

### Next steps

After doing this tutorial using curl, try these additional query combinations to further explore the API:

**Find albums with high scores from the 1960s:**
```shell
curl "http://localhost:3000/albums?release-date_like=196&album-score_gte=900"
```

**Find albums by a specific band:**
```shell
curl "http://localhost:3000/albums?name=Radiohead"
```

**Find albums released in the 1990s with high rankings:**
```shell
curl "http://localhost:3000/albums?release-date_like=199&global-album-ranking_lte=5"
```

**Find albums from the 1960s:**
```shell
curl "http://localhost:3000/albums?release-date_like=196"
```

You can also try repeating these queries using the [Postman](https://learning.postman.com/docs/sending-requests/requests/) GUI. To do this, adapt the values from the tutorial to Postman's Params section to make REST API calls. You can add multiple query parameters in Postman's Params section.