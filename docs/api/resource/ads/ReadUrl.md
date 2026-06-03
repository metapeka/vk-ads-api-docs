# ReadUrl

## /api/v2/urls/<url\_id>.json

The resource enables you to get information about a URL you advertise.

Used object: [URL](https://ads.vk.com/en/doc/api/object/URL)

### GET

The request returns information about an advertised URL.

Request example:

```http

  GET /api/v2/urls/13123170.json
```

Response example:

```http

  {
     "counters": [],
     "has_goals": false,
     "id": 13123170,
     "url": "http://example.com/2",
     "url_types": [\
       "external",\
       "external_new"\
     ]
  }
```
