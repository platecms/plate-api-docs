<!-- THIS IS DOCUMENTATION FOR PARTNERS WHICH IS TEMPORARY HIDDEN FROM THE DOCS  -->
## Get all partners

> `GET {base_url}/partners` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Partner Name 1"
    },
    {
      "id": 2,
      "name": "Partner Name 2"
    }
  ]
}
```

This endpoint retrieves all partners accessible by the provided API key.

### HTTP Request

`GET {base_url}/partners`


## Create partner

> An example of valid JSON post parameters

```json
{
  "name": "Created Partner Name 1"
}
```

> `POST {base_url}/partners/` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "name": "Created Partner Name 1"
  }
}
```

This endpoint creates a specific partner.

### HTTP Request

`POST {base_url}/partners/`

### POST Parameters

Parameter | Description
--------- | -----------
name | The name of the partner to create

### Constraints
This endpoint has the following constraints:

* A parameter `name` with length > 1 should be given


## Delete partner

> `DELETE {base_url}/partners/:id` returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "name": "Partner Name 1"
  }
}
```

This endpoint deletes a specific partner.

### HTTP Request

`DELETE {base_url}/partners/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the partner to delete

### Constraints
This endpoint has the following constraints:

* There should be no companies in the partner with id `:id`
