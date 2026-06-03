# RemarketingUsersList

## /api/v3/remarketing/users_lists/<id>.json

The resource enables you to manage a users list. Such lists are used for targeting external audiences.

Used object: [RemarketingUsersList](https://ads.vk.com/en/doc/api/object/RemarketingUsersList)

### GET

The request returns users list uploaded by the user.

Request example:

```http
  GET /api/v3/remarketing/users_lists/2005000.json
```

Response example:

```http
  {
    "status":"ready",
    "name":"Likes and comments in VK",
    "created":"2017-05-29 18:01:05",
    "base":0,
    "entries_count":5001,
    "ids_count":5001,
    "type":"vk",
    "id":2500000,
    "has_history": false,
    "matched_ids_count": 5001
  }
```

### POST

The request modifies the name of the users list.

Request example:

```http
  POST /api/v3/remarketing/users_lists/2005000.json
  {"name": "New name of the list"}
```

Response status codes:

204 - The name was successfully modified.

400 - The request cannot be validated.

404 - The list cannot be found.

Possible errors:

```http
  {"error": {"code": "validation_failed", "fields": { <fields with errors> }}}
 - Data error.
```

### DELETE

The request deletes the specified users list from the data sources. Only the lists that are not currently used in an audience configuration or provide basis for a Look-alike can be deleted.

Request example:

```http
  DELETE /api/v3/remarketing/users_lists/2005000.json
```

Response status codes:

204 - The list was deleted.

404 - The list cannot be found.

409 - The list is used in an audience configuration or Look-alike .
