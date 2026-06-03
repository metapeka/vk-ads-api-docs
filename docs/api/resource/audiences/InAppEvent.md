# InAppEvent

## /api/v2/remarketing/inapp_events/<rb_mobile_app_id>/trackers/<tracker_id>/events/<inapp_event_id>.json

The resource enables user to edit inapp category.

Used object: [InAppEvent](https://ads.vk.com/en/doc/api/object/InAppEvent)

### POST

Edit inapp event category.

Request example:

```http
  POST /api/v2/remarketing/inapp_events/65/trackers/1/events/7.json
  {
    "inapp_event_category_id": 2
  }
```

Where:
65 - url object id;

1 - tracker id;

7 - inapp event id.

Response status codes:

204 - Data successfully updated.

400 - Validation error.

404 - url object id, tracker id or inapp event id not found or not available.

Errors example:

```http
  {"error": {"code": "validation_failed", "fields": {"inapp_event_category_id": {"code": "bad_value", "message": "Bad value"}}}}
 - inapp category id is not found.
```
