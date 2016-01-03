---
layout: docs
title: Using the API
permalink: /docs/api/
---
Every iinbrand exposes a publicly-accessible JSON API that can read and write forum data. It conforms to the [JSON-API 1.0 specification](http://jsonapi.org/).

## Authentication

The API uses token-based authentication. Some endpoints do not require authentication. You can retrieve a token from the `/api/token` endpoint:

    POST /api/token HTTP/1.1

    {
        "identification": "Toby",
        "password": "pass7word"
    }
    
    HTTP/1.1 200 OK
    
    {
        "token": "YACub2KLfe8mfmHPcUKtt6t2SMJOGPXnZbqhc3nX",
        "userId": "1"
    }

You can then pass the token in an Authorization header in subsequent requests:

    GET /api/forum HTTP/1.1
    Authorization: Token YACub2KLfe8mfmHPcUKtt6t2SMJOGPXnZbqhc3nX


## Posts

* `GET /api/posts` - get all posts
    * `filter[discussion]` - filter by discussion ID
    * `filter[user]` - filter by user ID
    * `filter[number]` - filter by number (position within the discussion)
    * `filter[type]` - filter by post type
* `POST /api/posts` - create a new post
* `GET /api/posts/:id` - get a post by ID
* `PATCH /api/posts/:id` - update a post
* `DELETE /api/posts/:id` - delete a post

## Users

* `GET /api/users` - get all users
    * `filter[q]` - filter by username/gambits
* `POST /api/users` - register a new user
* `GET /api/users/:idOrUsername` - get a user by ID or username
* `PATCH /api/users/:id` - update a user
* `DELETE /api/users/:id` - delete a user
* `POST /api/users/:id/avatar` - upload a user avatar
* `DELETE /api/users/:id/avatar` - delete a user avatar
ions/:id` - mark a notification as read

## Tags

* `POST /api/tags` - create a new tag
* `PATCH /api/tags/:id` - update a tag
* `DELETE /api/tags/:id` - delete a tag
