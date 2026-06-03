# AdPlan

## /api/v2/ad\_plans/(?P<ad\_plan\_id>d+).json

A resource that allows you to retrieve/edit a single ad campaign.

Used object: [AdPlan](https://ads.vk.com/en/doc/api/object/AdPlan)

### GET

Retrieving a single ad campaign

Request example

```http

    GET /api/v2/ad_plans/6617841.json
```

Response example

```http

    {
        "id": 6617841,
        "name": "New campaign 2016-07-15 17:53"
    }
```

Parameters

- fields — list of fields in the response

```http

    /api/v2/ad_plans.json?fields=id,package_id
```

Available fields are described in [AdGroup](https://ads.vk.com/en/doc/api/object/AdGroup).

### POST

Editing an ad campaign

Request example

```http

    POST /api/v2/ad_plans/6617841.json
    {
        "name": "New name"
    }
```

Response example

```http

    HTTP 204
```

Possible response codes

- 200/204 — campaign saved
- 400 — validation error
- 404 — campaign not found

Possible error codes

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
