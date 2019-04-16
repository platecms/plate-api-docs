## Positionable Objects

Some of the [resources](#resources) available through the Plate API, are
so called positionable objects. These objects can be positioned within their
parent. For example, [sections](#sections) can be positioned within a [post](#posts),
and [rows](#rows) within a [section](#sections).

Inside a specific parent, each positionable object has a unique, sequential position.
This means that if there are 4 positionable objects inside 1 parent, each object
will have a property `position` with value equal to one of `[1,2,3,4]`.

For example, if there are 3 sections inside a post:

- The first section will have `position=1`
- The second section will have `position=2`
- The last section `position=3`.

The following constraint for values of the position attribute of a
positionable object holds:

<aside id="position-constraint">The position has to be an integer with a minimum value of 1, and a maximum value
equal to the total amount of positionable objects within the parent.</aside>


> A GET endpoint for a positionable object may return JSON as follows:

```json
{
  "data": {
    "id": 1,
    "type": "elements",
    "attributes": {
      "position": 1,
      ...
    },
    ...
  }
}
```

### Responses for positionable objects

The current position of a positionable object is returned in responses, as a property
inside the `attributes` object. See the example aside.


### Requests for positionable objects

> A request to a POST endpoint for a positionable object may contain data as follows:

```json
{
  "data": {
    "position": 2,
    ...
  }
}
```

The position of a positionable object can be set in POST/PUT requests. This can
be done by giving the `position` property inside the POST/PUT parameters. See
the example aside.

The values given for the `position` property have to fall within the [constraint](#position-constraint) on
the position.
