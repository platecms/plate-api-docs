## Posts

### Get all posts

> `GET {base_url}/site_translations/1/posts?post_status=published` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "posts",
      "attributes" : {
        "title": "A Post title",
        "language": "nl",
        "post_status": "published",
        "content": {
          ...
        }
      },
      "relations" : {
        "site_translation_id": 1,
        "content_type_id": 14
      }
    },
    {
      "id": 4,
      "type": "posts",
      "attributes" : {
        "title": "Another Post title",
        "language": "nl",
        "post_status": "published",
        "content": {
          ...
        }
      },
      "relations" : {
        "site_translation_id": 1,
        "content_type_id": 14
      }
    },
  ]
}
```

This endpoint retrieves all posts for a specific site translation

#### HTTP Request

`GET {base_url}/site_translations/:site_translation_id/posts[?post_status=...]`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_translation_id | The id of the site translation to which the posts belong
:site_id | The id of the site to which the posts belong
:post_status | Optional. The post_status of the posts to filter One of "published" and "unpublished".

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/posts` (Returns all posts in a site)

### Get specific post

> `GET {base_url}/site_translations/1/posts/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "posts",
    "attributes" : {
      "title": "A Post title",
      "language": "nl",
      "post_status": "published",
      "content": {
        ...
      }
    },
    "relations" : {
      "site_translation_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint retrieves a specific post.

#### HTTP Request

`GET {base_url}/posts/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_translation_id | The id of the site translation of the post to retrieve
:id | The id of the post to retrieve
:site_id | The id of the site of the post to retrieve

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/posts/:id`
* `GET {base_url}/site_translations/:site_translation_id/posts/:id`

### Create post

> An example of valid JSON POST parameters

```json
{
  "data": {    
    "content_type_id": 14,
    "title": "Created Post",
    "post_status": "unpublished"
  }
}
```

> `POST {base_url}/site_translations/1/posts` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "posts",
    "attributes" : {
      "title": "Created Post",
      "language": "nl",
      "post_status": "unpublished",
      "content": {
        ...
      }
    },
    "relations" : {
      "site_translation_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint creates a post.

#### HTTP Request

`POST {base_url}/site_translations/:site_translation_id/posts`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_translation_id | The id of the site translation to which the new post belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
content_type_id | The content type of the new post | Required
title     | The title of the new post | Required
language  | The language of the new post | Required. Has to be one of the languages of the site of the new post.
slug  | The slug of the new post | Optional
seo_title | The SEO title of the new post |
seo_description | The SEO description of the new post |
post_status  | The status of the new post | Optional. One of "published" or "unpublished". Default: "published"
 | **--Accepts [Content field parameters](#requests-for-content-objects)--** |

### Update post

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "title": "An updated post title",
    "post_status": "published"
  }
}
```

> `PUT {base_url}/site_translations/1/posts/3` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "posts",
    "attributes" : {
      "title": "An updated post title",
      "language": "nl",
      "post_status": "unpublished",
      "content": {
        ...
      }
    },
    "relations" : {
      "site_translation_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint updates a post.

#### HTTP Request

`PUT {base_url}/posts/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_translation_id | The id of the site translation of the post to update
:id | The id of the post to update
:site_id | The id of the site of the post to update

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
title     | The title of the post | Not null
slug     | The slug of the post | Not null
post_status  | The status of the new post | Optional. One of "published" or "unpublished". Default: "published"
 | **--Accepts [Content field parameters](#requests-for-content-objects)--** |

#### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/sites/:site_id/posts/:id`
* `PUT {base_url}/site_translations/:site_translation_id/posts/:id`

### Delete post

> `DELETE {base_url}/site_translations/1/posts/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "posts",
    "attributes" : {
      "title": "A Post title",
      "language": "nl",
      "post_status": "unpublished",
      "content": {
        ...
      }
    },
    "relations" : {
      "site_translation_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint deletes a specific post.

#### HTTP Request

`DELETE {base_url}/posts/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_translation_id | The id of the site translation of the post to delete
:id | The id of the post to delete
:site_id | The id of the site of the post to delete

#### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/sites/:site_id/posts/:id`
* `DELETE {base_url}/site_translations/:site_translation_id/posts/:id`
