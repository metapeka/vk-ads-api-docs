# AdPlans

## /api/v2/ad\_plans.json

A resource that allows you to create a new ad campaign or retrieve a list of existing ad campaigns.

Used object: [AdPlan](https://ads.vk.com/en/doc/api/object/AdPlan)

### GET

Retrieving a list of ad campaigns

Request example

```http

    GET /api/v2/ad_plans.json
```

Response example

```http

    {
        "count": 3,
        "offset": 0,
        "items": [\
            {\
                "id": 6617841,\
                "name": "New campaign 2022-07-15 17:53"\
            },\
            {\
                "id": 6711647,\
                "name": "New campaign 2022-08-16 19:49"\
            },\
            {\
                "id": 6711665,\
                "name": "New campaign 2022-08-16 19:51"\
            }\
        ]
    }
```

Available fields are described in [AdPlan](https://ads.vk.com/en/doc/api/object/AdPlan).

The resource supports pagination using the limit and offset parameters.

- limit — number of campaigns in the response. Default: 20

```http

    /api/v2/ad_plans.json?limit=10
```

- offset — shift by N campaigns from the beginning of the current selection

```http

    /api/v2/ad_plans.json?limit=5&offset=15
```

Filters

- \_id — campaign ID

```http

    /api/v2/ad_plans.json?_id=6617841
    /api/v2/ad_plans.json?_id__in=6617841,6711647
```

- \_status — campaign status. Available statuses: "active", "blocked", "deleted"

```http

    /api/v2/ad_plans.json?_status=active
    /api/v2/ad_plans.json?_status__ne=active
    /api/v2/ad_plans.json?_status__in=active,blocked
```

Sorting

- id

```http

    /api/v2/ad_plans.json?sorting=id - ascending
    /api/v2/ad_plans.json?sorting=-id - descending
```

- name

```http

    /api/v2/ad_plans.json?sorting=name - ascending
    /api/v2/ad_plans.json?sorting=-name - descending
```

- status

```http

    /api/v2/ad_plans.json?sorting=status - ascending
    /api/v2/ad_plans.json?sorting=-status - descending
```

- by multiple fields

```http

    /api/v2/ad_plans.json?sorting=status,name,-id
```

### POST

Creating an ad campaign

Request example:

```http

    POST /api/v2/ad_plans.json
    {
        "name": "My new campaign",
        "status": "active",
        "date_start": "2022-04-01 00:00:00",
        "date_end": "2022-04-15 00:00:00",
        "autobidding_mode": "max_goals",
        "budget_limit_day": "1000",
        "budget_limit": "5000",
        "enable_utm": "False",
        "enable_offline_goals": "False",
        "objective": "playersengagement",
        "ad_groups": []
    }
```

Response example:

```http

    HTTP 200
    {
        "id": 9826424
    }
```

The response always contains the id and ad\_groups fields (if the campaign is created with groups).

Important: ad\_groups is not supported in fields and will return an error.

A campaign can be created with one of the following statuses: active, blocked, deleted.

If the status is not provided, the active status is set.

Possible response codes

- 200/204 — campaign saved
- 400 — validation error

Possible error codes:

- pricelist\_not\_found — no pricelist was found for the provided pricelist\_id
- permission\_required — insufficient permissions to modify the field
- required — field is required
- max\_value — value is greater than the maximum
- min\_value — value is less than the minimum
- bad\_value — invalid value format or type
- bad\_items — the list contains invalid values
- read\_only\_field — read-only field
- duplicate\_value — duplicate values
- required\_value — required values are expected
- required\_one\_of\_value — one of the required values is expected
- unallowed\_value — value is not in the list of allowed values
- unallowed\_field — field is not allowed

In general, an error message has the following format:

```http

    {
        "error": {
            "fields": {
                "<field_name_1\>": {
                    "message": "<error_message_1\>",
                    "code": "<error_code_1\>"
                },
                "<field_name_2\>": {
                    "message": "<error_message_2\>",
                    "code": "<error_code_2\>"
                }
            },
            "message": "Validation failed",
            "code": "validation_failed"
        }
    }
```

where field\_name\_N is the name of the field where the error occurred, error\_message\_N is the error description, and error\_code\_N is the error code.

Example:

```http

    {
        "error": {
            "fields": {
                "audit_pixels": {
                    "message": "Error validating audit pixels urls",
                    "code": "audit_pixel_invalid_urls"
                }
            },
            "message": "Validation failed",
            "code": "validation_failed"
        }
    }
```
