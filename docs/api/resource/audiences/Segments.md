# Segments

## /api/v2/remarketing/segments.json

The resource that enables you to manage audience segments.

Used object: [Segment](https://ads.vk.com/en/doc/api/object/Segment)

### GET

The request returns a list of all audience segments created by the user.

Request example:

```http
  GET /api/v2/remarketing/segments.json
```

Additional GET parameters:

The following GET parameters enable you to filter data and provide additional information:

- limit - The number of the returned segment. Default value is 20. Maximum value is 100.
- offset - The offset starting point in the list. Default value is 0.
- _id - Data on the segment with the specified ID.
- _id__in - Data on the segments with the specified IDs. The IDs should be separated by commas without spaces: "_id__in=1,2,3".
- _name - Data on the segment with the specified name.
- _name__startswith - Data on the segment available below the specified string.

Response example:

```http
  {
      "items": [
        {
          "id": 243,
          "created": "2017-07-31 14:40:12",
          "updated": "2017-07-31 15:00:50",
          "name": "My segment",
          "pass_condition": 2
        },
      ],
      "count": 10000,
      "offset": 0,
      "limit": 20
  }
```

### POST

The request creates an audience segment.

A segment can contain user-added data sources and other segments. The following limitations apply:

- Maximum number of segments per user: 10000
- Embedding other segments must not generate cycles

Request example:

```http
  POST /api/v2/remarketing/segments.json
```

```http
  {
    "name": "segment",
    "pass_condition": 2,
    "relations": [
        {
          "object_type":"remarketing_counter",
          "params":{"goal_id":"uss", "right":0, "type":"positive", "counter_id":2500001, "left":365}
        },
        {
          "object_type":"segment",
          "object_id":1166
        }
      ]
  }
```

Response example:

```http
    {
      "id": 243,
      "created": "2017-07-31 14:40:12",
      "updated": "2017-07-31 15:00:50",
      "name": "segment",
      "pass_condition": 2
    }
```

Response status codes:

200 - The segment was created successfully.
400 - Data error.

Error example(s):

```http
  {"error": {"code": "segment_limit_exceeded", "message": "Segment limit 10000 exceeded"}}
  {"error": {"code": "validation_failed", "fields": {"pass_condition": {"code": "invalid_condition", "message": "Segment pass condition cannot be greater that number of segment relations"}}}}
  {"error": {"code": "validation_failed", "message": "Validation failed", "fields": {"source_id": {"message": "Unknown {source_type}", "code": "unknown_source", "source_id": 100500}}}}
  {"error": {"code": "validation_failed", "message": "Left should be greater than right"}}
```
