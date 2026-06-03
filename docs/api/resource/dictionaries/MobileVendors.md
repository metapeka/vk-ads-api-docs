# MobileVendors

## /api/v2/mobile\_vendors.json

The resource that provides information about mobile device vendors.

Used object: [MobileVendors](https://ads.vk.com/en/doc/api/object/MobileVendors)

### GET

The request returns a list of mobile devices vendors.

Request example:

```http

   GET /api/v2/mobile_vendors.json
```

Response example:

```http

    {
        "items": [\
            {\
                "id": 1,\
                "description": "Samsung"\
            },\
            {\
                "id": 2,\
                "description": "Nokia"\
            }\
        ]
    }
```

The response contains the "items" array consisting of the following objects: [MobileVendors](https://ads.vk.com/en/doc/api/object/MobileVendors).
