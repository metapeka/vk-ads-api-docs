# AdGroups

## /api/v2/ad\_groups.json

A resource that allows you to create a new ad group or retrieve a list of existing ad groups.

Used object: [AdGroup](https://ads.vk.com/en/doc/api/object/AdGroup)

### GET

Retrieving a list of ad groups

Request example

```http

    GET /api/v2/ad_groups.json
```

Response example

```http

    {
        "count": 3,
        "offset": 0,
        "items": [\
            {\
                "package_id": 83,\
                "last_updated": "2022-07-04 17:36:16",\
                "id": 6617841,\
                "name": "New ad group 2022-07-15 17:53"\
            },\
            {\
                "package_id": 83,\
                "last_updated": "2022-07-04 17:36:16",\
                "id": 6711647,\
                "name": "New ad group 2022-08-16 19:49"\
            },\
            {\
                "package_id": 83,\
                "last_updated": "2022-07-04 17:36:16",\
                "id": 6711665,\
                "name": "New ad group 2022-08-16 19:51"\
            }\
        ]
    }
```

Available fields are described in [AdGroup](https://ads.vk.com/en/doc/api/object/AdGroup).

The resource supports pagination using the limit and offset parameters.

- limit — number of groups in the response. Default: 20

```http

    /api/v2/ad_groups.json?limit=10
```

- offset — shift by N groups from the beginning of the current selection

```http

    /api/v2/ad_groups.json?limit=5&offset=15
```

Filters

- \_id — group ID

```http

    /api/v2/ad_groups.json?_id=6617841
    /api/v2/ad_groups.json?_id__in=6617841,6711647
```

- \_status — group status. Available statuses: "active", "blocked", "deleted"

```http

    /api/v2/ad_groups.json?_status=active
    /api/v2/ad_groups.json?_status__ne=active
    /api/v2/ad_groups.json?_status__in=active,blocked
```

- \_last\_updated — datetime of the last update of the group together with banners. Available lookups: "lt" (less than), "lte" (less than or equal), "gt" (greater than), "gte" (greater than or equal)

```http

    /api/v2/ad_groups.json?_last_updated__gt=2022-01-01 00:00:00
    /api/v2/ad_groups.json?_last_updated__gte=2022-01-01 00:00:00
    /api/v2/ad_groups.json?_last_updated__lt=2022-01-01 00:00:00
    /api/v2/ad_groups.json?_last_updated__lte=2022-01-01 00:00:00
```

Sorting

- id

```http

    /api/v2/ad_groups.json?sorting=id - ascending
    /api/v2/ad_groups.json?sorting=-id - descending
```

- name

```http

    /api/v2/ad_groups.json?sorting=name - ascending
    /api/v2/ad_groups.json?sorting=-name - descending
```

- status

```http

    /api/v2/ad_groups.json?sorting=status - ascending
    /api/v2/ad_groups.json?sorting=-status - descending
```

- by multiple fields

```http

    /api/v2/ad_groups.json?sorting=status,name,-id
```

### POST

Creating an ad group

Request example:

```http

    POST /api/v2/ad_groups.json
    {
        "name": "My new group",
        "status": "active",
        "date_start": "2022-04-01 00:00:00",
        "date_end": "2022-04-15 00:00:00",
        "autobidding_mode": "second_price",
        "budget_limit_day": "1000",
        "budget_limit": "5000",
        "mixing": "fastest",
        "price": "642.12",
        "age_restrictions": "18+",
        "banner_uniq_shows_limit": 2130,
        "uniq_shows_period": "week",
        "uniq_shows_limit": 100,
        "audit_viewability": "moat",
        "enable_utm": "False",
        "package_id": 449,
        "objective": "playersengagement",
        "banners": [{\
            "content": {\
                "primary": {\
                    "id": 32433493\
                }\
            },\
            "urls": {\
                "primary": {\
                    "id": 98574325\
                }\
            },\
            "textblocks": {\
                "primary": {\
                    "title": "Everyone needs this product!",\
                    "text": "All you need for happiness is..."\
                }\
            }\
        }, {\
            "content": {\
                "primary": {\
                    "id": 32433494\
                }\
            },\
            "urls": {\
                "primary": {\
                    "id": 98574325\
                }\
            },\
            "textblocks": {\
                "primary": {\
                    "title": "Buy me!",\
                    "text": "Buy right now"\
                }\
            }\
        }],
        "targetings": {
            "age": {
                "age_list": [21, 22, 23]
            },
            "birthday": {
                "days_after": 5,
                "days_before": 10
            },
            "fulltime": {
                "mon": [1],
                "tue": [1, 2],
                "wed": [1, 2, 3],
                "thu": [1, 2, 3, 4],
                "fri": [1, 2, 3, 4, 5],
                "sat": [1, 2, 3, 4, 5, 6],
                "sun": [1, 2, 3, 4, 5, 6, 7],
                "flags": [],
            },
            "pads": [5206],
            "sex": ["male"],
            "interests": [9018,7356],
            "interests_soc_dem": [7653,7655]
        }
    }
```

Response example:

```http

    HTTP 200
    {
        "id": 9826424,
        "banners": [{\
            "id": 23826937\
        }]
    }
```

The response always contains the id and banners fields (if the group is created with banners).

Important: banners is not supported in fields and will return an error.

Available fields, targetings, and other ad group settings are described in the [Package object](https://ads.vk.com/en/doc/api/object/Package) within which the group is created.

A group can be created with one of the following statuses: active, blocked, deleted.

If the status is not provided, the active status is set.

Possible response codes

- 200/204 — group saved
- 400 — validation error

Possible error codes:

- invalid\_package — the package is not available to this user
- can\_not\_set — cannot switch to the specified package
- step — invalid step when setting budget\_limit. The change must be a multiple of budget\_limit\_step from the `/api/v2/currencies.json` API for the user's currency
- not\_allowed\_for\_package — changes are not available in this package
- pricelist\_not\_found — no pricelist was found for the provided pricelist\_id
- permission\_required — insufficient permissions to modify the field
- audit\_pixel\_invalid\_roles — invalid audit pixel roles
- audit\_pixel\_max\_count — audit pixel count limit exceeded
- audit\_pixel\_must\_be\_unique — audit pixels must be unique
- audit\_pixel\_invalid\_urls — audit pixel has an invalid URL
- min\_translation\_hours — minimum broadcast time in fulltime targeting must be at least 8 hours
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

Examples of specifying targetings when creating/editing groups

- age:

```http

    {
        "age": {
            "age_list": [0, 12, 13, 14, 22, 23, 24]
        }
    }
```

- birthday:

```http

    {
        "birthday": {
            "days_after": 5,
            "days_before": 10
        }
    }
```

- browser:

```http

    {
        "browser": ["edge", "internet_explorer", "opera"]
    }
```

- fulltime:

```http

    {
        "fulltime": {
            "tue": [2],
            "wed": [2, 3],
            "thu": [2, 3, 4],
            "fri": [2, 3, 4, 5],
            "sat": [2, 3, 4, 5, 6],
            "sun": [2, 3, 4, 5, 6, 7],
            "flags": ["use_holidays_moving", "cross_timezone"],
    }
```

- geo:

```http

    {
        "geo": {
            "regions": [56, 97, 100]
        }
    }
```

or

```http

    {
        "geo": {
            "local_geo": {
                "visit_type": "usual",
                "loc_type": ["home", "work"],
                "locations": [{\
                    "lat": 55.75583,\
                    "lng": 37.6173,\
                    "radius": 3000,\
                    "label": "Moscow city center",\
                    "address": "Exact address"\
                }]
            }
        }
    }
```

You cannot pass local\_geo and regions in geo at the same time.

Example of incorrect geo payload:

```http

    {
        "regions": [56, 97, 100],
        "local_geo": {
            "visit_type": "usual",
            "loc_type": ["home", "work"],
            "locations": [{\
                "lat": 55.75583,\
                "lng": 37.6173,\
                "radius": 3000,\
                "label": "Moscow city center",\
                "address": "Exact address"\
            }]
        }
    }
```

Also, you cannot pass local\_geo and/or regions together with geo at the same time.

Example of an incorrect request:

```http

    POST /api/v2/ad_groups/9826424.json
    {
        "targetings": {
            "regions": [56, 97, 100],
            "geo": {
                "regions": [56, 97, 100]
            },
        }
    }
```

- group\_members:

```http

    {
        "group_members": "not_group_member"
    }
```

- interests:

```http

    {
        "interests": [9413, 9414, 9415]
    }
```

- interests\_soc\_dem:

```http

    {
        "interests_soc_dem": [0, 12, 13, 14, 22, 23, 24]
    }
```

- local\_geo:

```http

    {
        "local_geo": {
            "visit_type": "usual",
            "loc_type": ["home", "work"],
            "locations": [{\
                "lat": 55.75583,\
                "lng": 37.6173,\
                "radius": 3000,\
                "label": "Moscow city center",\
                "address": "Exact address"\
            }]
        }
    }
```

- mobile\_apps:

```http

    {
        "mobile_apps": "deleted"
    }
```

- mobile\_operation\_systems:

```http

    {
        "mobile_operation_systems": [37, 38, 39]
    }
```

- mobile\_operators:

```http

    {
        "mobile_operators": [3, 5, 6]
    }
```

- mobile\_prefix:

```http

    {
        "mobile_prefix": ["mts", "beeline", "megafon"]
    }
```

- mobile\_types:

```http

    {
        "mobile_types": ["smartphones", "tablets"]
    }
```

- mobile\_vendors:

```http

    {
        "mobile_vendors": [14, 41, 49]
    }
```

- pad\_category:

```http

    {
        "pad_category": {
            "iOS": [12, 13, 41],
            "Android": [7, 9, 83]
        }
    }
```

- pads:

```http

    {
        "pads": [9863, 9872]
    }
```

- regions:

```http

    {
        "regions": [56, 97, 100]
    }
```

- segments:

```http

    {
        "segments": [22679, 22728]
    }
```

- sex:

```http

    {
        "sex": ["male", "female"]
    }
```

- geo (regions):

```http

    {
        "geo": {
            "regions": [56, 97, 100, 188, -70]
        }
    }
```

- geo (local\_geo):

```http

    {
        "geo": {
            "local_geo": {
                "visit_type": "usual",
                "loc_type": ["home", "work"],
                "locations": [{\
                    "lat": 55.75583,\
                    "lng": 37.6173,\
                    "radius": 3000,\
                    "label": "Moscow city center",\
                    "address": "Exact address"\
                }]
            }
        }
    }
```
