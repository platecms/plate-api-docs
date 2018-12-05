# Companies

## Get all companies

> `GET {base_url}/partners/1/companies/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Company Name 1",
      "partner_id": 1
    },
    {
      "id": 2,
      "name": "Company Name 2",
      "partner_id": 1
    }
  ]
}
```

This endpoint retrieves all companies in a specific partner.

### HTTP Request

`GET {base_url}/partners/:partner_id/companies`

### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner to which the companies belong


## Get specific Company

> `GET {base_url}/partners/1/companies/1` returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "name": "Company 1",
    "partner_id": 1,
    "sites": [
      {
        "id": 1,
        "name": "Site Name 1",
      },
      {
        "id": 2,
        "name": "Site Name 2",
      }
    ]
  }
}

```

This endpoint retrieves a specific company and the id's of the sites of this company.

### HTTP Request

`GET {base_url}/partners/:partner_id/companies/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the company to retrieve

### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/companies/:id`

## Create company

> An example of valid JSON post parameters

```json
{
  "name": "Created Company Name 1",
}
```

> `POST {base_url}/partners/1/companies` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "name": "Created Partner Name 1",
    "partner_id": 1,
    "sites": []
  }
}
```
> Note that the `sites` attribute of a newly created company is always empty.

This endpoint creates a company.

### HTTP Request

`POST {base_url}/partners/:partner_id/companies`

### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner to which the new company belongs

### POST Parameters

Parameter | Description
--------- | -----------
name | The name of the partner to create

### Constraints
This endpoint has the following constraints:

* A parameter `name` with length > 1 should be given

## Update company

> An example of valid JSON post parameters

```json
{
  "name": "New Company name"
}
```

> `PUT {base_url}/partners/1/companies/1` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "name": "New Company name",
    "partner_id": 1,
    "sites": [
      {
        "id": 1,
        "name": "Site Name 1",
      },
      {
        "id": 2,
        "name": "Site Name 2",
      }
    ]
  }
}
```

This endpoint updates a specific company.

### HTTP Request

`PUT {base_url}/partners/:partner_id/companies/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner to which the updated company belongs
:id | The id of the company to update

### PUT Parameters

Parameter | Description
--------- | -----------
name | The new name for this company

### Constraints
This endpoint has the following constraints:

* If the parameter `name` is given, it should have length > 1

### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/companies/:id`


## Delete company

> `DELETE {base_url}/partners/1/companies/1` returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "name": "Company Name 1"
  }
}
```

This endpoint deletes a specific company.

### HTTP Request

`DELETE {base_url}/partners/:partner_id/companies/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner to which the delete company belongs
:id | The id of the company to delete

### Constraints
This endpoint has the following constraints:

* There should be no sites in the company with id `:id`

### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/companies/:id`
