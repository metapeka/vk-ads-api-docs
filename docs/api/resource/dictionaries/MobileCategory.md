# MobileCategory

## /api/v2/mobile\_categories.json

The resource that enables you to collect data on mobile app category.

Used object: [MobileCategory](https://ads.vk.com/en/doc/api/object/MobileCategory)

### GET

The request returns data on mobile apps categories.

Request example:

```http

  GET /api/v2/mobile_categories.json
```

Response example:

```http

    {
        "items": [\
            {\
                "id": 14595,\
                "name": "Arcades and action",\
                "type": "app",\
                "platform": "Android"\
            },\
            {\
                "id": 18,\
                "name": "Books",\
                "type": "app",\
                "platform": "iOS"\
            }\
        ]
    }
```

The response contains the "items" array consisting of the following objects: [MobileCategory](https://ads.vk.com/en/doc/api/object/MobileCategory).
