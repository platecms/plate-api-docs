## Rows

### Get all rows

> `GET {base_url}/sections/1/rows/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "rows",
      "attributes" : {
        "position": 1
      },
      "relations" : {
        "section_id": 1
      }
    },
    {
      "id": 4,
      "type": "rows",
      "attributes" : {
        "position": 2
      },
      "relations" : {
        "section_id": 1
      }
    }
  ]
}
```

This endpoint retrieves all rows for a specific section

#### HTTP Request

`GET {base_url}/sections/:section_id/rows`

#### URL Parameters

Parameter | Description
--------- | -----------
:section_id | The id of the sections to which the rows belong
:site_id | The id of the site to which the rows belong
:site_translation_id | The id of the site translation to which the rows belong
:post_id | The id of the post to which the rows belong

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/rows` (Returns all rows in a site)
* `GET {base_url}/site_translations/:site_translation_id/rows` (Returns all rows in a site translation)
* `GET {base_url}/posts/:post_id/rows` (Returns all rows in a post)

### Get specific row

> `GET {base_url}/sections/1/rows/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "rows",
    "attributes" : {
      "position": 1
    },
    "relations" : {
      "section_id": 1
    }
  }
}
```

This endpoint retrieves a specific row.

#### HTTP Request

`GET {base_url}/rows/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:section_id | The id of the sections of the row to retrieve
:id | The id of the row to retrieve
:site_id | The id of the site of the row to retrieve
:site_translation_id | The id of the site of site_translation the row to retrieve
:post_id | The id of the post of the row to retrieve

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/rows/:id`
* `GET {base_url}/site_translations/:site_translation_id/rows/:id`
* `GET {base_url}/posts/:post_id/rows/:id`
* `GET {base_url}/sections/:section_id/rows/:id`

### Create row

> An example of valid JSON POST parameters

```json
{
  "data": {    
    "position": 1
  }
}
```

> `POST {base_url}/sections/1/rows` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "rows",
    "attributes" : {
      "position": 1
    },
    "relations" : {
      "section_id": 1
    }
  }
}
```

This endpoint creates a row in a section.

#### HTTP Request

`POST {base_url}/sections/:section_id/rows`

#### URL Parameters

Parameter | Description
--------- | -----------
:section_id | The id of the sections to which the new row belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
 | **--Accepts the position field for [positionable objects](#requests-for-positionable-objects)--** |

### Update row

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "position": 3
  }
}
```

> `PUT {base_url}/sections/1/rows/4` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "rows",
    "attributes" : {
      "position": 3
    },
    "relations" : {
      "section_id": 1
    }
  }
}
```

This endpoint updates a row.

#### HTTP Request

`PUT {base_url}/rows/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:section_id | The id of the sections of the row to update
:id | The id of the row to update
:site_id | The id of the site of the row to update
:site_translation_id | The id of the site translation of the row to update
:post_id | The id of the post of the row to update

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
 | **--Accepts the position field for [positionable objects](#requests-for-positionable-objects)--** |

#### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/sites/:site_id/rows/:id`
* `PUT {base_url}/site_translations/:site_translation_id/rows/:id`
* `PUT {base_url}/posts/:post_id/rows/:id`
* `PUT {base_url}/sections/:section_id/rows/:id`

### Delete row

> `DELETE {base_url}/sections/1/rows/4` returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "rows",
    "attributes" : {
      "position": 3
    },
    "relations" : {
      "section_id": 1
    }
  }
}
```

This endpoint deletes a specific row.

#### HTTP Request

`DELETE {base_url}/rows/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:section_id | The id of the sections of the row to delete
:id | The id of the row to delete
:site_id | The id of the site of the row to delete
:site_translation_id | The id of the site_translation of the row to delete
:post_id | The id of the site of the row to delete

#### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/sites/:site_id/rows/:id`
* `DELETE {base_url}/site_translations/:site_translation_id/rows/:id`
* `DELETE {base_url}/posts/:post_id/rows/:id`
* `DELETE {base_url}/sections/:section_id/rows/:id`
