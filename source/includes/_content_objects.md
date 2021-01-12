## Abstract Content Objects

### Get all content_objects

> `GET {base_url}/site_translations/1/content_objects/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "content_objects",
      "attributes" : {
        "position": 1,
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
      "type": "content_objects",
      "attributes" : {
        "position": 2,
        "name": "Another ContentObject name",
          ...
        }
      },
      "relations" : {
        "site_translation_id": 1,
        "content_type_id": 14
      }
    }
  ]
}
```

This endpoint retrieves all content_objects for a specific site_translation

#### HTTP Request

`GET {base_url}/site_translations/:site_translation_id/content_objects`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the content_objects belong
:site_translation_id | The id of the site translation to which the content_objects belong

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/content_objects` (Returns all content_objects in a site)

### Get specific content_object

> `GET {base_url}/site_translations/1/content_objects/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "content_objects",
    "attributes" : {
      "position": 1,
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

This endpoint retrieves a specific content_object.

#### HTTP Request

`GET {base_url}/content_objects/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the content_object to retrieve

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/content_objects/:id`
* `GET {base_url}/site_translations/:site_translation_id/content_objects/:id`

### Create content_object

> An example of valid JSON POST parameters

```json
{
  "data": {
    "content_type_id": 14,
    "position": 1
  }
}
```

> `POST {base_url}/site_translations/1/content_objects` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_objects",
    "attributes" : {
      "position": 1,
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

This endpoint creates an content_object in a site_translation.

#### HTTP Request

`POST {base_url}/site_translations/:site_translation_id/content_objects`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_translation_id | The id of the site_translations to which the new content_object belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
content_type_id | The content type of the new content_object | Required
 | **--Accepts the position field for [positionable objects](#requests-for-positionable-objects)--** |
 | **--Accepts [Content object parameters](#requests-for-content-objects)--** |

### Update content_object

> An example of valid JSON PUT parameters

```json
{
  "data": {
    "position": 3
  }
}
```

> `PUT {base_url}/site_translations/1/content_objects/4` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_objects",
    "attributes" : {
      "position": 3,
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

This endpoint updates an content_object.

#### HTTP Request

`PUT {base_url}/content_objects/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the content_object to update

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
 | **--Accepts the position field for [positionable objects](#requests-for-positionable-objects)--** |
 | **--Accepts [Content field parameters](#requests-for-content-objects)--** |

#### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/sites/:site_id/content_objects/:id`
* `PUT {base_url}/site_translations/:site_translation_id/content_objects/:id`

### Delete content_object

> `DELETE {base_url}/site_translations/1/content_objects/4` returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_objects",
    "attributes" : {
      "position": 3,
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

This endpoint deletes a specific content_object.

#### HTTP Request

`DELETE {base_url}/content_objects/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the content_object to delete

#### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/sites/:site_id/content_objects/:id`
* `DELETE {base_url}/site_translations/:site_translation_id/content_objects/:id`