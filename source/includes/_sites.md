# Sites

## Get all sites

> `GET {base_url}/partners/1/companies/1/sites/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "company_id": 1,
      "theme_id": 1,
      "name": "Site name 1",
      "languages": "nl,en",
      "main_language": "nl",
      "param_key": "aea00cde61",
      "technical_contact_name": "David",
      "technical_contact_email": "david@getplate.com",
      "status": "creating"
    },
    {
      "id": 2,
      "company_id": 1,
      "theme_id": 123,
      "name": "Site name 2",
      "languages": "nl,en,de",
      "main_language": "nl",
      "param_key": "aec91acccc",
      "technical_contact_name": "Kobus",
      "technical_contact_email": "kobus@getplate.com",
      "status": "ready"
    }
  ]
}
```

This endpoint retrieves all sites in a specific company.

### HTTP Request

`GET {base_url}/companies/:company_id/sites`

### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner to which the sites belong
:company_id | The id of the partner to which the sites belong

### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/partners/:partner_id/sites/` (Gives all sites in a partner)

## Get specific Site

> `GET {base_url}/companies/1/sites/2` returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "theme_id": 123,
    "company_id": 1,
    "name": "Site name 2",
    "languages": "nl,en,de",
    "main_language": "nl",
    "param_key": "aec91acccc",
    "technical_contact_name": "Kobus",
    "technical_contact_email": "kobus@getplate.com",
    "status": "ready"
  }
}

```

This endpoint retrieves a specific site.

### HTTP Request

`GET {base_url}/companies/:company_id/sites/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:company_id | The id of the site to retrieve
:id | The id of the site to retrieve

### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:id`

## Create site

> An example of valid JSON post parameters

```json
{
  "name": "Created site",
  "theme_id": 1,
  "languages": "nl,en",
  "main_language": "en",
  "technical_contact_name": "Pieter",
  "technical_contact_email": "pieter@getplate.com",
  "initial_domain": "my-created-site"
}
```

> `POST {base_url}/companies/3/sites` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "theme_id": 1,
    "company_id": 3,
    "name": "Created site",
    "languages": "nl,en",
    "main_language": "en",
    "param_key": "aec91acccc",
    "technical_contact_name": "Pieter",
    "technical_contact_email": "pieter@getplate.com",
    "status": "creating"
  }
}
```

This endpoint creates a site.

### HTTP Request

`POST {base_url}/companies/:company_id/sites`

### URL Parameters

Parameter | Description
--------- | -----------
:company_id | The id of the company to which the new site belongs

### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
name      | The name of the new site | Required
seo_title | The SEO title of the new site
seo_description | The SEO description of the new site
languages | The languages of the new site | Required. Has to be comma-seperated string of [language codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
main_language | The main language of the new site | Required. Has to be in `languages`
theme_id | The id of the theme that will be installed on the new site. | Has to correspond to an existing theme
technical_contact_name | The name of the technical contact of the new site. |
technical_contact_email | The email of the technical contact of the new site. |
initial_domain | The initial_domain of this site | Required. Has to be an url-safe string.

## Update site

## Delete site
