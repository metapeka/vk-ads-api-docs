# LocalGeos

## /api/v2/remarketing/local_geo.json

A resource for managing local geo lists. After creating the lists, you can add them to a segment, which can then be included in campaign targeting.

Used object: [LocalGeo](https://ads.vk.com/en/doc/api/object/LocalGeo)

### GET

Retrieving the list of local geo lists.

Request example:

```http
   GET /api/v2/remarketing/local_geo.json?fields=id,name,regions
```

Response example:

```http
  {
    "items": [{
      "id": 1,
      "name": "New local geo list",
      "regions": [{
        "lat": 55.75583,
        "lng": 37.6173,
        "radius": 3000,
        "label": "Moscow city center",
        "address": "Exact address"
      }]
    }]
  }
```

The response contains an items array consisting of [LocalGeo](https://ads.vk.com/en/doc/api/object/LocalGeo) objects.

### POST

Creating a local geo list.

Request example:

```http
    POST /api/v2/remarketing/local_geo.json
  {
    "name": "New local geo list",
    "regions": [{
      "lat": 55.75583,
      "lng": 37.6173,
      "radius": 3000,
      "label": "Moscow city center",
      "address": "Exact address"
    }]
  }
```

Response example:

```http
  {
    "id": 1,
    "name": "New local geo list",
    "regions": [{
      "lat": 55.75583,
      "lng": 37.6173,
      "radius": 3000,
      "label": "Moscow city center",
      "address": "Exact address"
    }]
  }
```

Returned status codes:

200 — if the list was successfully created.

400 — in the following cases:

- validation errors — code validation_failed;

Error examples:

```http
  {"error": {"code": "validation_failed", "fields": { fields where errors were found }}}
```
