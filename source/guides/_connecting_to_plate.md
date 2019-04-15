## Connecting to the Plate API

Any application can connect to the Plate API using an HTTP request with a
certain method to an endpoint, with some parameters. The [resources section of
the documentation](#resources) describes the details of
all available endpoints, such as the endpoint itself, the required HTTP method and
the permitted/required parameters.

### Method
The HTTP method of a request should be one of `[GET, PUT, POST, DELETE]`.

### Endpoint
These endpoints (urls) of the API are structured as follows: `www.startwithplate.com/api/v2/{specific_path}`,
where `{specific_path}` represents a path corresponding to a certain action.
`{specific_path}` could for example be `partners/1/companies`, so the complete endpoint would be
`www.startwithplate.com/api/v2/partners/1/companies`. This path corresponds to the [index of
all companies for the partner with id 1](#get-all-companies).

### Parameters
Each HTTP request can contain three types of parameters: URL parameters, Query
parameters and POST/PUT parameters.

#### URL parameters
An URL parameter is one that is part of the endpoint itself. These parameters
mostly correspond to an id of a certain resource. The endpoint `www.startwithplate.com/api/v2/partners/1/companies`
contains the URL parameter `:partner_id` with value `1`, indicating that only
companies of the partner with id 1 should be returned.

#### Query parameter
A Query parameter is one that is appended to the endpoint in the form of a [query string](https://en.wikipedia.org/wiki/Query_string).
They can be used to convey information about for example [pagination](#pagination) #TODO FIX PAGINATION REFERENCE.
The endpoint `www.startwithplate.com/api/v2/partners/1/companies?pagination_page=3`
contains the Query parameter `pagination_page` with value `3`, indicating that
the third page of the pagination should be returned.

#### POST/PUT parameters
A POST/PUT parameter is one that is sent in the body of a POST or PUT request.
Plate requires this body to be structured in [JSON format](https://www.w3schools.com/js/js_json_syntax.asp).
The description of each endpoint in the [resources](#resources) section also describes
the accepted POST/PUT parameters.

<aside class="warning">Note that the parameters have to wrapped in a `data` property.</aside>

The example shown aside, shows how to submit the POST parameters `name` and `path`.

```json
{
    "data":{
      "name": "A new name",
      "path": "/some/random/path"
    }
}
```
