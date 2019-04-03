# Pagination

To prevent unmanageable response sizes, all index endpoints are paginated.
Each page contains a number of records, and if the total number of records exceeds
the number of records on a page, a next page will be available.

## Pagination response keys

> `GET {base_url}/site_translations/1/posts` returns the following json. Note that
`total_pages` equals 2 since `total_records` > `per_page`

```json
{
  "meta": {
    "pagination": {
      "page": 1,
      "per_page": 250,
      "total_records": 276,
      "total_pages": 2
    }
  },
  "data": [
    ...
  ]
}
```

Each index endpoint will return a pagination keys. These will be located in
the pagination object inside the meta object in a response.
The following keys will be present:

Key | Description
--------- | -----------
page | The page returned in the response
per_page | The amount of records returned per page.
total_records | The total amount of records available.
total_pages | The total amount of pages available.


## Pagination request keys

> `GET {base_url}/site_translations/15/posts?page=3&per_page=15` returns the following json. Note that
`total_pages` equals 2 since `total_records` > `per_page`

```json
{
  "meta": {
    "pagination": {
      "page": 3,
      "per_page": 15,
      "total_records": 50,
      "total_pages": 4
    }
  },
  "data": [
    ...
  ]
}
```

To change the pagination parameters, some [url parameters](#url-parameters) can be
send with the request. These will for example allow to change the page that is returned
in the response, or the number of records that is returned per page. The following
pagination keys are accepted:

Key | Description | Default value | Constraints
--------- | ----------- | ----------- | -----------
page | The page returned in the response | 1 | Has to be larger than 0
per_page | The amount of records returned per page. | Has to be between 1 and 250
