---
title: "Rock-Rankers API"
layout: default
nav_order: 1
description: "Rock-rankers API documentation homepage"
permalink: /
---
## Rock-rankers API

### Where music meets metrics

Welcome to Rock-rankers, the ultimate API for rock fans who love data as much as they love music.

## What's rock-rankers?

* Rock-rankers is a lightweight REST API that performs metrics-driven rock music analysis.
* Rock-rankers scores, ranks, and compares bands, albums, and songs.
* The results are clear, visual, data-driven insights that serious rock fans demand.

## Who uses rock-rankers?

Rock-rankers is for developers building streaming apps and sites for rock fans who love to analyze and debate music.

## See rock-rankers in action

Placeholder, Add a sample rock rakers query and response.

### Note

The Rock Rankers API is an educational project demonstrating REST API documentation for managing rock music rankings. It runs locally via JSON Server. See [Getting Started](./Tutorials/rock-rankers%20environment%20set-up.md) for setup.

## Get started

Follow this tutorial to learn how to do a one-time setup of your rock-rankers environment.  

* [rock-rankers environment set-up](./Tutorials/rock-rankers%20environment%20set-up.md)

## Tutorials

Learn how to perform common rock-rankers tasks:

* [How to retrieve band information](./Tutorials/tutorial-get-band.md)
* [How to retrieve album information](./Tutorials/tutorial-get-album.md)
* [How to filter bands with combined query parameters](./Tutorials/tutorial-get-band-filters.md)
* [How to filter albums with combined query parameters](./Tutorials/tutorial-get-album-filters.md)

## Learn more

### API reference docs

 **View rock-rankers resource and endpoints**

* [bands](./API/bands.md)
* [albums](./API/albums.md)
* [users](./API/users.md)

**Edit the rock-rankers database**  
Rock-rankers supports the following typical `HTTP` functions:

| HTTP Method | Operation | Description |
|-------------|-----------|-------------|
| POST | Create | Create new records |
| PUT | Update | Update an entire record |
| PATCH | Update | Update specific record fields |
| DELETE | Delete | Delete a record |

**Endpoints by Resource**  

**Bands**

* [POST: create a new band](./API/post-band.md)
* [PUT: update an existing band](./API/put-band.md)
* [PATCH: partially update a band](./API/patch-band.md)
* [DELETE: delete a band](./API/delete-band.md)

**Albums**

* [POST: create a new album](./API/post-album.md)
* [PUT: update an existing album](./API/put-album.md)
* [PATCH: partially update an album](./API/patch-album.md)
* [DELETE: delete an album](./API/delete-album.md)

**Users**

* [POST: create a new user](./API/post-user.md)
* [PUT: update an existing user](./API/put-user.md)
* [PATCH: partially update a user](./API/patch-user.md)
* [DELETE: delete a user](./API/delete-user.md)
  
### View the rock-rankers repo and OpenAPI specification

* [Rock-rankers api repo](https://github.com/drenn08/rock-rankers-api)
* [View OpenAPI Specification](https://raw.githubusercontent.com/GillWrites/rock-rankers-api/main/api/rock-rankers-spec.yml)

## Troubleshooting

### How to troubleshoot the most common rock-rankers api error messages

| HTTP Status Code | Error Type | Description | Common Causes for POST Requests | Troubleshooting Steps |
|-----------------|------------|-------------|-------------------------------|----------------------|
| 400 | Bad Request | The server can't process the request due to malformed syntax or invalid parameters. | You omitted required fields in the request body. You used invalid data types. You provided an email with invalid format. You exceeded field length limits. You specified invalid values for numeric ranges. | Include all required fields in your JSON request body. For users: include `last-name`, `first-name`, and `email`. For bands: include `name`, `genre`, `years-active`, and `origin`. For albums: include `name`, `album`, `release-date`, and `album-score`. Format email addresses with an @ symbol and domain. Limit field lengths to their maximums. Limit names to 100 characters and email to 255 characters. Set `album-score` between 0 and 1000. Set `release-date` between 1900 and 2100. Review the `details` array in the error response for specific field issues. |
| 401 | Unauthorized | The server requires authentication or your credentials are invalid. | You didn't include the `Authorization` header in your POST request. You didn't include a Bearer token. Your token has expired or is invalid. | Add the Authorization header with format: `Authorization: Bearer <your-token>`. Confirm your token is current and hasn't expired. Format the header with "Bearer" followed by a space and your token. Send the token in the header, not in the request body. |
| 403 | Forbidden | The server refuses to your request authorization. | You lack write or create permissions. Your account doesn't allow creating new resources. Your API key lacks create scope for users, bands, or albums. | Confirm your account has write or create permissions for the resource type. Verify your API key has the correct scope for POST operations. Check for account-level restrictions that prevent resource creation. Test a different resource endpoint to determine if the server restricts a specific resource. Contact <help@rockrankers.com> if you believe you should have create access. |
| 429 | Too Many Requests | You have exceeded the rate limit. | You created too many resources in rapid succession. Your bulk import operations exceeded rate limits. Your automated scripts posted too frequently. | Read the `Retry-After` header value and wait that many seconds before you retry. Add rate limiting to your code with delays between POST requests. Batch your operations if the API supports it. Space out resource creation with appropriate delays. Example: add 1 to 2 seconds between requests. Reduce how frequently you make POST operations. |
| 500 | Internal Server Error | The server encountered an unexpected error. | The server failed to insert data into the database. The backend encountered a validation error during resource creation. The server failed to generate an ID. The server encountered a constraint violation. | Retry your POST request after 30 to 60 seconds with the same data. Confirm your request body format is correct and matches the schema. Save the `requestId` from the error response. Verify you set the correct `Content-Type: application/json` header. Try creating a different resource to see if the error relates to specific data. Contact <api-support@example.com> with the `requestId`, endpoint URL, and request body you used. |

## Contact rock-rankers

Rock-rankers would love to hear from you: hello&rockrakers.com
