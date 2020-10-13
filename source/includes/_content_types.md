## Content Type

### Get all Content Types

> `GET {base_url}/sites/1/content_types/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "content_types",
      "attributes" : {
        "name": "menu_item",
        "title": "Menu Item",
        "plural_name": "menu_items",
        "plural_title": "Menu Items",
        "icon_name": "icon",
        "content_type_kinds": [
          {"id": "55", "type": "abstract_content_type"},
        ]
      },
      "relations" : {
        "site_id": 1
      }
    },
    {
      "id": 4,
      "type": "content_types",
      "attributes" : {
        "name": "review",
        "title": "Review",
        "plural_name": "reviews",
        "plural_title": "Reviews",
        "icon_name": "review_icon",
        "content_type_kinds": [
          {"id": "56", "type": "abstract_content_type"},
          {
            "id": "57",
            "type": "post_type",
            "settings": {
              "en": { "slug": "reviews", "index_post_id": 9999 },
              "nl": { "slug": "beoordelingen", "index_post_id": 9998 }
            }
          },
        ]
      },
      "relations" : {
        "site_id": 1
      }
    }
  ]
}
```

This endpoint retrieves all content_types for a specific site

#### HTTP Request

`GET {base_url}/sites/:site_id/content_types`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the content types belong


### Get specific Content Type

> `GET {base_url}/sites/1/content_types/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_types",
    "attributes" : {
      "name": "review",
      "title": "Review",
      "plural_name": "reviews",
      "plural_title": "Reviews",
      "icon_name": "review_icon",
      "content_type_kinds": [
        {"id": "56", "type": "abstract_content_type"},
        {
          "id": "57",
          "type": "post_type",
          "settings": {
            "en": { "slug": "reviews", "index_post_id": 9999 },
            "nl": { "slug": "beoordelingen", "index_post_id": 9998 }
          }
        },
      ]
    },
    "relations" : {
      "site_id": 1
    }
  }
}
```

This endpoint retrieves information about a specific content type. It also contains the content type different content type kinds, which can be one or multiple of these:
- abstract_content_type
- post_type (contains extra localization settings)
- section_type
- element_type
- tray_type
- authentication_type

#### HTTP Request

`GET {base_url}/sites/1/content_types/3`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the content_type to retrieve
:id | The id of the content_type to retrieve

### Create Content Type

> An example of valid JSON POST parameters

```json
{
  "data": {
    "name": "review",
    "title": "Review",
    "plural_name": "reviews",
    "plural_title": "Reviews",
    "icon_name": "review_icon",
    "content_type_kinds": [
      {"type": "abstract_content_type"},
      {
        "type": "post_type",
        "settings": {
          "en": { "slug": "reviews" },
          "nl": { "slug": "beoordelingen" }
        }
      },
    ]
  }
}
```

> `POST {base_url}/sites/1/content_types` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_types",
    "attributes" : {
      "name": "review",
      "title": "Review",
      "plural_name": "reviews",
      "plural_title": "Reviews",
      "icon_name": "review_icon",
      "content_type_kinds": [
        {"id": "56", "type": "abstract_content_type"},
        {
          "id": "57",
          "type": "post_type",
          "settings": {
            "en": { "slug": "reviews", "index_post_id": 9999 },
            "nl": { "slug": "beoordelingen", "index_post_id": 9998 }
          }
        },
      ]
    },
    "relations" : {
      "site_id": 1
    }
  }
}
```

#### HTTP Request

`POST {base_url}/sites/:site_id/content_types`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the new Content Type belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
name      | The identifying name of the new Content Type | Not null.
title      | The title of the new Content Type | Not null.
plural_name      | The identifying plural name of the new Content Type | Not null.
plural_title      | The plural title of the new Content Type | Not null.
icon_name | The Icon name for the new Content Type
content_type_kinds | Array of JSON objects to create content_type kinds for the Content Type


### Update Content Type

> An example of valid JSON PUT parameters

```json
{
  "data": {
    "name": "review",
    "title": "Beoordeling",
    "plural_name": "reviews",
    "plural_title": "Beoordelingen",
    "icon_name": "review_icon",
    "content_type_kinds": [
      {"type": "abstract_content_type"},
      {
        "type": "post_type",
        "settings": {
          "en": { "slug": "reviews" },
          "nl": { "slug": "beoordelingen" }
        }
      },
    ]
  }
}
```

> `PUT {base_url}/sites/1/content_types/5` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_types",
    "attributes" : {
      "name": "review",
      "title": "Beoordeling",
      "plural_name": "reviews",
      "plural_title": "Beoordelingen",
      "icon_name": "review_icon",
      "content_type_kinds": [
        {"id": "56", "type": "abstract_content_type"},
        {
          "id": "57",
          "type": "post_type",
          "settings": {
            "en": { "slug": "reviews", "index_post_id": 9999 },
            "nl": { "slug": "beoordelingen", "index_post_id": 9998 }
          }
        },
      ]
    },
    "relations" : {
      "site_id": 1
    }
  }
}
```

This endpoint updates a Content Type.

#### HTTP Request

`PUT {base_url}/sites/:site_id/content_types/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the Content Type to retrieve
:id | The id of the Content Type to retrieve

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
name      | The identifying name of the new Content Type | Not null.
title      | The title of the new Content Type | Not null.
plural_name      | The identifying plural name of the new Content Type | Not null.
plural_title      | The plural title of the new Content Type | Not null.
icon_name | The Icon name for the new Content Type
content_type_kinds | Array of JSON objects to create content_type kinds for the Content Type | If present, needs to represent all kinds

<aside class="warning">
Be aware that the `content_type_kinds` parameter is not mandatory in the update action. However, when it is present, it needs to represent *all content type kinds* currently inside the content_type. If one or more are omitted, the api call will delete these.
</aside>


### Delete Content Type

> `DELETE {base_url}/sites/1/content_types/5` returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_types",
    "attributes" : {
      "name": "review",
      "title": "Beoordeling",
      "plural_name": "reviews",
      "plural_title": "Beoordelingen",
      "icon_name": "review_icon",
      "content_type_kinds": [
        {"id": "56", "type": "abstract_content_type"},
        {
          "id": "57",
          "type": "post_type",
          "settings": {
            "en": { "slug": "reviews", "index_post_id": 9999 },
            "nl": { "slug": "beoordelingen", "index_post_id": 9998 }
          }
        },
      ]
    },
    "relations" : {
      "site_id": 1
    }
  }
}
```

This endpoint deletes a specific Content Type.

#### HTTP Request

`DELETE {base_url}/sites/:site_id/content_types/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the Content Type to retrieve
:id | The id of the Content Type to retrieve
