## Elements

### Get all elements

> `GET {base_url}/columns/1/elements/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "elements",
      "attributes" : {
        "position": 1,
        "content": {
          ...
        }
      },
      "relations" : {
        "column_id": 1,
        "content_type_id": 14
      }
    },
    {
      "id": 4,
      "type": "elements",
      "attributes" : {
        "position": 2,
        "name": "Another Element name",
          ...
        }
      },
      "relations" : {
        "column_id": 1,
        "content_type_id": 14
      }
    }
  ]
}
```

This endpoint retrieves all elements for a specific column

#### HTTP Request

`GET {base_url}/columns/:column_id/elements`

#### URL Parameters

Parameter | Description
--------- | -----------
:column_id | The id of the columns to which the elements belong
:site_id | The id of the site to which the elements belong
:site_translation_id | The id of the site translation to which the elements belong
:post_id | The id of the posts to which the elements belong
:section_id | The id of the sections to which the elements belong
:row_id | The id of the rows to which the elements belong

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/elements` (Returns all elements in a site)
* `GET {base_url}/site_translations/:site_translation_id/elements` (Returns all elements in a site translation)
* `GET {base_url}/posts/:post_id/elements` (Returns all elements in a post)
* `GET {base_url}/sections/:section_id/elements` (Returns all elements in a section)
* `GET {base_url}/rows/:row_id/elements` (Returns all elements in a row)

### Get specific element

> `GET {base_url}/columns/1/elements/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "elements",
    "attributes" : {
      "position": 1,
      "content": {
        ...
      }
    },
    "relations" : {
      "column_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint retrieves a specific element.

#### HTTP Request

`GET {base_url}/elements/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the element to retrieve

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/elements/:id`
* `GET {base_url}/site_translations/:site_translation_id/elements/:id`
* `GET {base_url}/posts/:post_id/elements/:id`
* `GET {base_url}/sections/:section_id/elements/:id`
* `GET {base_url}/rows/:row_id/elements/:id`
* `GET {base_url}/columns/:column_id/elements/:id`

### Create element

> An example of valid JSON POST parameters

```json
{
  "data": {    
    "content_type_id": 14,
    "position": 1
  }
}
```

> `POST {base_url}/columns/1/elements` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "elements",
    "attributes" : {
      "position": 1,
      "content": {
        ...
      }
    },
    "relations" : {
      "column_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint creates an element in a column.

#### HTTP Request

`POST {base_url}/columns/:column_id/elements`

#### URL Parameters

Parameter | Description
--------- | -----------
:column_id | The id of the columns to which the new element belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
content_type_id | The content type of the new element | Required
 | **--Accepts the position field for [positionable objects](#requests-for-positionable-objects)--** |
 | **--Accepts [Content object parameters](#requests)--** |

### Update element

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "position": 3
  }
}
```

> `PUT {base_url}/columns/1/elements/4` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "elements",
    "attributes" : {
      "position": 3,
      "content": {
        ...
      }
    },
    "relations" : {
      "column_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint updates an element.

#### HTTP Request

`PUT {base_url}/elements/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the element to update

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
 | **--Accepts the position field for [positionable objects](#requests-for-positionable-objects)--** |
 | **--Accepts [Content field parameters](#requests-for-content-objects)--** |

#### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/sites/:site_id/elements/:id`
* `PUT {base_url}/site_translations/:site_translation_id/elements/:id`
* `PUT {base_url}/posts/:post_id/elements/:id`
* `PUT {base_url}/sections/:section_id/elements/:id`
* `PUT {base_url}/rows/:row_id/elements/:id`
* `PUT {base_url}/columns/:column_id/elements/:id`

### Delete element

> `DELETE {base_url}/columns/1/elements/4` returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "elements",
    "attributes" : {
      "position": 3,
      "content": {
        ...
      }
    },
    "relations" : {
      "column_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint deletes a specific element.

#### HTTP Request

`DELETE {base_url}/elements/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the element to delete

#### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/sites/:site_id/elements/:id`
* `DELETE {base_url}/site_translations/:site_translation_id/elements/:id`
* `DELETE {base_url}/posts/:post_id/elements/:id`
* `DELETE {base_url}/sections/:section_id/elements/:id`
* `DELETE {base_url}/rows/:row_id/elements/:id`
* `DELETE {base_url}/columns/:column_id/elements/:id`
