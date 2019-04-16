## Errors

> For example when a partner with id=1 does not exist: `GET {base_url}/partners/1`

```json
{
  "errors": [
    {
      "id": 1,
      "resource_type": "partner",
      "status": "404",
      "code": "not-found",
      "title": "Partner not found",
      "detail": "A partner with id=1 could not be found"
    }
  ]
}
```

If a request is invalid, Plate will return a corresponding HTTP status, accompanied
by clarifying error messages. These error messages will be send in the JSON response,
in the `errors` array. (See example) These errors can contain the following keys:

Key | Description
--------- | -----------
id | The request-specified id of the resource that could not be found
resource_type | The kind of resource that could not be found. E.g. `"partner"` or `"site"`
status | The HTTP status code applicable to this problem, as a string value
code | An human-readable version of the status
title | A short description of the problem
detail | A human-readable explanation of the occurred problem
messages  | An array of problem-specific messages. E.g. which [validations failed](#422-unprocessable entity)


The following errors can be returned by Plate:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Wrong authentication details provided
403 | Forbidden -- Forbidden request
404 | Not Found -- The specified resource could not be found.
422 | Unprocessable entity
429 | Too Many Requests -- You're requesting too many requests.
500 | Internal Server Error -- We had a problem with our server. Try again later.

### 400 Bad Request

The provided request does not match with the required syntax. Read the documentation
for the valid syntax.

### 401 Unauthorized

The provided authentication details do not match any valid integration according to the
[authentication requirements](#authentication). Please follow these requirements with an
activated integration key.

### 403 Forbidden

The request was understood, but the authenticated integration is not allowed to perform this action.

### 404 Not Found

One or more resources specified in the request could not be found.

### 422 Unprocessable entity

The request was understood and authorized, but the data provided does not match the requirements.
For example one of the validations of a provided content field was not matched, or a required
attribute was not given.

### 429 Too Many Requests

The server received too many requests, please slow down the rate of requests.
The rate limiting is implemented using the Sliding Log mechanism. This means that
for each partition in time, a certain amount of requests is allowed. Currently, the
allowed number of requests is 50 requests per 5000 milliseconds.

This means that the following sequence of requests will exceed the rate limit:

- **(t = 0 seconds):** 10 requests
- **(t = 1 seconds):** 10 requests
- **(t = 2 seconds):** 10 requests
- **(t = 3 seconds):** 10 requests
- **(t = 4 seconds):** 11 requests

Since at t=4, more than 50 request have been executed in the past 5 seconds.

However the following sequence of requests will not exceed the rate limit:

- **(t = 0 seconds):** 9 requests
- **(t = 1 seconds):** 19 requests
- **(t = 2 seconds):** 0 requests
- **(t = 3 seconds):** 0 requests
- **(t = 4 seconds):** 10 requests
- **(t = 5 seconds):** 20 requests
- **(t = 6 seconds):** 19 requests

Since at every value for t, the amount of requests in the past 5 seconds is at
most 50. (At t=4, the total count in the previous 5 seconds is 48, at t=5, 49, and at t=6, 49 as well)


### 500 Internal Server Error

An error occurred while executing your request. Please try again later, or contact
info@getplate.com for help.
