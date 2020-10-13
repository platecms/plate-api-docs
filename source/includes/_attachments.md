## Attachment

### Get all attachments

> `GET {base_url}/sites/1/attachments/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "attachments",
      "attributes" : {
        "file_name": "some_image.jpg",
        "size": 12391,
        "title": "An image"
      },
      "relations" : {
        "site_id": 1,
        "attachment_folder_id": 2
      }
    },
    {
      "id": 4,
      "type": "attachments",
      "attributes" : {
        "file_name": "other_image.jpg",
        "size": 2002,
        "title": "Another image"
      },
      "relations" : {
        "site_id": 1,
        "attachment_folder_id": null
      }
    }
  ]
}
```

This endpoint retrieves all attachments for a specific site

#### HTTP Request

`GET {base_url}/sites/:site_id/attachments`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the attachments belong
:attachment_folder_id | The id of the attachment folder to which the attachments belong

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/attachment_folder/:attachment_folder_id/attachments/` (Gives all attachments in an attachment folder)


### Get specific attachment

> `GET {base_url}/sites/1/attachments/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "attachments",
    "attributes" : {
      "file_name": "some_image.jpg",
      "size": 12391,
      "title": "An image"
    },
    "relations" : {
      "site_id": 1,
      "attachment_folder_id": 2
    }
  }
}
```

This endpoint retrieves information about a specific attachment, but does not return the actual content of the attachment

#### HTTP Request

`GET {base_url}/attachments/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the attachment to retrieve
:id | The id of the attachment to retrieve
:attachment_folder_id | The id of the attachment folder to which the attachments belong

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/attachments/:id`
* `GET {base_url}/attachment_folders/:attachment_folder_id/attachments/:id`


### Download specific attachment

This endpoint returns a specific attachment as a file.

#### HTTP Request

`GET {base_url}/attachments/:id/download`

#### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/attachments/:id/download`
* `GET {base_url}/attachment_folders/:attachment_folder_id/attachments/:id/download`


#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the attachment to retrieve
:id | The id of the attachment to retrieve
:attachment_folder_id | The id of the attachment folder to which the attachments belong


### Create attachment

> An example of a valid HTTP request body, given the header `Content-type: multipart/formdata; boundary: arandomuniquestring098123`

```text
--arandomuniquestring098123
Content-Disposition: form-data; name="title"

A title describing this attachment
--arandomuniquestring098123
Content-Disposition: form-data; name="file" filename="plate.png"
Content-Type: image/png

 ... contents of the file 'plate.png' ...
--arandomuniquestring098123-
```

> `POST {base_url}/site/1/attachments` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "attachments",
    "attributes" : {
      "file_name": "plate.png",
      "size": 12391,
      "title": "A title describing this attachment"
    },
    "relations" : {
      "site_id": 1,
      "attachment_folder_id": 2
    }
  }
}
```

This endpoint is used to upload a new attachment. This endpoint expects a request with
`Content-type: multipart/form-data, boundary={boundary-key}`, following the `multipart/form-data`
principle as defined in <a href="https://tools.ietf.org/html/rfc7578#section-4.1" target="_blank"> RFC 7578</a>  and
shown in <a href="https://tools.ietf.org/html/rfc1867#section-6" target="_blank">RFC 1867</a>.

All POST parameters should also be sent according to the `multipart` principle, that is,
each variable should have its own part in the request body. To the right an example
of a valid HTTP request is shown.

<aside class="warning">
Be aware of the fact that this endpoint requires requests with a different type of content than
most other requests, and should follow the `multipart/form-data`
principle as defined in <a href="https://tools.ietf.org/html/rfc7578#section-4.1" target="_blank"> RFC 7578</a>
</aside>

#### HTTP Request

`POST {base_url}/sites/:site_id/attachments`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the new attachment belongs

#### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
title      | The title of the new attachment | Not null.
file      | The new attachment.  | Required

#### Alternative endpoints

Alternative endpoints are:

* `POST {base_url}/attachment_folders/:attachment_folder_id/attachments`


### Update attachments

> An example of valid JSON PUT parameters

```json
{
  "data": {
    "title": "A new attachment_title"
  }
}
```

> `PUT {base_url}/sites/1/attachments/5` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "attachments",
    "attributes" : {
      "file_name": "plate.png",
      "size": 12391,
      "title": "A new attachment_title"
    },
    "relations" : {
      "site_id": 1,
      "attachment_folder_id": 2
    }
  }
}
```

This endpoint updates an attachment.

#### HTTP Request

`PUT {base_url}/attachments/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the attachment to retrieve
:id | The id of the attachment to retrieve
:attachment_folder_id | The id of the attachment folder to which the attachments belong

#### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
title      | The title of the updated attachment | Not null.
attachment_folder_id | The id of the attachment folder to which the updated attachment belongs | Id of an existing attachment folder.

#### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/attachment_folders/:attachment_folder_id/attachments/:id`
* `PUT {base_url}/sites/:site_id/attachments/:id`

### Delete attachment

> `DELETE {base_url}/sites/1/attachments/5` returns JSON structured like this:

```json
{
  "data": {
    "id": 5,
    "type": "attachments",
    "attributes" : {
      "file_name": "plate.png",
      "size": 12391,
      "title": "A new attachment_title"
    },
    "relations" : {
      "site_id": 1,
      "attachment_folder_id": 2
    }
  }
}
```

This endpoint deletes a specific attachment.

#### HTTP Request

`DELETE {base_url}/attachments/:id`

#### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the attachment to retrieve
:id | The id of the attachment to retrieve
:attachment_folder_id | The id of the attachment folder to which the attachments belong

#### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/attachment_folders/:attachment_folder_id/attachments/:id`
* `DELETE {base_url}/sites/:site_id/attachments/:id`
