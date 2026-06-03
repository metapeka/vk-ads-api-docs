# Segment

## /api/v2/remarketing/segments/<id>.json

The resource that enables you to manage an audience segment.

Used object: [Segment](https://ads.vk.com/en/doc/api/object/Segment)

### GET

The request returns data on an audience segment.

Request example:

```http
  GET /api/v2/remarketing/segments/243.json
```

Response example:

```http
  {
    "id": 243,
    "created": "2017-07-31 14:40:12",
    "updated": "2017-07-31 15:00:50",
    "name": "My segment",
    "pass_condition": 2
  }
```

### POST

The request modifies parameters of an audience segment.

Request example:

```http
  POST /api/v2/remarketing/segments/243.json
```

```http
  {
    "name": "segment v2",
    "pass_condition": 1
  }
```

Response example:

```http
    {
      "id": 243,
      "created": "2017-07-31 14:40:12",
      "updated": "2017-07-31 15:00:50",
      "name": "Segment v2",
      "pass_condition": 1
    }
```

Response status codes:

201 - The segment was created successfully.
400 - Data error.

Error example(s):

```http
  {"error": {"code": "validation_failed", "fields": {"pass_condition": {"code": "invalid_condition", "message": "Segment pass condition cannot be greater that number of segment relations"}}}}
```

### DELETE

The request deletes an audience segment. Only the segments that are not currently used in a campaign or another segment can be deleted.

Request example:

```http
  DELETE /api/v2/remarketing/segments/243.json
```

Response status codes:

204 - The segment was deleted.
404 - The segment was not found.
409 - The segment is used in a campaign or another segment.
