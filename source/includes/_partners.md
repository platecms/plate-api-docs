# Partners

## Get specific partner

> `GET {base_url}/partners/1` returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "name": "Partner Name 1"
  }
}

```

This endpoint retrieves a specific partner.

### HTTP Request

`GET {base_url}/partners/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the partner to retrieve

## Update partner

> An example of valid JSON post parameters

```json
{
  "name": "New Partner name"
}
```

> `PUT {base_url}/partners/1` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "name": "New Partner name"
  }
}
```

This endpoint updates a specific partner.

### HTTP Request

`PUT {base_url}/partners/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:id | The id of the partner to update

### PUT Parameters

Parameter | Description
--------- | -----------
name | Thenew name for this partner

### Constraints
This endpoint has the following constraints:

* If the parameter `name` is given, it should have length > 1
