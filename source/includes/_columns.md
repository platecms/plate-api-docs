# Columns

## Get all columns

> `GET {base_url}/rows/1/columns/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "columns",
      "attributes" : {
        "position": 1
      },
      "relations" : {
        "row_id": 1
      }
    },
    {
      "id": 4,
      "type": "columns",
      "attributes" : {
        "position": 2
      },
      "relations" : {
        "row_id": 1
      }
    }
  ]
}
```

This endpoint retrieves all columns for a specific row

### HTTP Request

`GET {base_url}/rows/:row_id/columns`

### URL Parameters

Parameter | Description
--------- | -----------
:row_id | The id of the rows to which the columns belong
:site_id | The id of the site to which the columns belong
:site_translation_id | The id of the site translation to which the columns belong
:post_id | The id of the post to which the columns belong
:section_id | The id of the section to which the columns belong

### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/columns` (Returns all columns in a site)
* `GET {base_url}/site_translations/:site_translation_id/columns` (Returns all columns in a site translation)
* `GET {base_url}/posts/:post_id/columns` (Returns all columns in a post)
* `GET {base_url}/sections/:section_id/columns` (Returns all columns in a section)

## Get specific column

> `GET {base_url}/rows/1/columns/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "columns",
    "attributes" : {
      "position": 1
    },
    "relations" : {
      "row_id": 1
    }
  }
}
```

This endpoint retrieves a specific column.

### HTTP Request

`GET {base_url}/columns/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:row_id | The id of the rows of the column to retrieve
:id | The id of the column to retrieve
:site_id | The id of the site of the column to retrieve
:site_translation_id | The id of the site of site_translation the column to retrieve
:post_id | The id of the post of the column to retrieve
:section_id | The id of the section of the column to update

### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/columns/:id`
* `GET {base_url}/site_translations/:site_translation_id/columns/:id`
* `GET {base_url}/posts/:post_id/columns/:id`
* `GET {base_url}/sections/:section_id/columns/:id`

## Create column

> An example of valid JSON POST parameters

```json
{
  "data": {    
    "position": 1
  }
}
```

> `POST {base_url}/rows/1/columns` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "columns",
    "attributes" : {
      "position": 1
    },
    "relations" : {
      "row_id": 1
    }
  }
}
```

This endpoint creates a column in a row.

### HTTP Request

`POST {base_url}/rows/:row_id/columns`

### URL Parameters

Parameter | Description
--------- | -----------
:row_id | The id of the rows to which the new column belongs

### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
position | The position (Read more about positions. #TODO FIX LINK TO EXPLANATION OF POSITION) of the new column | Required

## Update column

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "position": 3
  }
}
```

> `PUT {base_url}/rows/1/columns/4` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "columns",
    "attributes" : {
      "position": 3
    },
    "relations" : {
      "row_id": 1
    }
  }
}
```

This endpoint updates a column.

### HTTP Request

`PUT {base_url}/columns/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:row_id | The id of the row of the columns to update
:id | The id of the column to update
:site_id | The id of the site of the column to update
:site_translation_id | The id of the site translation of the column to update
:post_id | The id of the post of the column to update
:section_id | The id of the section of the column to update

### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
position | The new position (Read more about positions. #TODO FIX LINK TO EXPLANATION OF POSITION) of the column | Not null

### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/sites/:site_id/columns/:id`
* `PUT {base_url}/site_translations/:site_translation_id/columns/:id`
* `PUT {base_url}/posts/:post_id/columns/:id`
* `PUT {base_url}/sections/:section_id/columns/:id`
* `PUT {base_url}/rows/:row_id/columns/:id`

## Update column grid

> An example of valid JSON PUT parameters

```json
{
  "data": [
    {
      "id": 1,
      "grid": 9
    },
    {
      "id": 2,
      "grid": 3
    }
  ]
}
```

> `PUT {base_url}/rows/1/columns/` with the above parameters returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "type": "columns",
      "attributes" : {
        "position": 1
      },
      "relations" : {
        "row_id": 1
      }
    },
    {
      "id": 4,
      "type": "columns",
      "attributes" : {
        "position": 2
      },
      "relations" : {
        "row_id": 1
      }
    }
  ]
}
```

This endpoint updates the grid of columns in a row. It requires an array with objects containing the id of a column, and the (new) non-zero grid of that column. The sum of all the specified grids has to be 12, and all column ids should be present.

### HTTP Request

`PUT {base_url}/rows/:row_id/columns/`

### URL Parameters

Parameter | Description
--------- | -----------
:row_id | The id of the row of the columns to update

### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
id | The id of a column |
grid | The grid of a column | At least 1. Not null. The grids should sum up to 12.

## Delete column

> `DELETE {base_url}/rows/1/columns/4` returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "columns",
    "attributes" : {
      "position": 3
    },
    "relations" : {
      "row_id": 1
    }
  }
}
```

This endpoint deletes a specific column.

### HTTP Request

`DELETE {base_url}/columns/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:row_id | The id of the rows of the column to delete
:id | The id of the column to delete
:site_id | The id of the site of the column to delete
:site_translation_id | The id of the site_translation of the column to delete
:post_id | The id of the site of the column to delete
:section_id | The id of the section of the column to update

### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/sites/:site_id/columns/:id`
* `DELETE {base_url}/site_translations/:site_translation_id/columns/:id`
* `DELETE {base_url}/posts/:post_id/columns/:id`
* `DELETE {base_url}/sections/:section_id/columns/:id`
* `DELETE {base_url}/rows/:row_id/columns/:id`
