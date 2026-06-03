# RemarketingOfflineGoals

## /api/v2/remarketing/offline_goals.json

A resource that allows you to create a new offline conversion list or retrieve an array of existing offline conversion lists.

Used object: [RemarketingOfflineGoal](https://ads.vk.com/en/doc/api/object/RemarketingOfflineGoal)

### GET

Retrieve an array of offline conversion lists.

Request example

```http
GET /api/v2/remarketing/offline_goals.json
```

Response example

```http
{
  "items": [
    {
      "id": 83213,
      "created": "2017-07-04 17:36:16",
      "updated": "2018-11-09 12:08:57",
      "name": "Store visits list",
      "type": "phone",
      "attribution_period": 90,
      "load_status": "matched"
    },
    {
      ...
    }
  ]
}
```

### POST

Create an offline conversion list.

Request example

```http
POST /api/v2/remarketing/offline_goals.json

Content-Type: multipart/form-data
"list_users": File
data = {
  "name": "Store visits list",
  "attribution_period": 90,
  "type": "email"
}
```

Returned status codes:

- **204** — Offline conversion list successfully added.
- **400** — Validation error.
