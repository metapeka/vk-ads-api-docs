# Banner

## /api/v2/banners/<banner\_id>.json

A resource that allows you to retrieve, update, and delete ads.

Used object: [Banner](https://ads.vk.com/en/doc/api/object/Banner)

### GET

Retrieving a single ad

Request example

```http

    GET /api/v2/banners/23617841.json
```

Response example

```http

    {
        "id": 23826937
        "ad_group": 9367343
    }
```

### POST

Editing an ad

Request example

```http

    POST /api/v2/banners/23826937.json
    {
        "status": "blocked"
    }
```

Response example

```http

    HTTP 204
```

The contents of the urls, textblocks, and content sections are fully replaced on update. For example, for a banner with content:

```http

    {
        "content": {
            "logo_image": {
                "id": 83465432
            },
            "promo_image": {
                "id": 90465432
            },
            "tpl_background_image": {
                "id": 86342123
            }
        }
    }
```

the update request:

```http

    {
        "content": {
            "logo_image": {
                "id": 83465432
            },
            "promo_image": {
                "id": 88278634
            },
            "tpl_background_image_300": {
                "id": 72934723
            }
        }
    }
```

will result in exactly this new content section after the update.

Possible response codes

- 200/204 — ad saved
- 400 — validation error
- 404 — ad not found

Possible error codes

- active\_banners\_limit — the limit of active banners for the user has been exceeded
- deleted\_banner — a deleted banner cannot be modified
- bad\_width — invalid content width value
- bad\_height — invalid content height value
- bad\_size — maximum content size exceeded
- bad\_type — invalid content type
- bad\_length — content has an invalid playback duration
- bad\_bitrate — content has an invalid bitrate
- dynamic\_content — dynamic content is used in an invalid role
- custom\_params — invalid video parameters
- exclamation\_signs\_limit — exclamation marks limit exceeded in the banner text block
- invalid\_macros — a disallowed macro is used in the banner text block
- persistent\_urls — changing URLs is not allowed in the package
- one\_url\_object\_id — URLs leading to different objects are not allowed in the package
- ad\_group\_one\_url — different URLs are not allowed in the package
- url\_not\_checked — using unchecked URLs is not allowed
- url\_not\_valid — the URL does not match the specified role
- max\_value — value is greater than the maximum
- min\_value — value is less than the minimum
- bad\_value — invalid value format or type
- required — field is required
- unallowed\_value — value is not in the list of allowed values
- bad\_items — the list contains invalid values
- unallowed\_field — field is not allowed
- read\_only\_field — updating a non-editable field

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
                "call_to_action": {
                    "message": "Unallowed value",
                    "code": "unallowed_value"
                }
            },
            "message": "Validation failed",
            "code": "validation_failed"
        }
    }
```

### DELETE

Deleting an ad

Request example

```http

    DELETE /api/v2/banners/23617841.json
```

Response example

```http

    HTTP 204
```

Possible response codes

- 204 — ad deleted
- 404 — ad not found
