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

# Leads

## /api/v1/lead\\_ads/leads.json

A resource that allows you to retrieve a list of received leads.

### GET

Retrieve the list of leads.

Request example

```http
GET /api/v1/lead_ads/leads.json
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
      "form_name": "New lead form 2022-07-15 17:53"\
      ...\
    },\
    {\
      "id": 105,\
      "form_name": "New lead form 2022-08-16 19:49"\
      ...\
    },\
    {\
      "id": 42303,\
      "form_name": "New lead form 2022-08-16 19:51"\
      ...\
    }\
  ]
}
```

Available fields are described in [LeadsListElement](https://ads.vk.com/en/doc/api/object/LeadsListElement).

The resource supports pagination via the `limit` and `offset` parameters.

- `limit` — number of leads in the response. Default is 20. Maximum is 50.

```http
/api/v1/lead_ads/leads.json?limit=10
```

- `offset` — offset by N leads from the beginning of the current result set.

```http
/api/v1/lead_ads/leads.json?limit=5&offset=15
```

Filters

- `_form_ids` — lead form IDs

```http
/api/v1/lead_ads/leads.json?_form_ids__in=6617841,6711647
```

- `_ad_plan_ids` — ad campaign IDs

```http
/api/v1/lead_ads/leads.json?_ad_plan_ids__in=6617841,6711647
```

- `_ad_group_ids` — ad group IDs

```http
/api/v1/lead_ads/leads.json?_ad_group_ids__in=6617841,6711647
```

- `_banner_ids` — ad (banner) IDs

```http
/api/v1/lead_ads/leads.json?_banner_ids__in=6617841,6711647
```

- `_created_at` — lead received date and time. Available constraints: `lte` (less than or equal), `gte` (greater than or equal).

```http
/api/v1/lead_ads/leads.json?_created_at__lte=2022-01-01%2000:00:00
/api/v1/lead_ads/leads.json?_created_at__gte=2022-01-01%2000:00:00
```

Sorting

- `id`

```http
/api/v1/lead_ads/leads.json?sorting=id   - ascending
/api/v1/lead_ads/leads.json?sorting=-id  - descending
```

- `form_id`

```http
/api/v1/lead_ads/leads.json?sorting=form_id   - ascending
/api/v1/lead_ads/leads.json?sorting=-form_id  - descending
```

- `form_name`

```http
/api/v1/lead_ads/leads.json?sorting=form_name   - ascending
/api/v1/lead_ads/leads.json?sorting=-form_name  - descending
```

- `ad_plan_id`

```http
/api/v1/lead_ads/leads.json?sorting=ad_plan_id   - ascending
/api/v1/lead_ads/leads.json?sorting=-ad_plan_id  - descending
```

- `ad_group_id`

```http
/api/v1/lead_ads/leads.json?sorting=ad_group_id   - ascending
/api/v1/lead_ads/leads.json?sorting=-ad_group_id  - descending
```

- `banner_id`

```http
/api/v1/lead_ads/leads.json?sorting=banner_id   - ascending
/api/v1/lead_ads/leads.json?sorting=-banner_id  - descending
```

- `created_at`

```http
/api/v1/lead_ads/leads.json?sorting=created_at   - ascending
/api/v1/lead_ads/leads.json?sorting=-created_at  - descending
```

- multiple fields

```http
/api/v1/lead_ads/leads.json?sorting=created_at,form_name,-id
```
