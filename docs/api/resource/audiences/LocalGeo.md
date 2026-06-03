# LocalGeo

## /api/v2/remarketing/local_geo/1234.json

A resource for managing local geo lists. After creating the lists, you can add them to a segment, which can then be included in campaign targeting.

Used object: [LocalGeo](https://ads.vk.com/en/doc/api/object/LocalGeo)

### POST

Editing a local geo list.

Request example:

```http
    POST /api/v2/remarketing/local_geo/1234.json
  {
    "name": "New local geo list name",
    "regions": [{
      "lat": 55.75583,
      "lng": 37.6173,
      "radius": 3000,
      "label": "Moscow city center",
      "address": "Exact address",
    }]
  }
```

Response example:

```http
  {
    "id": 1234,
    "name": "New local geo list name",
    "regions": [{
      "lat": 55.75583,
      "lng": 37.6173,
      "radius": 3000,
      "label": "Moscow city center",
      "address": "Exact address",
    }]
  }
```

Returned status codes:

200 — if the list was successfully updated.

404 — when attempting to update a non-existent list.

Error examples:

```http
  {"error": {"code": "validation_failed", "fields": { fields where errors were found }}}
```

### DELETE

Deleting a local geo list.

Request example:

```http
   DELETE /api/v2/remarketing/local_geo/1234.json
```

Returned status codes:

204 — list deleted.

404 — list not found.

409 — the list is used in the user's remarketing audiences.
