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

# SurveyCopy

## /api/v1/lead\\_ads/survey\\_forms/<survey\\_id>/copy

A resource that allows you to create a full copy of a survey.

### POST

Request example:

```http
POST /api/v1/lead_ads/survey_forms/17/copy
{
  "name": "Copy of survey 17" // This field is optional. If omitted, the source survey name will be used.
}
```

Response example:

```http
HTTP 200
{
  "id": 18,
  "status": 1
  ...
}
```

The response contains all fields of [Survey](https://ads.vk.com/en/doc/api/object/Survey).

Possible response codes

- **200** — ad saved
- **404** — survey not found
