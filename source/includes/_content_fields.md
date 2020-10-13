## Content Field

### Get all content fields

> `GET {base_url}/sites/1/content_fields/` returns JSON structured like this:
```json
{
  "data": [
    {
      "id": 3,
      "type": "content_fields",
      "attributes" : {
        "title": "Selected images",
        "name": "selected_images",
        "field_type": "array",
        "settings": { "array_field_kind": "attachments" },
        "validations": {
          "required": {"enabled": true},
          "length": {"enabled": true, "min": 2, "max": 10, "range_handler": "between"},
        }
      },
      "relations" : {
        "site_id": 1,
        "content_type_id": 10
      }
    },
    {
      "id": 4,
      "type": "content_fields",
      "attributes" : {
        "title": "Authors",
        "name": "authors",
        "field_type": "reference",
        "settings": {
          "referenced_content_type_kind_id": 9876,
          "referenced_title_field": "name",
          "context": "global"
        },
        "validations": {
          "required": {"enabled": false},
          "length": {"enabled": false},
        }
      },
      "relations" : {
        "site_id": 1,
        "content_type_id": 10
      }
    }
  ]
}
```

This endpoint retrieves all Content Fields for a specific site

#### HTTP Request

`GET {base_url}/sites/:site_id/content_fields`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the content fields belong

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/content_types/:content_type_id/content_fields` (Gives all Content Fields for a certain Content Type)


### Get specific Content Field

> `GET {base_url}/sites/1/content_fields/4` returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_fields",
    "attributes" : {
      "title": "Authors",
      "name": "authors",
      "field_type": "reference",
      "settings": {
        "referenced_content_type_kind_id": 9876,
        "referenced_title_field": "name",
        "context": "global"
      },
      "validations": {
        "required": {"enabled": false},
        "length": {"enabled": false},
      }
    },
    "relations" : {
      "site_id": 1,
      "content_type_id": 10
    }
  }
}
```

This endpoint retrieves information about a specific Content Field.

#### HTTP Request

`GET {base_url}/sites/:site_id/content_fields/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the Content Field to retrieve
:id | The id of the Content Field to retrieve
:content_type_id | The id of the Content Type to which the Content Field belongs (optional)

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/content_types/:content_type_id/content_fields/:id`


### Create Content Field

> An example of valid JSON POST parameters

```json
{
  "data": {
    "title": "Authors",
    "name": "authors",
    "field_type": "reference",
    "settings": {
      "referenced_content_type_kind_id": 9876,
      "referenced_title_field": "name",
      "context": "global"
    },
    "validations": {
      "required": {"enabled": false},
      "length": {"enabled": true, "min": 2, "max": 10, "range_handler": "between"},
    }
  }
}
```

> `POST {base_url}/content_types/123/content_fields` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_fields",
    "attributes" : {
      "title": "Authors",
      "name": "authors",
      "field_type": "reference",
      "settings": {
        "referenced_content_type_kind_id": 9876,
        "referenced_title_field": "name",
        "context": "global"
      },
      "validations": {
        "required": {"enabled": false},
        "length": {"enabled": true, "min": 2, "max": 10, "range_handler": "between"},
      }
    },
    "relations" : {
      "site_id": 1,
      "content_type_id": 10
    }
  }
}
```

#### HTTP Request

`POST {base_url}/content_types/:content_type_id/content_fields`

#### URL Parameters

Parameter | Description
--------- | -----------
:content_type_id | The id of the Content Type to which the new Content Field belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
name      | The identifying name of the new Content Field | Not null.
title      | The title of the new Content Field | Not null.
field_type      | The identifying plural name of the new Content Field | Must be one of available field_types
settings      | The field settings for the new Content Field | Must be settings JSON based on specific field_type
validations | Validation settings for Content Field | Must be json based on specific field_type

The following field_types are available (along with corresponding settings and validations json keys)

##### String

**Settings:**
None

**Validations:**
required: [enabled:boolean]
length: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string]
match: [enabled:boolean, regex_body:string, custom_error:string]

##### Text

**Settings:**
[editor_kind:"html|wysiwyg|none"]

**Validations:**
required: [enabled:boolean]
length: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string]

##### Reference

**Settings:**
[referenced_content_type_kind_id:integer, referenced_title_field:string, context:"local|global"]

**Validations:**
required: [enabled:boolean]
length: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string]

##### Choice

**Settings:**
[choice_field_kind:"radio|checkbox|dropdown|toggle", predefined_values:array]

**Validations:**
required: [enabled:boolean]
length: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string]

##### Array

**Settings:**
[array_field_kind:"strings|attachments"]

**Validations:**
required: [enabled:boolean]
length: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string]

##### Media

**Settings:**
None

**Validations:**
required: [enabled:boolean]
file_types: [enabled:boolean, custom_error:string, allowed_file_types:array]
filesize: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string, min_filesize_unit:"mb|kb", max_filesize_unit:"mb|kb"]

##### Datetime

**Settings:**
[datetime_field_kind:array]

<aside class="info">
The possible values for data_time_field_kind are: [date], [time] and [date, time]
</aside>

**Validations:**
required: [enabled:boolean]


### Update Content Field

> An example of valid JSON PUT parameters

```json
{
  "data": {
    "title": "Authors",
    "name": "authors",
    "field_type": "reference",
    "settings": {
      "referenced_content_type_kind_id": 9876,
      "referenced_title_field": "name",
      "context": "global"
    },
    "validations": {
      "required": {"enabled": false},
      "length": {"enabled": true, "min": 2, "max": 10, "range_handler": "between"},
    }
  }
}
```

> `PUT {base_url}/content_types/123/content_fields/4` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_fields",
    "attributes" : {
      "title": "Authors",
      "name": "authors",
      "field_type": "reference",
      "settings": {
        "referenced_content_type_kind_id": 9876,
        "referenced_title_field": "name",
        "context": "global"
      },
      "validations": {
        "required": {"enabled": false},
        "length": {"enabled": true, "min": 2, "max": 10, "range_handler": "between"},
      }
    },
    "relations" : {
      "site_id": 1,
      "content_type_id": 10
    }
  }
}
```

This endpoint updates a Content Field.

#### HTTP Request

`PUT {base_url}/content_types/:content_type_id/content_fields/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:content_type_id | The id of the Content Type of the Content Field to retrieve
:id | The id of the Content Field to retrieve

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
name      | The identifying name of the new Content Field | Not null.
title      | The title of the new Content Field | Not null.
field_type      | The identifying plural name of the new Content Field | Must be one of available field_types
settings      | The field settings for the new Content Field | Must be settings JSON based on specific field_type
validations | Validation settings for Content Field | Must be json based on specific field_type

The following field_types are available (along with corresponding settings and validations json keys)

##### String

**Settings:**
None

**Validations:**
required: [enabled:boolean]
length: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string]
match: [enabled:boolean, regex_body:string, custom_error:string]

##### Text

**Settings:**
[editor_kind:"html|wysiwyg|none"]

**Validations:**
required: [enabled:boolean]
length: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string]

##### Reference

**Settings:**
[referenced_content_type_kind_id:integer, referenced_title_field:string, context:"local|global"]

**Validations:**
required: [enabled:boolean]
length: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string]

##### Choice

**Settings:**
[choice_field_kind:"radio|checkbox|dropdown|toggle", predefined_values:array]

**Validations:**
required: [enabled:boolean]
length: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string]

##### Array

**Settings:**
[array_field_kind:"strings|attachments"]

**Validations:**
required: [enabled:boolean]
length: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string]

##### Media

**Settings:**
None

**Validations:**
required: [enabled:boolean]
file_types: [enabled:boolean, custom_error:string, allowed_file_types:array]
filesize: [enabled:boolean, min:integer, max:integer, range_handler:string, custom_error:string, min_filesize_unit:"mb|kb", max_filesize_unit:"mb|kb"]

##### Datetime

**Settings:**
[datetime_field_kind:array]

<aside class="info">
The possible values for data_time_field_kind are: [date], [time] and [date, time]
</aside>

**Validations:**
required: [enabled:boolean]


### Delete Content Field

> `DELETE {base_url}/sites/1/content_fields/4` returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "content_fields",
    "attributes" : {
      "title": "Authors",
      "name": "authors",
      "field_type": "reference",
      "settings": {
        "referenced_content_type_kind_id": 9876,
        "referenced_title_field": "name",
        "context": "global"
      },
      "validations": {
        "required": {"enabled": false},
        "length": {"enabled": false},
      }
    },
    "relations" : {
      "site_id": 1,
      "content_type_id": 10
    }
  }
}
```

This endpoint deletes a specific Content Field.

#### HTTP Request

`DELETE {base_url}/sites/:site_id/content_fields/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the Content Field to retrieve
:id | The id of the Content Field to retrieve
:content_type_id | The id of the Content Type to which the Content Field belongs (optional)

#### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/content_types/:content_type_id/content_fields/:id`
