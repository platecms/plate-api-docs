# Site Translations

## Get all site translations

> `GET {base_url}/sites/1/site_translations/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "site_translations",
      "attributes" : {
        "language": "nl",
        "content": {
          "content_field_1": {
            "value": [1032, 12, 1],
            "type": "reference",
            "subtype": "element",
            "content_field_id": 82
          },
          "content_field_2": {
            "value": "Go girl",
            "type": "text",
            "content_field_id": 83
          }
        }
      },
      "relations" : {
        "site_id": 1,
        "content_type_id": 16
      }
    },
    {
      "id": 2,
      "type": "site_translations",
      "attributes" : {
        "language": "en",
        "content": {
          "content_field_1": {
            "value": [1032, 123, 456],
            "type": "reference",
            "subtype": "element",
            "content_field_id": 82
          },
          "content_field_2": {
            "value": "A little text",
            "type": "text",
            "content_field_id": 83
          }
        }
      },
      "relations" : {
        "site_id": 1,
        "content_type_id": 16
      }
    }
  ]
}
```

This endpoint retrieves all site translations for a specific site

### HTTP Request

`GET {base_url}/sites/:site_id/site_translations`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the site_translations belong


## Get specific site translations

> `GET {base_url}/sites/1/site_translations/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "site_translations",
    "attributes" : {
      "language": "nl",
      "content": {
        "content_field_1": {
          "value": [1032, 12, 1],
          "type": "reference",
          "subtype": "element",
          "content_field_id": 82
        },
        "content_field_2": {
          "value": "Go girl",
          "type": "text",
          "content_field_id": 83
        }
      }
    },
    "relations" : {
      "site_id": 1,
      "content_type_id": 16
    }
  }
}
```

This endpoint retrieves a specific site translation.

### HTTP Request

`GET {base_url}/site_translations/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the site translation to retrieve
:id | The id of the site translation to retrieve

### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/site_translations/:id`

## Update site translation

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "content_field_1": [
      {
        "id": 22,
      },
      {
        "id": 24,
        "reference_content_field_1": "Updated text for existing content_reference"
      },
      {
        "reference_content_field_1": "I am a referenced element",
        "reference_content_field_2": "Some text",

      }
    ],
    "content_field_2": "New text"
  }
}
```

> `PUT {base_url}/sites/1/site_translations/3` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "site_translations",
    "attributes" : {
      "language": "nl",
      "content": {
        "content_field_1": {
          "value": [22, 23, 1033],
          "type": "reference",
          "subtype": "element",
          "content_field_id": 82
        },
        "content_field_2": {
          "value": "New text",
          "type": "text",
          "content_field_id": 83
        }
      }
    },
    "relations" : {
      "site_id": 1,
      "content_type_id": 16
    }
  }
}
```

This endpoint updates a site translation.

### HTTP Request

`PUT {base_url}/site_translations/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the site translation to retrieve
:id | The id of the site translation to retrieve

### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
 | **--[Content field parameters](#Content field parameters) --**#TODO Fix link to explanation of content field parameters|

### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/sites/:site_id/site_translations/:id`
