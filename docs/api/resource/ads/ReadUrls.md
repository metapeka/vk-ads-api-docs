# ReadUrls

## /api/v2/urls/<url\_id1>,<url\_id2>,<url\_id3>.json

The resource enables you to get information about several URLs you advertise.

Used object: [URL](https://ads.vk.com/en/doc/api/object/URL)

### GET

The request returns information about advertised URLs.

Request example:

```http

  GET /api/v2/urls/13123170,13123171.json
```

Response example:

```http

  {
      "items": [\
          {\
              "counters": [],\
              "has_goals": false,\
              "id": 13123170,\
              "url": "http://example.com/2",\
              "url_types": [\
                "external",\
                "eternal_new"\
              ]\
          },\
          {\
              "counters": [],\
              "has_goals": false,\
              "id": 13123171,\
              "url": "http://example.com/3",\
              "url_types": []\
          }\
      ]
  }
```
