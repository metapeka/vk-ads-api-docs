# InAppEventCategories

## /api/v1/inapp\_event\_categories.json

The resource enables user to get information about inapp event category.

Used object: [InAppEventCategories](https://ads.vk.com/en/doc/api/object/InAppEventCategories)

### GET

The request returns a list of all available inapp event categories.

Request example:

```http

  GET /api/v1/inapp_event_categories.json
```

Response example:

```http

    {
        "count": 2,
        "items": [\
            {\
                "id": 1,\
                "name": "addToCart",\
            },\
            {\
                "id": 2,\
                "name": "purchase",\
            }\
       ],
   }
```
