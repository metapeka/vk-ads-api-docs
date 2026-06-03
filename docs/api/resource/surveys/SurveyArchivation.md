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

# SurveyArchivation

## /api/v1/lead\\_ads/survey\\_forms/archive

A resource that allows you to archive a survey.

### POST

Request example:

```http
POST /api/v1/lead_ads/survey_forms/archive?_form_ids__in=43,3952,552
```

Response example:

```http
HTTP 200
[\
  {\
    "id": 43,\
    "status": 2\
    ...\
  },\
  {\
    "id": 3952,\
    "status": 2\
    ...\
  },\
  {\
    "id": 552,\
    "status": 2\
    ...\
  }\
]
```

The response contains all fields of [Survey](https://ads.vk.com/en/doc/api/object/Survey).

Note that archiving can succeed only if all specified surveys exist and are not currently archived.

Possible response codes

- **200** — ad saved
- **404** — survey not found
