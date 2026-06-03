# MobileOperationSystem

## /api/v2/mobile\_os.json

The resource that provides information about mobile operating system.

Used object: [MobileOperationSystem](https://ads.vk.com/en/doc/api/object/MobileOperationSystem)

### GET

The request returns a list of mobile operating systems.

Request example:

```http

   GET /api/v2/mobile_os.json
```

Response example:

```http

    {
        "items": [\
            {\
                "id": 1,\
                "description": "Android 8.0.0",\
                "version": "8.0.0",\
                "os": "Android"\
            },\
            {\
                "id": 2,\
                "description": "Symbian",\
                "version": "",\
                "os": "Symbian"\
            }\
        ]
    }
```

The response contains the "items" array consisting of the following objects: [MobileOperationSystem](https://ads.vk.com/en/doc/api/object/MobileOperationSystem).
