## Content Objects

Some of the [resources](#resources) available through the Plate API have
a dynamic set of content fields. These content fields can be defined through
the Plate dashboard. Resources which have such content fields are called content
objects. Examples of content objects are [site translations](#site-translations),
[posts](#posts), [sections](#sections) and [elements](#elements).
The endpoints for content objects have some specific features/requirements.

### Responses for content objects

> A GET endpoint for a content object may return JSON as follows:

```json
{
  "data": {
    "id": 1,
    "type": "elements",
    "attributes": {
      "content": {
        "categories": {
          "value": [789],
          "type": "reference",
          "subtype": "posts",
          "content_field_id": 123
        },
        "name": {
          "value": "Pied Piper",
          "type": "string",
          "content_field_id": 456
        }
      },
      ...
    },
    ...
  }
}
```

For endpoints of content objects, the JSON response is expanded with the values
set for the content fields of the content objects.

Consider an [element](#elements) with `id=5`, having two content fields:

- `categories` (A reference content field to a Post)
- `name` (A text content field)

An example response is shown aside.

As can be seen in the example response, the API will return an extra property in the
`"attributes"` objects, named `"content"`, next to the 'standard' attributes.
The `"content"` object in the response contains an object for each of the
content fields of the selected object (the element, in the example). Each content field
object contains the properties of that content field for the content object.

For each content field, the following properties are returned:

Property | Description
--------- | -----------
value | The value of the content field for the selected content object.
type | The type of content field. E.g. "string", "array" or "reference".
subtype (optional) | The subtype of the content field. Only given for content fields with type "array" or "reference". E.g. "attachments", or "posts".
content_field_id | The id of the content_field

#### Value
The `value` property can be of different types - it can be a string, integer or array,
depending of the type of content field. So the `type` property can be used to deduce
the meaning of the value found in the `value` property.

For reference fields, the `value` property will be an array of numbers. These
numbers are ID's of referenced resources for the content field. The
`subtype` property will indicate what kind of resource is selected/referenced.

<aside class="notice"> For example, if the <code>value</code> property equals <code>[12, 23, 24]</code>, the <code>type</code> property equals
<code>reference</code>, and the <code>subtype</code> property equals <code>posts</code>, then the content field contains
references to the posts with ids 12, 23 and 24. </aside>

For array fields, the `value` property will be an array of numbers or strings,
depending on the `subtype` property. If the `subtype` property equals `attachments`,
the `value` property will be an array of numbers, representing attachments. If the
`subtype` property equals `text`, then the `value` property will be an array of
strings, which is the actual value of the content field.

### Requests for content objects

> A request to a POST endpoint for a content object may contain data as follows:

```json
{
  "data": {
    ...
    "name": "A name for the new element",
    "categories": [
      {
        "id": 25
      },
      {
        "title": "A title for a newly created reference post"
        ...
      }
    ]
  }
}
```

For PUT/POST endpoints of content objects, the data sent with the request also
can contain data for the content fields for content objects. Consider creating
an element with a post type that has the following content fields:

- `name` (A text content field)
- `categories` (A reference content field to a Post)

An example of request data is shown aside.

As can be seen in the example, for each content field an object or value is provided in
the request data.

- For content fields which take plain values, such as content fields
with type `string` or `choice`, the plain value is given. This value can be a string
or integer.
- For content fields with type `media`, the value has to be an id of an
existing attachment.
- For content fields with type `reference`, the value has to be an array of objects.
This object can consist of either an id of an existing object to reference to,
or the data for a new object to reference to.

<aside class="notice"> In the example, the field `categories` (with type `reference`)
will be set with two referenced objects. One existing object with `id=25`, and one
new object which will have the value "A title for  a newl...." for the content field
`title`. Note that data for referenced content fields can be nested, so there is no
need to first create an object to reference to, and then use the id in the request
for the referring object. Instead, nest the data directly.</aside>
