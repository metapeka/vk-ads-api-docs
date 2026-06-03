# RemarketingOfflineGoal

## /api/v2/remarketing/offline_goals/<id>.json

A resource that allows you to delete, upload additional data to, and/or change the names of offline conversion lists.

Used object: [RemarketingOfflineGoal](https://ads.vk.com/en/doc/api/object/RemarketingOfflineGoal)

### POST

Request example

```http
    POST /api/v2/remarketing/offline_goals/34235.json

    Content-Type: multipart/form-data
    "list_users": File
    data = {
        "name": "Store visit list"
    }
```

Returned status codes:

204 — Offline conversion list successfully updated.

400 — Validation error.

### DELETE

Request example

```http
    DELETE /api/v2/remarketing/offline_goals/34235.json
```

Returned status codes:

204 — List deleted.

404 — List not found.
