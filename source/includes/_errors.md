# Errors

> For example when a partner with id=1 does not exist: `GET {base_url}/partners/1`

```json
{
  "errors": [
    {
      "id": 1,
      "resource_rtpe": "partner",
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
detail | A human-readable explanation of the occured problem
messages  | An array of problem-specific messages. E.g. which [validations failed](#422-unprocessable entity)


The following errors can be returned by Plate:

Error Code | Meaning
---------- | -------
!400 | Bad Request -- Your request is invalid.
!401 | Unauthorized -- Your API key is wrong.
!403 | Forbidden -- The kitten requested is hidden for administrators only.
404 | Not Found -- The specified resource could not be found.
!405 | Method Not Allowed -- You tried to access a kitten with an invalid method.
!406 | Not Acceptable -- You requested a format that isn't json.
!410 | Gone -- The kitten requested has been removed from our servers.
!418 | I'm a teapot.
!422 | Unprocessable entity
!429 | Too Many Requests -- You're requesting too many kittens! Slow down!
!500 | Internal Server Error -- We had a problem with our server. Try again later.
!503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

## 404 Not Found

One or more resources specified in the request could not be found. The `errors`
object in the JSON response will contain the following keys:
