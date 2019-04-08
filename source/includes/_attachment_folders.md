# Attachment Folders

## Get all attachment folders

> `GET {base_url}/sites/1/attachment_folders/` returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 3,
      "type": "attachment_folders",
      "attributes" : {
        "name": "Folder name 3"        
      },
      "relations" : {
        "site_id": 1
      }
    },
    {
      "id": 3,
      "type": "attachment_folders",
      "attributes" : {
        "name": "Folder name 3"        
      },
      "relations" : {
        "site_id": 1
      }
    }
  ]
}
```

This endpoint retrieves all attachment folders for a specific site

### HTTP Request

`GET {base_url}/sites/:site_id/attachment_folders`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the attachment folder belong


## Get specific attachment folder

> `GET {base_url}/attachment_folders/3` returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "attachment_folders",
    "attributes" : {
      "name": "Folder name 3"        
    },
    "relations" : {
      "site_id": 1
    }
  }
}
```

This endpoint retrieves a specific attachment folder.

### HTTP Request

`GET {base_url}/attachment_folders/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the attachment folder to retrieve
:id | The id of the attachment folder to retrieve

### Alternative endpoints

Alternative endpoints are:

* `GET {base_url}/sites/:site_id/attachment_folders/:id`

## Create attachment folder

> An example of valid JSON POST parameters

```json
{
  "data": {    
    "name": "Created Folder",
  }
}
```

> `POST {base_url}/sites/1/attachment_folders` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "attachment_folders",
    "attributes" : {
      "name": "Created Folder"        
    },
    "relations" : {
      "site_id": 1
    }
  }
}
```

This endpoint creates a attachment folder.

### HTTP Request

`POST {base_url}/sites/:site_id/attachment_folders`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the new attachment folder belongs

### POST Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
 name     | The name of the folder | Not null. Required.

## Update attachment folders

> An example of valid JSON PUT parameters

```json
{
  "data": {    
    "name": "A new foldername"
  }
}
```

> `PUT {base_url}/attachment_folders/3` with the above parameters returns JSON structured like this:

```json
{
  "data": {
    "id": 3,
    "type": "attachment_folders",
    "attributes" : {
      "name": "A new foldername"        
    },
    "relations" : {
      "site_id": 1
    }
  }
}
```

This endpoint updates a site.

### HTTP Request

`PUT {base_url}/attachment_folders/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site of the attachment folder to retrieve
:id | The id of the attachment folder to retrieve

### PUT Parameters

Parameter | Description | Constraints
--------- | ----------- | -----------
 name     | The name of the folder | Not null.

### Alternative endpoints

Alternative endpoints are:

* `PUT {base_url}/sites/:site_id/attachment_folders/:id`

## Delete attachment folder

> `DELETE {base_url}/attachment_folders/1` returns JSON structured like this:

```json
{
  "data": {
    "id": 1,
    "type": "attachment_folders",
    "attributes" : {
      "name": "The deleted folder"        
    },
    "relations" : {
      "site_id": 1
    }
  }
}
```

This endpoint deletes a specific attachment folder.

### HTTP Request

`DELETE {base_url}/attachment_folders/:id`

### URL Parameters

Parameter | Description
--------- | -----------
:site_id | The id of the site to which the delete attachment folder belongs
:id | The id of the attachment folder to delete

### Alternative endpoints

Alternative endpoints are:

* `DELETE {base_url}/sites/:site_id/attachment_folders/:id`
