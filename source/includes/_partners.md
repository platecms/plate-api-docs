# Partners

## Get specific partner

> `GET {base_url}/partners/1` returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "name": "Partner Name 1",
    "companies": [
      {
        "id": 1,
        "name": "Company Name 1",
      },
      {
        "id": 2,
        "name": "Company Name 2",
      }
    ]
  }
}

```

This endpoint retrieves a specific partner and the companies that are in this
partner.

<aside class="warning">Only the <code>id</code> and <code>name</code> attributes
of the companies that are in this partner are shown. Use the
<a href="#get-all-companies">Get all companies</a>
or <a href="#get-specific-company">Get specific company</a> endpoint to get detailed information about the companies
</aside>

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
