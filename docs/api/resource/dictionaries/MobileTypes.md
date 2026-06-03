# MobileTypes

## /api/v2/mobile\_types.json

A resource that provides information about mobile device types.

Used object: [MobileTypes](https://ads.vk.com/en/doc/api/object/MobileTypes)

### GET

The request returns a list of mobile device types.

Request example:

```http

   GET /api/v2/mobile_types.json
```

Response example:

```http

    {
        "items": [\
            {\
                "id": "tablets",\
                "description": "Tablets"\
            },\
            {\
                "id": "smartphones",\
                "description": "Smartphones"\
            }\
        ]
    }
```
