Information

Resources

Audiences and data sources

Users

Dictionaries

Ads

Finance

Lead forms

Subscriptions

Surveys

[Surveys](https://ads.vk.com/en/doc/api/resource/Surveys) [Survey](https://ads.vk.com/en/doc/api/resource/Survey) [SurveyArchivation](https://ads.vk.com/en/doc/api/resource/SurveyArchivation) [SurveyUnarchivation](https://ads.vk.com/en/doc/api/resource/SurveyUnarchivation) [SurveyRespondentsExport](https://ads.vk.com/en/doc/api/resource/SurveyRespondentsExport) [Respondents](https://ads.vk.com/en/doc/api/resource/Respondents) [SurveyCopy](https://ads.vk.com/en/doc/api/resource/SurveyCopy)

Objects

# Survey

## /api/v1/lead\\_ads/survey\\_forms/<survey\\_id>.json

A resource that allows you to retrieve and update surveys.

### GET

Retrieve a single survey.

Request example

```http
GET /api/v1/lead_ads/survey_forms/17.json
```

Response example

```http
{
  "id": "17",
  "name": "My first survey"
}
```

Available fields are described in [Survey](https://ads.vk.com/en/doc/api/object/Survey).

Parameters

- `get_active_form_ad_plans` — a flag indicating whether to return IDs of active `ad_plan`s for the survey. If not specified, they are not returned by default.

```http
/api/v1/lead_ads/survey_forms/17.json?get_active_form_ad_plans=1
```

### POST

Edit a survey. Available fields are described in [Survey](https://ads.vk.com/en/doc/api/object/Survey).

Request example

```http
POST /api/v1/lead_ads/survey_forms/17.json
{
  "name": "VK Ads. Updated survey"
}
```

Response example

```http
HTTP 200
{
  "id": "17",
  "name": "VK Ads. Updated survey",
  ...
}
```

The contents of the `result_info` and `pages` sections are fully replaced on update.

Possible response codes

- **200** — ad saved
- **400** — validation error
- **404** — survey not found

Possible error codes

- `bad_value` — invalid value format or type
- `required` — field is required
- `required_value` — a required value is expected
- `unallowed_value` — value is not in the list of allowed values
- `bad_items` — the list contains invalid values
- `max_value` — string/list length/size exceeds the maximum
- `min_value` — string/list length/size is below the minimum
- `duplicate_value` — the list contains duplicate values

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
      "field": {
        "message": "Bad items",
        "code": "bad_items"
      }
    },
    "message": "Validation failed",
    "code": "validation_failed"
  }
}
```
