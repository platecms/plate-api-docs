## Filtering

To allow for efficient retrieval of a specific set of objects, the Plate API
allows to filter Index endpoints based on id. This way you can retrieve `n`
specified objects in one request, instead of making `n` requests.

This is done by adding a query parameter `id[]={id_value}` for each object you 
want to retrieve. For example, to retrieve the posts with ids `[1, 5, 6]`, send
a GET request with the following path and query:

```
/site_translation/12/posts?id[]=1&id[]=5&id[]=6
```
