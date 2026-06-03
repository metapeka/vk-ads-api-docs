# SegmentRelation

## /api/v2/remarketing/segments/<segment_id>/relations/<id>.json

The resource that enables you to modify data source parameters in an audience segment.

Used object: [SegmentRelation](https://ads.vk.com/en/doc/api/object/SegmentRelation)

### POST

The request modifies data source parameters in an audience segment. Only the "params" field values can be modified.

Request example:

```http
  POST /api/v2/remarketing/segments/243/relations/30.json
```

```http
  {
    "params": {
      "left": 359,
      "right": 1,
      "type": "negative"
    }
  }
```

Response example:

```http
  {"object_type": "remarketing_pricelist", "id": 1120, "object_id": 30}
```

Response status codes:

200 - Data source parameters were modified successfully.
400 - Data error.

Error example(s):

```http
  {"error": {"code": "validation_failed", "message": "Left should be greater than right"}}
```

### DELETE

The request deletes data source from an audience segment.

Request example:

```http
  DELETE /api/v2/remarketing/segments/243/relations/30.json
```

Response status codes:

204 - Data sources were successfully deleted.
400 - Due to data source removal, their number in the segment is less than the required "pass_condition" value. Reduce the "pass_condition" value for the segment before making another request.
404 - Segment or data source cannot be found.
