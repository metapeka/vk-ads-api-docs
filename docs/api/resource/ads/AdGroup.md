# AdGroup

## /api/v2/ad\_groups/<ad\_group\_id>.json

A resource that allows you to retrieve/edit a single ad group.

### GET

Retrieving a single ad group

Request example

```http

    GET /api/v2/ad_groups/6617841.json
```

Response example

```http

    {
        "id": 6617841,
        "name": "New ad group 2022-07-15 17:53",
        "package_id": 83
    }
```

Parameters

- fields — list of fields in the response

```http

    /api/v2/ad_groups.json?fields=id,package_id
```

Available fields are described in [AdGroup](https://ads.vk.com/en/doc/api/object/AdGroup).

### POST

Editing an ad group

Request example

```http

    POST /api/v2/ad_groups/6617841.json
    {
        "name": "New name"
    }
```

Response example

```http

    HTTP 204
```

Possible response codes

- 200/204 — group saved
- 400 — validation error
- 404 — group not found

Possible error codes

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
- recommended\_not\_available — the `recommended` strategy is not available. You must set either the total budget and the broadcast period, or the group daily budget

### DELETE

Deleting an ad group

Request example

```http

    DELETE /api/v2/ad_groups/6617841.json
```

Response example

```http

    HTTP 204
```
