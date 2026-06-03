# SegmentRelationsDelete

## /api/v2/remarketing/segments/<segment_id>/relations/<id>,<id>+.json

The resource that enables you to delete a large number of data sources from an audience segment.

Used object: [SegmentRelation](https://ads.vk.com/en/doc/api/object/SegmentRelation)

### DELETE

The request deletes data sources from an audience segment.

Request example:

```http
  DELETE /api/v2/remarketing/segments/243/relations/30,31.json
```

Response status codes:

204 - Data sources were successfully deleted.
400 - Due to data source removal, their number in the segment is less than the required "pass_condition" value. Reduce the "pass_condition" value for the segment before making another request.
404 - Segment or data source cannot be found.
