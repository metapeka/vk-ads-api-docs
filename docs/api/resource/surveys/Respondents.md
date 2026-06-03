# Respondents

## /api/v1/lead\\_ads/respondents.json

A resource that allows you to retrieve a list of received respondents.

### GET

Retrieve the list of respondents.

Request example

```http
GET /api/v1/lead_ads/respondents.json
```

Response example

```http
{
  "count": 3,
  "offset": 0,
  "limit": 0,
  "items": [\
    {\
      "id": 2523,\
      "form_name": "New survey 2022-07-15 17:53"\
      ...\
    },\
    {\
      "id": 105,\
      "form_name": "New survey 2022-08-16 19:49"\
      ...\
    },\
    {\
      "id": 42303,\
      "form_name": "New survey 2022-08-16 19:51"\
      ...\
    }\
  ]
}
```

Available fields are described in [RespondentsListElement](https://ads.vk.com/en/doc/api/object/RespondentsListElement).

The resource supports pagination via the `limit` and `offset` parameters.

- `limit` — number of respondents in the response. Default is 20. Maximum is 50.

```http
/api/v1/lead_ads/respondents.json?limit=10
```

- `offset` — offset by N respondents from the beginning of the current result set.

```http
/api/v1/lead_ads/respondents.json?limit=5&offset=15
```

Filters

- `_form_ids` — survey IDs

```http
/api/v1/lead_ads/respondents.json?_form_ids__in=6617841,6711647
```

- `_ad_plan_ids` — ad campaign IDs

```http
/api/v1/lead_ads/respondents.json?_ad_plan_ids__in=6617841,6711647
```

- `_ad_group_ids` — ad group IDs

```http
/api/v1/lead_ads/respondents.json?_ad_group_ids__in=6617841,6711647
```

- `_banner_ids` — ad (banner) IDs

```http
/api/v1/lead_ads/respondents.json?_banner_ids__in=6617841,6711647
```

- `_created_at` — respondent received date and time. Available constraints: `lte` (less than or equal), `gte` (greater than or equal).

```http
/api/v1/lead_ads/respondents.json?_created_at__lte=2022-01-01%2000:00:00
/api/v1/lead_ads/respondents.json?_created_at__gte=2022-01-01%2000:00:00
```

Sorting

- `id`

```http
/api/v1/lead_ads/respondents.json?sorting=id   - ascending
/api/v1/lead_ads/respondents.json?sorting=-id  - descending
```

- `survey_id`

```http
/api/v1/lead_ads/respondents.json?sorting=survey_id   - ascending
/api/v1/lead_ads/respondents.json?sorting=-survey_id  - descending
```

- `survey_name`

```http
/api/v1/lead_ads/respondents.json?sorting=survey_name   - ascending
/api/v1/lead_ads/respondents.json?sorting=-survey_name  - descending
```

- `ad_plan_id`

```http
/api/v1/lead_ads/respondents.json?sorting=ad_plan_id   - ascending
/api/v1/lead_ads/respondents.json?sorting=-ad_plan_id  - descending
```

- `ad_group_id`

```http
/api/v1/lead_ads/respondents.json?sorting=ad_group_id   - ascending
/api/v1/lead_ads/respondents.json?sorting=-ad_group_id  - descending
```

- `banner_id`

```http
/api/v1/lead_ads/respondents.json?sorting=banner_id   - ascending
/api/v1/lead_ads/respondents.json?sorting=-banner_id  - descending
```

- `created_at`

```http
/api/v1/lead_ads/respondents.json?sorting=created_at   - ascending
/api/v1/lead_ads/respondents.json?sorting=-created_at  - descending
```

- multiple fields

```http
/api/v1/lead_ads/respondents.json?sorting=created_at,survey_name,-id
```
