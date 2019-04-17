## Partners

### Get specific partner

> `GET {base_url}/partners/1` returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "type": "partners",
    "attributes": {
      "name": "Partner Name 1"
    },
    "relations": {}
  }
}

```

This endpoint retrieves a specific partner.

#### HTTP Request

`GET {base_url}/partners/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the partner to retrieve

### Update partner

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "name": "New Partner name"
  }
}
```

> `PUT {base_url}/partners/1` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "type": "partners",
    "attributes": {
      "name": "New Partner name"
    },
    "relations": {}
  }
}
```

This endpoint updates a specific partner.

#### HTTP Request

`PUT {base_url}/partners/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the partner to update

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
name | The new name for this partner | String. Not null
