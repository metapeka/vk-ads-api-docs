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

# Surveys

## /api/v1/lead\\_ads/survey\\_forms.json

A resource that allows you to create a new survey or retrieve a list of existing surveys.

### GET

Retrieve the list of surveys.

Request example

```http
GET /api/v1/lead_ads/survey_forms.json
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
      "name": "New survey 2022-07-15 17:53"\
      ...\
    },\
    {\
      "id": 105,\
      "name": "New survey 2022-08-16 19:49"\
      ...\
    },\
    {\
      "id": 42303,\
      "name": "New survey 2022-08-16 19:51"\
      ...\
    }\
  ]
}
```

Available fields are described in [SurveysListElement](https://ads.vk.com/en/doc/api/object/SurveysListElement).

The resource supports pagination via the `limit` and `offset` parameters.

- `limit` — number of surveys in the response. Default is 20. Maximum is 50.

```http
/api/v1/lead_ads/survey_forms.json?limit=10
```

- `offset` — offset by N surveys from the beginning of the current result set.

```http
/api/v1/lead_ads/survey_forms.json?limit=5&offset=15
```

Filters

- `_ad_plan_ids` — ad campaign IDs

```http
/api/v1/lead_ads/survey_forms.json?_ad_plan_ids__in=6617841,6711647
```

- `_ad_group_ids` — ad group IDs

```http
/api/v1/lead_ads/survey_forms.json?_ad_group_ids__in=6617841,6711647
```

- `_banner_ids` — ad (banner) IDs

```http
/api/v1/lead_ads/survey_forms.json?_banner_ids__in=6617841,6711647
```

- `q` — string to search surveys. Search is performed by survey name; full word matches are taken into account.

```http
/api/v1/lead_ads/survey_forms.json?q=new
```

Sorting

- `id`

```http
/api/v1/lead_ads/survey_forms.json?sorting=id   - ascending
/api/v1/lead_ads/survey_forms.json?sorting=-id  - descending
```

- `name`

```http
/api/v1/lead_ads/survey_forms.json?sorting=name   - ascending
/api/v1/lead_ads/survey_forms.json?sorting=-name  - descending
```

- `status`

```http
/api/v1/lead_ads/survey_forms.json?sorting=status   - ascending
/api/v1/lead_ads/survey_forms.json?sorting=-status  - descending
```

- `created`

```http
/api/v1/lead_ads/survey_forms.json?sorting=created   - ascending
/api/v1/lead_ads/survey_forms.json?sorting=-created  - descending
```

- `updated`

```http
/api/v1/lead_ads/survey_forms.json?sorting=updated   - ascending
/api/v1/lead_ads/survey_forms.json?sorting=-updated  - descending
```

- `respondents_count`

```http
/api/v1/lead_ads/survey_forms.json?sorting=respondents_count   - ascending
/api/v1/lead_ads/survey_forms.json?sorting=-respondents_count  - descending
```

- `ad_plans_count`

```http
/api/v1/lead_ads/survey_forms.json?sorting=ad_plans_count   - ascending
/api/v1/lead_ads/survey_forms.json?sorting=-ad_plans_count  - descending
```

- multiple fields

```http
/api/v1/lead_ads/survey_forms.json?sorting=status,name,-id
```

Additional flags

- `get_active_form_ad_plans` — a flag indicating whether to return IDs of active `ad_plan`s for surveys. If not specified, they are not returned by default.

```http
/api/v1/lead_ads/survey_forms.json?get_active_form_ad_plans=1
```

### POST

Create a survey. The structure of the survey object is described in [Survey](https://ads.vk.com/en/doc/api/object/Survey).

Request example:

```http
POST /api/v1/lead_ads/survey_forms.json
{
  "name": "Survey from Silicon Valley",
  "first_screen_type": "text",
  "title": "Which \"Silicon Valley\" character are you?",
  "description": "Follow us into the future!",
  "company_title": "Pied Piper",
  "result_info": {
    "positive": {
      "title": "Thank you, now",
      "description": "Follow us into the future",
      "site_url": "http://piedpiper.com.ru/index.html?utm_source=pied_piper&utm_medium=hooli",
      "cta_text": "Go to website"
    }
  },
  "pages": [\
    {\
      "blocks": [\
        {\
          "block_data": {\
            "type": "question",\
            "data": {\
              "is_required": true,\
              "text": "How do you exit Vim?",\
              "type": "multiple_answers",\
              "answers": [\
                { "type": 0, "text": "Ctrl + Alt + Del -> Enter" },\
                { "type": 0, "text": "Turn off the lights and leave" },\
                { "type": 0, "text": "Esc -> :wq" },\
                { "type": 0, "text": "Ctrl + D" },\
                { "type": 0, "text": "Ctrl + X" },\
                { "type": 2, "text": "" }\
              ]\
            }\
          }\
        }\
      ]\
    },\
    {\
      "blocks": [\
        {\
          "block_data": {\
            "type": "question",\
            "data": {\
              "is_required": true,\
              "type": "one_answer",\
              "answers": [\
                { "type": 0, "text": "Tabs for Python developers" },\
                { "type": 0, "text": "Whatever the team lead says" },\
                { "type": 4, "text": "" }\
              ]\
            }\
          }\
        }\
      ]\
    }\
  ],
  "logo_id": "4242eafb-4242-4242-4242-424ec4de4242",
  "gradient": 3
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

When a survey is created, it is assigned the `active` status.

Possible response codes

- **200** — survey saved
- **400** — validation error

Possible error codes:

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
