# Form Messages

Plate allows to receive form messages using the liquid `form` tag. These form messages
can be retrieved using the following endpoints.

The response not only contains the `content`, the fields submitted in a form messages,
but also `sent_from_object` which represent the content object that contains the
form where the form message was sent from, and also the url of the page where the
form was sent from, in `sent_from_url`.

Note that `sent_from_object` might be `null` if the object that contained the form
no longer exists.

## Get all form messages

> `GET {base_url}/sites/1/form_messages/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 2,
      "type": "form_messages",
      "attributes": {
        "content": {
          "form_field_1": "A filled in form field",
          "some_other_form_field": "an@example.email"
        },
        "sent_from_object": {
          "type": "elements",
          "id": 12
        },
        "sent_from_url": "/contact"
      },
      "relations": {
          "site_id": 1
      }
    },
    {
      "id": 3,
      "type": "form_messages",
      "attributes": {
        "content": {
          "form_field_1": "Another fill",
          "some_other_form_field": "my@sneaky.email"
        },
        "sent_from_object": null,
        "sent_from_url": "/contact"
      },
      "relations": {
          "site_id": 1
      }
    }
  ]
}
```

This endpoint retrieves all form messages for a specific site

### HTTP Request

`GET {base_url}/sites/:site_id/form_messages`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the form message belong


## Get specific form message

> `GET {base_url}/form_messages/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "form_messages",
    "attributes": {
      "content": {
        "form_field_1": "A filled in form field",
        "some_other_form_field": "an@example.email"
      },
      "sent_from_object": {
        "type": "elements",
        "id": 12
      },
      "sent_from_url": "/contact"
    },
    "relations": {
        "site_id": 1
    }
  }
}
```

This endpoint retrieves a specific form message.

### HTTP Request

`GET {base_url}/form_messages/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the form message to retrieve
:id | The id of the form message to retrieve

### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/form_messages/:id`

## Delete form message

> `DELETE {base_url/form_messages/2` returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "type": "form_messages",
    "attributes": {
      "content": {
        "form_field_1": "A filled in form field",
        "some_other_form_field": "an@example.email"
      },
      "sent_from_object": {
        "type": "elements",
        "id": 12
      },
      "sent_from_url": "/contact"
    },
    "relations": {
        "site_id": 1
    }
  }
}
```

This endpoint deletes a specific form message.

### HTTP Request

`DELETE {base_url}/form_messages/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the delete form message belongs
:id | The id of the form message to delete

### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/sites/:site_id/form_messages/:id`
