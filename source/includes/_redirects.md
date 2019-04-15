## Redirects

### Get all redirects

> `GET {base_url}/posts/1/redirects/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "type": "redirects",
      "attributes": {
        "from_url": "/some_old/path/here"
      },
      "relations": {
        "post_id": 1
      }
    },
    {
      "id": 2,
      "type": "redirects",
      "attributes": {
        "from_url": "/some_other/path/there"
      },
      "relations": {
        "post_id": 1
      }
    }
  ]
}
```

This endpoint retrieves all redirects in a specific post.

#### HTTP Request

`GET {base_url}/posts/:post_id/redirects`

#### URL Parameters

Parameter | Description
--------- | -----------
:post_id | The id of the post to which the redirects belong


### Get specific Redirect

> `GET {base_url}/posts/1/redirects/1` returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "type": "redirects",
    "attributes": {
      "from_url": "/some_old/path/here"
    },
    "relations": {
      "post_id": 1
    }
  }
}

```

This endpoint retrieves a specific redirect.

#### HTTP Request

`GET {base_url}/redirects/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the redirect to retrieve

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/posts/:post_id/redirects/:id`

### Create redirect

> An example of valid JSON POST parameters

```json
{
  "data": {    
    "from_url": "/an/old/path",
  }
}
```

> `POST {base_url}/posts/1/redirects` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "redirects",
    "attributes": {
      "from_url": "/an/old/path"
    },
    "relations": {
      "post_id": 1
    }
  }
}
```

This endpoint creates a redirect.

#### HTTP Request

`POST {base_url}/posts/:post_id/redirects`

#### URL Parameters

Parameter | Description
--------- | -----------
:post_id | The id of the post to which the new redirect belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -------------
from_url | The path which is redirected | Is a valid [http path](https://tools.ietf.org/html/rfc3986#section-3.3).

### Update redirect

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "from_url": "/a/new/path",
  }
}
```

> `PUT {base_url}/posts/1/redirects/1` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "type": "redirects",
    "attributes": {
      "from_url": "/a/new/path"
    },
    "relations": {
      "post_id": 1
    }
  }
}
```

This endpoint updates a specific redirect.

#### HTTP Request

`PUT {base_url}/redirects/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:post_id | The id of the post to which the updated redirect belongs
:id | The id of the redirect to update

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
from_url | The new path which is redirected | Is a valid [http path](https://tools.ietf.org/html/rfc3986#section-3.3).

#### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/posts/:post_id/redirects/:id`


### Delete redirect

> `DELETE {base_url}/posts/1/redirects/1` returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "type": "redirects",
    "attributes": {
      "from_url": "/a/new/path"
    },
    "relations": {
      "post_id": 1
    }
  }
}
```

This endpoint deletes a specific redirect.

#### HTTP Request

`DELETE {base_url}/redirects/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:post_id | The id of the post to which the delete redirect belongs
:id | The id of the redirect to delete

#### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/posts/:post_id/redirects/:id`
