Information

Resources

Audiences and data sources

Users

Dictionaries

Ads

Finance

Lead forms

[LeadForm](https://ads.vk.com/en/doc/api/resource/LeadForm) [LeadForms](https://ads.vk.com/en/doc/api/resource/LeadForms) [LeadFormArchivation](https://ads.vk.com/en/doc/api/resource/LeadFormArchivation) [LeadFormUnarchivation](https://ads.vk.com/en/doc/api/resource/LeadFormUnarchivation) [LeadFormLeadsExport](https://ads.vk.com/en/doc/api/resource/LeadFormLeadsExport) [LeadFormImage](https://ads.vk.com/en/doc/api/resource/LeadFormImage) [Leads](https://ads.vk.com/en/doc/api/resource/Leads) [TestLeadSending](https://ads.vk.com/en/doc/api/resource/TestLeadSending) [LeadFormCopy](https://ads.vk.com/en/doc/api/resource/LeadFormCopy)

Subscriptions

Surveys

Objects

# LeadForm

## /api/v1/lead\\_ads/lead\\_forms/<lead\\_form\\_id>.json

A resource that allows you to retrieve and update lead forms.

### GET

Retrieving a single lead form

Request example

```http

    GET /api/v1/lead_ads/lead_forms/17.json
```

Response example

```http

    {
        "id": "17",
        "name": "My first lead form"
    }
```

Available fields are described in [LeadForm](https://ads.vk.com/en/doc/api/object/LeadForm).

Parameters

- get\\_active\\_form\\_ad\\_plans — a flag indicating whether to return the IDs of active ad\\_plans for the form. If not specified, they are not returned by default.

```http

    /api/v1/lead_ads/lead_forms/17.json?get_active_form_ad_plans=1
```

### POST

Editing a lead form

Request example

```http

    POST /api/v1/lead_ads/lead_forms/17.json
    {
        "name": "VK Ads. Updated lead form"
    }
```

Response example

```http

    HTTP 200
    {
        "id": "17",
        "name": "VK Ads. Updated lead form",
        ...
    }
```

The contents of the contact\\_fields, result\\_info, agreement, notifications, and pages sections are fully replaced on update. For example, for a lead form with contact\\_fields:

```http

    {
        "contact_fields": [\
            "first_name",\
            "phone",\
            "city"\
        ],
    }
```

the update request:

```http

    {
        "contact_fields": [\
            "first_name",\
            "phone",\
            "birth_date"\
        ],
    }
```

will result in exactly this new contact\\_fields section after the update.

Possible response codes

- 200 — lead form saved
- 400 — validation error
- 404 — lead form not found

Possible error codes

- bad\\_value — invalid value format or type
- required — field is required
- required\\_value — a required value is expected
- unallowed\\_value — value is not in the list of allowed values
- bad\\_items — the list contains invalid values
- max\\_value — string/list length/size is greater than the maximum
- min\\_value — string/list length/size is less than the minimum
- duplicate\\_value — the list contains duplicate values
- bad\\_contact\\_field\\_value — the provided list of contact fields does not contain all required values

In general, an error message has the following format:

```http

    {
        "error": {
            "fields": {
                "<field_name_1\\>": {
                    "message": "<error_message_1\\>",
                    "code": "<error_code_1\\>"
                },
                "<field_name_2\\>": {
                    "message": "<error_message_2\\>",
                    "code": "<error_code_2\\>"
                }
            },
            "message": "Validation failed",
            "code": "validation_failed"
        }
    }
```

where field\\_name\\_N is the name of the field where the error occurred, error\\_message\\_N is the error description, and error\\_code\\_N is the error code.

Example:

```http

    {
        "error": {
            "fields": {
                "contact_fields": {
                    "message": "Provided contact fields do not contain required values",
                    "code": "bad_contact_field_value"
                }
            },
            "message": "Validation failed",
            "code": "validation_failed"
        }
    }
```
