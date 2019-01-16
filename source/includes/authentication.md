# Authentication and Authorization

To authenticate a request, it has to be accompanied by authentication details.
The authentication details consist of 2 parts, a public key and a signature calculated using
the secret key. If a request is authenticated correctly, it will also be authorized.

## Integration

To create a key pair (a public and a secret key), you have to create a so-called integration
in the Plate dashboard. An integration represents an external application that interacts
with the Plate API. When you create an integration, you are able to create a key pair.

<aside class="notice">
An integration (and its key pair) should be used by at most 1 external application,
so it is easy to add or revoke access for an external application, without inflicting
other applications.
</aside>



## Authentication procedure

To authenticate a request, two headers have to be sent with the request: the `Date` header
and the `Authorization` header.

### Date header

The `Date` header should contain the current time, formatted
according to <a href="https://tools.ietf.org/html/rfc7231#section-7.1.1.1" target="_blank">RFC 7231</a>.
A request will be unauthorized if this date is more than 15 minutes past the time at which
the server receives this request.

### Authorization header

The `Authorization` consists of 3 parts: `hmac {public_key}:{signature}`.

* `hmac`: The authentication protocol used, and is not variable.
* `{public_key}`: The public key of the [integration](#integration) that you
want to use for authenticating this request.
* `{signature}`: The signature of this request, which is calculated
using the secret key matching the `{public_key}`.

### Calculating the signature

> The layout of the string to sign of a request

```
{http_method}
{url_domain}
{url_path}
{query_string}
{http_date}
```

To calculate the signature of a request, first the string to sign has to be setup.
The layout of the string to sign is shown to the right.
<aside class="notice">
Newlines in the string to sign should be represented by `\n` characters when calculating
the signature.
</aside>

> An example string to sign (note that `paginate_amount` and `paginate_page` are
  fictional parameters, and only there as an example)

```
GET
www.startwithplate.com
/api/v2/partners/15/sites
paginate_amount=10&paginate_page=2
Sun, 06 Nov 1994 08:49:37 GMT
```

> The valid Authorization header given the above string to sign is

```
Authorization hmac mypublickey:FOjhvBsNceYeVNAJtneSLUeYbNO133Gj1sx+aEu7I8A2ixH3VyYpc6PtxGDGVzpG1EPrDaL7sgurV2Q0+8BHDQ==
```

The string to sign consists of the following parts:

* `{http_method}`: The HTTP method of the request, e.g. `GET` or `POST`.
* `{url_domain}`: The domain part of the url, without the protocol, path or query parameters.
* `{url_path}`: The path part of the url, e.g. `/api/v2/partners/15`
* `{query_string}`: The query string part of the url. Note that the parameters should be sorted
alphabetically, based on the key of the parameters. So `key=value&alpha=beta` is incorrect,
but `alpha=beta&key1=value` is correct.
* `{http_date}`: The value that is set in the [`Date` header](#date-header).

To get the signature, the HMAC based on the string to sign has to be calculated, as defined in [RFC 2104](https://tools.ietf.org/html/rfc2104), using the SHA512 hash algorithm. The key that is used for
the HMAC, is the secret key that corresponds to the public key that is used in the authorization
header, alongside the signature. The signature has be send in base64 representation, so not in a
hexadecimal representation.

#### Example

The HMAC of the example string to sign (shown to the right), with a secret key of `mysecretkey`, would be:
`FOjhvBsNceYeVNAJtneSLUeYbNO133Gj1sx+aEu7I8A2ixH3VyYpc6PtxGDGVzpG1EPrDaL7sgurV2Q0+8BHDQ==`.

So given a key pair with a public key of `mypublickey` and a secret key of `mysecretkey`,
and a request with:

* The method `GET`
* The url `www.startwithplate.com/api/v2/partners/15/sites?paginate_amount=10&paginate_page=2`
* A `Date` header of `Sun, 06 Nov 1994 08:49:37 GMT`

the valid `Authorization` header would be:

`hmac mypublickey:FOjhvBsNceYeVNAJtneSLUeYbNO133Gj1sx+aEu7I8A2ixH3VyYpc6PtxGDGVzpG1EPrDaL7sgurV2Q0+8BHDQ==`
