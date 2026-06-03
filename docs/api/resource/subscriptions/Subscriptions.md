# Subscriptions

## /api/v3/subscription.json

A resource that allows you to manage subscriptions to notifications about creation or modification of a user's objects. It supports only subscriptions created via this method; subscriptions from `v2/subscriptions.json` are not supported.

### GET

Returns a list of all subscriptions the user has.

Request example:

```http
GET /api/v3/subscription.json
```

Additional GET parameters:

You can filter/paginate the data using the following parameters:

- `fields` — list of fields to include in the response.
- `limit` — number of subscriptions returned in the response. Default: 20. Maximum: 50.
- `offset` — starting offset from the beginning of the subscriptions list. Default: 0.

Response example:

```http
{
  "items": [\
    {\
      "id": 123,\
      "resource": "BANNER",\
      "callback_url": "https://domain.ru/mt/callback/"\
    }\
  ],
  ...
  "count": 10000,
  "offset": 0,
  "limit": 20
}
```

### POST

Creates a subscription to notifications about changes to all objects of the specified resource for the user whose token is provided.

Request example:

```http
POST /api/v3/subscription.json
{
  "resource": "BANNER",
  "callback_url": "https://domain.ru/mt/callback/"
}
```

Response example:

```http
{
  "id": 123
}
```

Returned status codes:

- **200** — subscription successfully created.
- **400** — validation error.

Error examples:

```http
{"error": {"fields": {"callback_url": {"expected": "URL", "message": "Bad value", "code": "bad_value"}}, "message": "Validation failed", "code": "validation_failed"}}

{"error": {"fields": {"resource": {"message": "Unallowed value", "code": "unallowed_value", "allowed_values": ["BANNER", "CAMPAIGN", "OKLEADAD"]}}, "message": "Validation failed", "code": "validation_failed"}}

{"error": {"fields": {"callback_url": {"expected": "URL with https:// schema", "message": "Bad value", "code": "bad_value"}}, "message": "Validation failed", "code": "validation_failed"}}
```

When an action that may trigger sending notifications is performed (for example, saving a campaign with a moderation status change, or a new lead appearing for the `OKLEADAD` subscription), a notification about this change is sent to all users subscribed to this event.

Notification payload structure:

```http
{
  "id": <id>,
  "resource_id": <object_id>,
  "resource": <resource>,
  "callback_url": <callback_url>,
  "created": <datetime>,
  "data": <response>
}
```

Where:

- `id` — notification identifier.
- `object_id` — identifier of the changed object.
- `resource` — resource name for which the subscription to changes of all objects was created (the `resource` field of the [Subscription](https://ads.vk.com/en/doc/api/object/Subscription) object).
- `callback_url` — address to which the event notification will be sent. Must use the `https://` scheme.
- `datetime` — notification creation time.
- `response` — a JSON object identical to the response returned by the "get object" method of the corresponding resource.

Example:

```http
{
  "id": "07c0810ac51c47c98e001b1e91c94ba4",
  "resource_id": 1,
  "resource": "LEAD",
  "callback_url": "https://domain.ru/mt/callback/",
  "created": "2019-06-02 18:23:29.797499",
  "data": {
    "id": 4,
    "form_id": 19,
    "ad_plan_id": 1,
    "ad_group_id": 3,
    "banner_id": 2,
    "created_at": "2023-01-31 09:25:41.26 +0000 UTC",
    "answers": [],
    "contact_info": {
      "first_name": "Ivan",
      "phone": "+78005553535",
      "birth_date": "2006-01-02",
      "city": "Moscow"
    }
  }
}
```
