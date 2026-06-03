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

# LeadForms

## /api/v1/lead\\_ads/lead\\_forms.json

A resource that allows you to create a new lead form or retrieve a list of existing lead forms.

### GET

Retrieve the list of lead forms.

Request example

```http
GET /api/v1/lead_ads/lead_forms.json
```

Response example

```http
{
  "count": 3,
  "offset": 0,
  "limit": 5,
  "items": [\
    {\
      "id": 2523,\
      "name": "New lead form 2022-07-15 17:53"\
      ...\
    },\
    {\
      "id": 105,\
      "name": "New lead form 2022-08-16 19:49"\
      ...\
    },\
    {\
      "id": 42303,\
      "name": "New lead form 2022-08-16 19:51"\
      ...\
    }\
  ]
}
```

Available fields are described in [LeadFormsListElement](https://ads.vk.com/en/doc/api/object/LeadFormsListElement).

The resource supports pagination via the `limit` and `offset` parameters.

- `limit` — number of forms in the response. Default is 20. Maximum is 50.

```http
/api/v1/lead_ads/lead_forms.json?limit=10
```

- `offset` — offset by N forms from the beginning of the current result set.

```http
/api/v1/lead_ads/lead_forms.json?limit=5&offset=15
```

Filters

- `_ad_plan_ids` — ad campaign IDs

```http
/api/v1/lead_ads/lead_forms.json?_ad_plan_ids__in=6617841,6711647
```

- `_ad_group_ids` — ad group IDs

```http
/api/v1/lead_ads/lead_forms.json?_ad_group_ids__in=6617841,6711647
```

- `_banner_ids` — ad (banner) IDs

```http
/api/v1/lead_ads/lead_forms.json?_banner_ids__in=6617841,6711647
```

- `q` — string to search forms. Search is performed by form name; full word matches are taken into account.

```http
/api/v1/lead_ads/lead_forms.json?q=new
```

Sorting

- `id`

```http
/api/v1/lead_ads/lead_forms.json?sorting=id   - ascending
/api/v1/lead_ads/lead_forms.json?sorting=-id  - descending
```

- `name`

```http
/api/v1/lead_ads/lead_forms.json?sorting=name   - ascending
/api/v1/lead_ads/lead_forms.json?sorting=-name  - descending
```

- `status`

```http
/api/v1/lead_ads/lead_forms.json?sorting=status   - ascending
/api/v1/lead_ads/lead_forms.json?sorting=-status  - descending
```

- `created`

```http
/api/v1/lead_ads/lead_forms.json?sorting=created   - ascending
/api/v1/lead_ads/lead_forms.json?sorting=-created  - descending
```

- `updated`

```http
/api/v1/lead_ads/lead_forms.json?sorting=updated   - ascending
/api/v1/lead_ads/lead_forms.json?sorting=-updated  - descending
```

- `leads_count`

```http
/api/v1/lead_ads/lead_forms.json?sorting=leads_count   - ascending
/api/v1/lead_ads/lead_forms.json?sorting=-leads_count  - descending
```

- `ad_plans_count`

```http
/api/v1/lead_ads/lead_forms.json?sorting=ad_plans_count   - ascending
/api/v1/lead_ads/lead_forms.json?sorting=-ad_plans_count  - descending
```

- multiple fields

```http
/api/v1/lead_ads/lead_forms.json?sorting=status,name,-id
```

Additional flags

- `get_active_form_ad_plans` — a flag indicating whether to return IDs of active `ad_plan`s for forms. If not specified, they are not returned by default.

```http
/api/v1/lead_ads/lead_forms.json?get_active_form_ad_plans=1
```

* * *

### POST

Create a lead form.

Request example:

```http
POST /api/v1/lead_ads/lead_forms.json
{
  "name": "My first lead form",
  "company_title": "VKontakte",
  "logo_id": "96a871b5-04c7-45b0-9a8d-565f65bd14c5",
  "contact_fields": [\
    "first_name",\
    "phone"\
  ],
  "result_info": {
    "title": "Thank you!",
    "description": "Your request has been successfully submitted!",
    "site_url": "https://mail.ru",
    "phone": "+78008005555"
  },
  "agreement": {
    "usage": "template_document",
    "template_document": {
      "company_title": "VK",
      "registration_address": "Leningradsky Avenue, 39"
    }
  }
}
```

Response example:

```http
HTTP 200
{
  "id": 9826424
  ...
}
```

When a form is created, it is assigned the `active` status.

Possible response codes

- `200` — form saved
- `400` — validation error

Possible error codes:

- `bad_value` — invalid value format or type
- `required` — field is required
- `required_value` — a required value is expected
- `unallowed_value` — value is not in the list of allowed values
- `bad_items` — the list contains invalid values
- `max_value` — string/list length/size exceeds the maximum
- `min_value` — string/list length/size is below the minimum
- `duplicate_value` — the list contains duplicate values
- `bad_contact_field_value` — the provided list of contact fields does not contain all required values

In general, an error message has the following format:

```http
{
  "error": {
    "fields": {
      "<field_name_1>": {
        "message": "<error_message_1>",
        "code": "<error_code_1>"
      },
      "<field_name_2>": {
        "message": "<error_message_2>",
        "code": "<error_code_2>"
      }
    },
    "message": "Validation failed",
    "code": "validation_failed"
  }
}
```

where `field_name_N` is the name of the field where the error occurred, `error_message_N` is the error description, and `error_code_N` is the error code.

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
