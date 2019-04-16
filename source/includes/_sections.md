## Sections

### Get all sections

> `GET {base_url}/posts/1/sections/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "sections",
      "attributes" : {
        "position": 1,
        "name": "A Section name",
        "content": {
          ...
        }
      },
      "relations" : {
        "post_id": 1,
        "content_type_id": 14
      }
    },
    {
      "id": 4,
      "type": "sections",
      "attributes" : {
        "position": 2,
        "name": "Another Section name",
        "content": {
          ...
        }
      },
      "relations" : {
        "post_id": 1,
        "content_type_id": 14
      }
    }
  ]
}
```

This endpoint retrieves all sections for a specific post

#### HTTP Request

`GET {base_url}/posts/:post_id/sections`

#### URL Parameters

Parameter | Description
--------- | -----------
:post_id | The id of the posts to which the sections belong
:site_id | The id of the site to which the sections belong
:site_translation_id | The id of the site translation to which the sections belong

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/sections` (Returns all sections in a site)
* `GET {base_url}/site_translations/:site_translation_id/sections` (Returns all sections in a site translation)

### Get specific section

> `GET {base_url}/posts/1/sections/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "sections",
    "attributes" : {
      "position": 1,
      "name": "A Section name",
      "content": {
        ...
      }
    },
    "relations" : {
      "post_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint retrieves a specific section.

#### HTTP Request

`GET {base_url}/sections/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:post_id | The id of the posts of the section to retrieve
:id | The id of the section to retrieve
:site_id | The id of the site of the section to retrieve
:site_translation_id | The id of the site of site_translation the section to retrieve

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/sections/:id`
* `GET {base_url}/site_translations/:site_translation_id/sections/:id`
* `GET {base_url}/posts/:post_id/sections/:id`

### Create section

> An example of valid JSON POST parameters

```json
{
  "data": {    
    "content_type_id": 14,
    "name": "Created Section",
    "position": 1
  }
}
```

> `POST {base_url}/posts/1/sections` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "sections",
    "attributes" : {
      "position": 1,
      "name": "Created Section",
      "content": {
        ...
      }
    },
    "relations" : {
      "post_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint creates a section in a post.

#### HTTP Request

`POST {base_url}/posts/:post_id/sections`

#### URL Parameters

Parameter | Description
--------- | -----------
:post_id | The id of the posts to which the new section belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
content_type_id | The content type of the new section | Required
name     | The name of the new section | Required
 | **--Accepts the position field for [positionable objects](#requests-for-positionable-objects)--** |
 | **--Accepts [Content field parameters](#requests-for-content-objects)--** |

### Update section

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "name": "Updated Section Name",
    "position": 3
  }
}
```

> `PUT {base_url}/posts/1/sections/4` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "sections",
    "attributes" : {
      "position": 3,
      "name": "Updated Section Name",
      "content": {
        ...
      }
    },
    "relations" : {
      "post_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint updates a section.

#### HTTP Request

`PUT {base_url}/sections/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:post_id | The id of the posts of the section to update
:id | The id of the section to update
:site_id | The id of the site of the section to update
:site_translation_id | The id of the site translation of the section to update

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
name     | The new name of the section | Not null
 | **--Accepts the position field for [positionable objects](#requests-for-positionable-objects)--** |
 | **--Accepts [Content field parameters](#requests-for-content-objects)--** |

#### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/sites/:site_id/sections/:id`
* `PUT {base_url}/site_translations/:site_translation_id/sections/:id`
* `PUT {base_url}/posts/:post_id/sections/:id`

### Delete section

> `DELETE {base_url}/posts/1/sections/4` returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "sections",
    "attributes" : {
      "position": 3,
      "name": "Updated Section Name",
      "content": {
        ...
      }
    },
    "relations" : {
      "post_id": 1,
      "content_type_id": 14
    }
  }
}
```

This endpoint deletes a specific section.

#### HTTP Request

`DELETE {base_url}/sections/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:post_id | The id of the posts of the section to delete
:id | The id of the section to delete
:site_id | The id of the site of the section to delete
:site_translation_id | The id of the site_translation of the section to delete

#### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/sites/:site_id/sections/:id`
* `DELETE {base_url}/site_translations/:site_translation_id/sections/:id`
* `DELETE {base_url}/posts/:post_id/sections/:id`
