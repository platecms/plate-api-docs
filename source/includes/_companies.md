# Companies

## Get all companies

> `GET {base_url}/partners/1/companies/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "type": "companies",
      "attributes": {
        "name": "Company Name 1",
        "street_name": "Somestreet",
        "street_no": "5",
        "street_suffix": "a",
        "city": "Ede",
        "zipcode": "6734 AT",
        "country": "Netherlands",
        "phone": "+3123456789",
        "kvk_number": "0123456789",
        "vat_number": "9876543210",
        "invoice_contact_first_name": "Johannes",
        "invoice_contact_last_name": "Pleet",
        "invoice_contact_email": "johannes@getplate.com"
      },
      "relations": {
        "partner_id": 1
      }
    },
    {
      "id": 2,
      "type": "companies",
      "attributes": {
        "name": "Company Name 2",
        "street_name": "Somestreet",
        "street_no": "5",
        "street_suffix": "a",
        "city": "Ede",
        "zipcode": "6734 AT",
        "country": "Netherlands",
        "phone": "+3123456789",
        "kvk_number": "0123456789",
        "vat_number": "9876543210",
        "invoice_contact_first_name": "Johannes",
        "invoice_contact_last_name": "Pleet",
        "invoice_contact_email": "johannes@getplate.com"
      },
      "relations": {
        "partner_id": 1
      }
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
    "type": "companies",
    "attributes": {
      "name": "Company Name 1",
      "street_name": "Somestreet",
      "street_no": "5",
      "street_suffix": "a",
      "city": "Ede",
      "zipcode": "6734 AT",
      "country": "Netherlands",
      "phone": "+3123456789",
      "kvk_number": "0123456789",
      "vat_number": "9876543210",
      "invoice_contact_first_name": "Johannes",
      "invoice_contact_last_name": "Pleet",
      "invoice_contact_email": "johannes@getplate.com"
    },
    "relations": {
      "partner_id": 1
    }
  }
}

```

This endpoint retrieves a specific company.

### HTTP Request

`GET {base_url}/companies/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the company to retrieve

### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/partners/:partner_id/companies/:id`

## Create company

> An example of valid JSON POST parameters

```json
{
  "data": {    
    "name": "Created Company Name 1",
  }
}
```

> `POST {base_url}/partners/1/companies` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "type": "companies",
    "attributes": {
      "name": "Created Company Name 1",
      "street_name": "",
      "street_no": "",
      "street_suffix": "",
      "city": "",
      "zipcode": "",
      "country": "",
      "phone": "",
      "kvk_number": "",
      "vat_number": "",
      "invoice_contact_first_name": "",
      "invoice_contact_last_name": "",
      "invoice_contact_email": ""
    },
    "relations": {
      "partner_id": 1
    }
  }
}
```

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
name | The name for the new company
street_name | The street name for the new company
street_no | The street number for the new company
street_suffix | The street suffix for the new company
city | The city for the new company
zipcode | The zipcode for the new company
country | The country for the new company
phone | The phone number for this company
kvk_number | The [kvk number](https://www.kvk.nl/advies-en-informatie/bedrijf-starten-of-overnemen/kvk-nummer-alles-wat-je-moet-weten/) for the new company
vat_number | The [vat number](https://en.wikipedia.org/wiki/VAT_identification_number) for the new company
invoice_contact_first_name | The first name for the invoice contact for the new company
invoice_contact_last_name | The last name for the invoice contact for the new company
invoice_contact_email | The email address for the invoice contact for the new company

### Constraints
This endpoint has the following constraints:

* A parameter `name` with length > 1 should be given

## Update company

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "name": "New Company name"
  }
}
```

> `PUT {base_url}/partners/1/companies/1` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "type": "companies",
    "attributes": {
      "name": "New Company name",
      "street_name": "Somestreet",
      "street_no": "5",
      "street_suffix": "a",
      "city": "Ede",
      "zipcode": "6734 AT",
      "country": "Netherlands",
      "phone": "+3123456789",
      "kvk_number": "0123456789",
      "vat_number": "9876543210",
      "invoice_contact_first_name": "Johannes",
      "invoice_contact_last_name": "Pleet",
      "invoice_contact_email": "johannes@getplate.com"
    },
    "relations": {
      "partner_id": 1
    }
  }
}
```

This endpoint updates a specific company.

### HTTP Request

`PUT {base_url}/companies/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:partner_id | The id of the partner to which the updated company belongs
:id | The id of the company to update

### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
name | The new name for this company | Required.
street_name | The new street name for this company | Required.
street_no | The new street number for this company | Required.
street_suffix | The new street suffix for this company
city | The new city for this company | Required.
zipcode | The new zipcode for this company | Required.
country | The new country for this company | Required.
phone | The new phone number for this company
kvk_number | The new [kvk number](https://www.kvk.nl/advies-en-informatie/bedrijf-starten-of-overnemen/kvk-nummer-alles-wat-je-moet-weten/) for this company | Required.
vat_number | The new [vat number](https://en.wikipedia.org/wiki/VAT_identification_number) for this company | Required.
invoice_contact_first_name | The new first name for the invoice contact for this company | Required.
invoice_contact_last_name | The new last name for the invoice contact for this company | Required.
invoice_contact_email | The new email address for the invoice contact for this company | Required.

### Constraints
This endpoint has the following constraints:

* The updated company needs to have a value for all required PUT parameters. So either a
value was already set, or a new value has to be set through this request.

### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/partners/:partner_id/companies/:id`


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

`DELETE {base_url}/companies/:id`

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

* `DELETE {base_url}/partners/:partner_id/companies/:id`
