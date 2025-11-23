---
# markdownlint-disable
# vale  off
title: "Environment set-up"
parent: "Get Started Tutorial"
layout: default
nav_order: 1
# tags used by AI files
description: Describes how to configure your local computer to run a local instance of
 rock-rankers-api
 permalink:/get-started/rock-rankers-environment-set-up/
tags: 
    - get-started
categories: 
    - tutorials
ai_relevance: high
importance: 9
prerequisites: []
examples: []
api_endpoints: []
version: "v1.0"
last_updated: "2025-11-22"
# vale  on
# markdownlint-enable
---

<!-- vale Google.Acronyms = NO -->

## Tutorial: Rock-rankers environment set-up

### Install software

Following these steps prepares your development system for a smooth rock-rankers-api
experience.

Expect this preparation to take about 40 minutes to complete.

1. **Check prerequisites**
   * Verify system compatibility. Rock-rankers runs on any development system running a
   current version of the Windows, MacOS, or Linux operating system.
  
2. **Create a GitHub account**
      * Create a [GitHub cloud account](https://github.com).
  
3. **Create a fork of the rock-rankers-api repository**
     * Browse to the
     [rock-rankers-api repository](https://github.com/GillWrites/rock-rankers-api).
     * Create a fork of the rock-rankers repository within your GitHub account. This
     article tells you how: [Git: fork a repo](https://docs.github.com/articles/fork-a-repo).

4. **Install Git command line tools**
    * [Git, command line](https://docs.github.com/en/get-started/quickstart/set-up-git).

5. **Create a clone of forked rock-rankers api on GitHub Desktop**
   * [Install GitHub Desktop](https://desktop.github.com).
   * Create a clone of GitHub cloud on local GitHub Desktop. This article tells you how:
   [Cloning a GitHub repository](https://docs.github.com/en/desktop/adding-and-cloning-repositories/cloning-and-forking-repositories-from-github-desktop).

6. **Install node.js**
      * [A current or LTS version of `node.js`](https://nodejs.org/en/download).

7. **Install json server**
      * Version 0.17.4 of [json-server](https://www.npmjs.com/package/json-server/v/0.17.4).
  
<!-- vale Google.Acronyms = YES -->

## Verify your development environment

1. To test your development system, browse to your rock-rankers-api repository.
   * Open a command line and browse to your `GitHub repository workspace`. This is the
   directory that contains your fork of the `rock-rankers-api` repository.

   ```shell
    cd <your GitHub repository workspace>/
   ```

**For example:**

```shell
         cd /Documents/GitHub/GitHubRepos/
```

   Type `ls` to verify that you see rock-rankers-api folder returned. The output should
   include `rock-rankers-api`.

   ```shell
    ls
    rock-rankers-api
   ```

1. Browse to the `rock-rankers-api/api` folder and verify you can see the json database.
The output should include the `rock-rankers-api.json` database.

```shell
 ls
 api-ranks-db-source.json
```

You are now ready to make a test call to the rock-rankers database.

## Make a test call to the rock-rankers service

1. Enter the following command to start the json server:

   ```shell
    json-server -w api-ranks-db-source.json
   ```

   If you installed the software correctly, you should see
   the service start and display the URL of the service: `http://localhost:3000`.

2. Make a test call to the service.

   ```shell
    curl http://localhost:3000/bands
   ```

If the service is running correctly, you should see a list of bands from the rock-rankers
database, such as in this example.

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

You should see the list of bands.

If you receive an error in any step of the procedure investigate. Correct the error before
continuing. Some common situations that cause errors include:

1. You mistyped a command.
2. You aren't in the correct directory.
3. A required software component didn't install correctly.
4. A required software component isn't up to date.

## Next steps

If you see the list of bands from the rock-rankers service, congratulations. You're ready to
move onto the next steps on your rock-rankers journey.

You can now move on and learn how to perform common rock-rankers tasks in
[Tutorials](../tutorials.md).
