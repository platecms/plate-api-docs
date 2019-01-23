# Theme files

## Get all theme files

> `GET {base_url}/sites/1/theme_files/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "type": "theme_files",
      "attributes" : {
        "etag": "a2b67bf1906313e9f98c3c0a2bbb7b4c",
        "path": "posts",
        "file_name": "index",
        "extension": "plate",
      },
      "relations" : {
        "site_id": 1,
      }
    },
    {
      "id": 2,
      "type": "theme_files",
      "attributes" : {
        "etag": "ef8192015354713e9f98c3c0a2ec76ec",
        "path": "posts",
        "file_name": "show",
        "extension": "plate",
      },
      "relations" : {
        "site_id": 1,
      }
    }
  ]
}
```

This endpoint retrieves all theme files for a specific site

### HTTP Request

`GET {base_url}/sites/:site_id/theme_files`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the theme files belong

## Download all theme files

This endpoint returns all theme files of a specific site packed together in a zip file.

### HTTP Request

`GET {base_url}/sites/:site_id/theme_files/download`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the theme files to download


## Get specific theme file

> `GET {base_url}/sites/1/theme_files/2` returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "type": "theme_files",
    "attributes" : {
      "etag": "ef8192015354713e9f98c3c0a2ec76ec",
      "path": "posts",
      "file_name": "show",
      "extension": "plate",
    },
    "relations" : {
      "site_id": 1,
    }
  }
}

```

This endpoint retrieves details about a specific theme file, but does not return the actual
content of the theme file

### HTTP Request

`GET {base_url}/sites/:site_id/theme_files/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the theme_file to retrieve
:id | The id of the theme_file to retrieve

## Download specific theme file

This endpoint returns a specific theme file as a file.

### HTTP Request

`GET {base_url}/sites/:site_id/theme_files/:id/download`


### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the theme_file to download
:id | The id of the theme_file to download


## Create theme file

> An example of a valid HTTP request body, given the header `Content-type: multipart/formdata; boundary: arandomuniquestring098123`

```text
--arandomuniquestring098123
Content-Disposition: form-data; name="path"

posts
--arandomuniquestring098123
Content-Disposition: form-data; name="file" filename="index.plate"
Content-Type: text/plain

 ... contents of the file 'index.plate' ...
--arandomuniquestring098123-
```

> `POST {base_url}/site/1/theme_files` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "type": "theme_files",
    "attributes" : {
      "etag": "ef8192015354713e9f98c3c0a2ec76ec",
      "path": "posts",
      "file_name": "index",
      "extension": "plate",
    },
    "relations" : {
      "site_id": 1,
    }
  }
}
```

This endpoint is used to upload a new theme file. This endpoint expects a request with
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

### HTTP Request

`POST {base_url}/sites/:site_id/theme_files`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the new theme_file belongs

### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
path      | The path where the new theme_file is situated in the theme or site | Has to be a valid path
file      | The new theme file.  | Required


## Update theme file

> An example of valid JSON PUT parameters

```json
{
  "path": "pages"
  "file_name": "_sidebar"
}
```

> `PUT {base_url}/sites/1/theme_files/2` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "type": "theme_files",
    "attributes" : {
      "etag": "ef8192015354713e9f98c3c0a2ec76ec",
      "path": "pages",
      "file_name": "_sidebar",
      "extension": "plate",
    },
    "relations" : {
      "site_id": 1,
    }
  }
}
```

This endpoint updates a theme file.

### HTTP Request

`PUT {base_url}/sites/:site_id/theme_files/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the theme file to update belongs
:id | The id of the theme file to update

### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
file_name      | The new name of the theme file | Not null
path | The new path of the theme file |


## Delete theme file

> `DELETE {base_url}/sites/1/theme_files/2` returns JSON structured like this:

```json
{
  "data": {
    "id": 2,
    "type": "theme_files",
    "attributes" : {
      "etag": "ef8192015354713e9f98c3c0a2ec76ec",
      "path": "pages",
      "file_name": "_sidebar",
      "extension": "plate",
    },
    "relations" : {
      "site_id": 1,
    }
  }
}
```

This endpoint deletes a specific theme file.

### HTTP Request

`DELETE {base_url}/sites/:site_id/theme_files/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the theme file to update belongs
:id | The id of the theme file to update
