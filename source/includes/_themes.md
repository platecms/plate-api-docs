## Themes

### Get all themes

> `GET {base_url}/partners/1/themes/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "type": "themes",
      "attributes" : {
        "name": "Theme name 1",
        "languages": "nl,en",
        "main_language": "nl",
        "status": "creating"
      },
      "relations" : {
        "partner_id": 1,
        "site_id": 22
      }
    },
    {
      "id": 2,
      "type": "themes",
      "attributes" : {
        "name": "Theme name 2",
        "languages": "nl",
        "main_language": "nl",
        "status": "unpublished"
      },
      "relations" : {
        "partner_id": 1,
        "site_id": 23
      }
    }
  ]
}
```

This endpoint retrieves all themes for a specific partner

#### HTTP Request

`GET {base_url}/partners/:partner_id/themes`

#### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner to which the themes belong


### Get specific Theme

> `GET {base_url}/partners/1/themes/2` returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "type": "themes",
    "attributes" : {
      "name": "Theme name 2",
      "languages": "nl",
      "main_language": "nl",
      "status": "unpublished"
    },
    "relations" : {
      "partner_id": 1,
      "site_id": 23
    }
  }
}

```

This endpoint retrieves a specific Theme.

#### HTTP Request

`GET {base_url}/partners/:partner_id/themes/:id`

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/theme/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner of the theme to retrieve
:id | The id of the company to retrieve


### Create theme

> An example of valid JSON POST parameters

```json
{
  "data": {    
    "name": "Created theme",
    "copy_from_theme_id": 1,
    "languages": "nl,de",
    "main_language": "de",
    "initial_subdomain": "my-created-theme-example-site"
  }
}
```

> `POST {base_url}/partners/3/themes` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "themes",
    "attributes" : {
      "name": "Created theme",
      "languages": "nl,de",
      "main_language": "de",
      "status": "creating"
    },
    "relations" : {
      "partner_id": 3,
      "site_id": 29
    }
  }
}
```

This endpoint creates a theme.

#### HTTP Request

`POST {base_url}/partners/:partner_id/themes`

#### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner to which the new theme belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
name      | The name of the new theme | Required
languages | The languages of the new theme | Required. Has to be comma-seperated string of [language codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
main_language | The main language of the new theme | Required. Has to be in `languages`
copy_from_theme_id | The id of the theme that will be installed on the new theme. | Has to correspond to an existing theme
initial_subdomain | The subdomain where this theme will be visible | Required. Has to be an url-safe string.


### Update theme

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "name": "New name"
  }
}
```

> `PUT {base_url}/partners/3/themes/5` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "themes",
    "attributes" : {
      "name": "New name",
      "languages": "nl,de",
      "main_language": "de",
      "status": "creating"
    },
    "relations" : {
      "partner_id": 3,
      "site_id": 29
    }
  }
}
```

This endpoint updates a theme.

#### HTTP Request

`PUT {base_url}/themes/:id`


#### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner to which the theme to update belongs
:id | The id of the theme to update

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
name      | The new name of the theme |
languages | The new languages of the theme | Has to be comma-seperated string of [language codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
main_language | The new main language of the theme | Has to be in `languages`


#### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/partners/:partner_id/themes/:id`


### Delete theme

> `DELETE {base_url}/partners/3/themes/5` returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "themes",
    "attributes" : {
      "name": "New name",
      "languages": "nl,de",
      "main_language": "de",
      "status": "creating"
    },
    "relations" : {
      "partner_id": 3,
      "site_id": 29
    }
  }
}
```

This endpoint deletes a specific theme.

#### HTTP Request

`DELETE {base_url}/themes/:id`


#### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner to which the theme to delete belongs
:id | The id of the theme to delete

#### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/partners/:partner_id/themes/:id`
