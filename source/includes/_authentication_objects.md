## Authentication Objects

### Get all Authentication Objects

> `GET {base_url}/site/1/authentication_objects` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "authentication_objects",
      "attributes" : {
        "email": "test@email.com",
        "reset_password_sent_at": null,
        "confirmed_at": "2020-10-13 12:49:39 +0000",
        "confirmation_sent_at": "2020-10-13 12:49:39 +0000",
        "unconfirmed_email": null,
        "content": {
          ...
        }
      },
      "relations" : {
        "site_id": 1,
        "content_type_id": 14
      }
    },
    {
      "id": 4,
      "type": "authentication_objects",
      "attributes" : {
        "email": "test@email.com",
        "reset_password_sent_at": null,
        "confirmed_at": "2020-10-13 12:49:39 +0000",
        "confirmation_sent_at": "2020-10-13 12:49:39 +0000",
        "unconfirmed_email": null,
        "content": {
          ...
        }
      },
      "relations" : {
        "site_id": 1,
        "content_type_id": 14
      }
    },
  ]
}
```

This endpoint retrieves all Authentication Objects for a specific site translation

#### HTTP Request

`GET {base_url}/sites/:site_id/authentication_objects`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the authentication objects belong


### Get specific Authentication Object

> `GET {base_url}/sites/1/authentication_objects/4` returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "authentication_objects",
    "attributes" : {
      "email": "test@email.com",
      "reset_password_sent_at": null,
      "confirmed_at": "2020-10-13 12:49:39 +0000",
      "confirmation_sent_at": "2020-10-13 12:49:39 +0000",
      "unconfirmed_email": null,
      "content": {
        ...
      }
    },
    "relations" : {
      "site_id": 1,
      "content_type_id": 14
    }
  },
}
```

This endpoint retrieves a specific Authentication Object.

#### HTTP Request

`GET {base_url}/sites/:site_id/authentication_objects/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the authentication object to retrieve
:id | The id of the authentication object to retrieve


### Create Authentication Object

> An example of valid JSON POST parameters

```json
{
  "data": {
    "email": "test@email.com",
    "invite_type": "without_password",
    "content_type_id": 14,
  }
}
```

> `POST {base_url}/sites/1/authentication_objects` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "type": "authentication_objects",
    "attributes" : {
      "email": "test@email.com",
      "reset_password_sent_at": null,
      "confirmed_at": "2020-10-13 12:49:39 +0000",
      "confirmation_sent_at": "2020-10-13 12:49:39 +0000",
      "unconfirmed_email": null,
      "content": {
        ...
      }
    },
    "relations" : {
      "site_id": 1,
      "content_type_id": 14
    }
  },
}
```

This endpoint creates an Authentication Object.

#### HTTP Request

`POST {base_url}/sites/:site_id/authentication_objects`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site translation to which the new Authentication Object belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
content_type_id | The content type of the new authentication object | Required
email     | The email of the new authentication object | Required
invite_type  | The type of invitation for the user | Null or 'without_password'
password | The password for the user | Required if invite_type is not 'without_password'
 | **--Accepts [Content field parameters](#requests-for-content-objects)--** |

<aside class="info">
If invite_type is 'without_password', the person logging in with the authentication object for the first time (by clicking the link in the email) will have to set a password.
</aside>

### Update Authentication Object

> An example of valid JSON PUT parameters

```json
{
  "data": {
    "email": "new-email@test.com"
  }
}
```

> `PUT {base_url}/sites/1/authentication_objects/3` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "authentication_objects",
    "attributes" : {
      "email": "test@email.com",
      "reset_password_sent_at": null,
      "confirmed_at": "2020-10-13 12:49:39 +0000",
      "confirmation_sent_at": "2020-10-13 12:49:39 +0000",
      "unconfirmed_email": "new-email@test.com",
      "content": {
        ...
      }
    },
    "relations" : {
      "site_id": 1,
      "content_type_id": 14
    }
  },
}
```

This endpoint updates an Authentication Object.

<aside class="info">
Note that changing the email will not immediately change the `email` value, but rather fill the `unconfirmed_email` field. The new email will receive an email with a confirmation link, that changes the values.
</aside>

#### HTTP Request

`PUT {base_url}/sites/:site_id/authentication_objects/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the authentication object to update
:id | The id of the authentication object to update

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
email     | The email of the new authentication object | Required
 | **--Accepts [Content field parameters](#requests-for-content-objects)--** |


### Delete Authentication Objects

> `DELETE {base_url}/sites/1/authentiation_objects/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "authentication_objects",
    "attributes" : {
      "email": "test@email.com",
      "reset_password_sent_at": null,
      "confirmed_at": "2020-10-13 12:49:39 +0000",
      "confirmation_sent_at": "2020-10-13 12:49:39 +0000",
      "unconfirmed_email": null,
      "content": {
        ...
      }
    },
    "relations" : {
      "site_id": 1,
      "content_type_id": 14
    }
  },
}
```

This endpoint deletes a specific Authentication Object.

#### HTTP Request

`DELETE {base_url}/authentication_objects/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the authentication object to delete
:id | The id of the authentication object to delete
