# MobileOperator

## /api/v2/mobile\_operators.json

The resource that provides information about mobile network operator.

Used object: [MobileOperator](https://ads.vk.com/en/doc/api/object/MobileOperator)

### GET

The request returns a list of mobile network operators.

Request example:

```http

   GET /api/v2/mobile_operators.json
```

Response example:

```http

    {
        "items": [\
            {\
                "id": 1,\
                "name": "Beeline"\
            },\
            {\
                "id": 2,\
                "name": "MTC"\
            }\
        ]
    }
```

The response contains the "items" array consisting of the following objects: [MobileOperator](https://ads.vk.com/en/doc/api/object/MobileOperator).
