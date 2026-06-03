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

# SurveyRespondentsExport

## /api/v1/lead\\_ads/survey\\_forms/<survey\\_id>/respondents.xlsx

A resource that allows you to retrieve the collected data of respondents who completed the survey. Currently, export is available only in the xlsx file format.

### GET

Request example

```http
GET /api/v1/lead_ads/survey_forms/17/respondents.xlsx
```

Filters

- `_created_at` — date and time when the respondent's answer was received. Available constraints: `lte` (less than or equal), `gte` (greater than or equal).

```http
/api/v1/lead_ads/survey_forms/17/respondents.xlsx?_created_at__lte=2022-01-01%2000:00:00
/api/v1/lead_ads/survey_forms/17/respondents.xlsx?_created_at__gte=2022-01-01%2000:00:00
```

- `_ad_plan_id` — ad campaign IDs

```http
/api/v1/lead_ads/survey_forms/17/respondents.xlsx?_ad_plan_id__in=6617841,6711647
```

- `_ad_group_id` — ad group IDs

```http
/api/v1/lead_ads/survey_forms/17/respondents.xlsx?_ad_group_id__in=6617841,6711647
```

- `_banner_id` — ad (banner) IDs

```http
/api/v1/lead_ads/survey_forms/17/respondents.xlsx?_banner_id__in=6617841,6711647
```

Possible response codes

- **200** — ad saved
- **404** — survey not found
