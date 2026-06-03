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

# LeadFormLeadsExport

## /api/v1/lead\\_ads/lead\\_forms/<lead\\_form\\_id>/leads.<export\\_format>

A resource that allows you to retrieve the collected data of leads who have submitted the form. Currently, the following export formats are available:

- csv
- xlsx

### GET

Request example

```http
GET /api/v1/lead_ads/lead_forms/17/leads.csv
```

Response example

```http
HTTP 200
"Campaign ID","Group ID","Ad ID","Lead time","Name","Phone","Do you have a pet?"
"1","3","2","2022-12-08 21:41:03.922 +0000 UTC","Victor","+78008005555","Yes"
```

Filters

- `_created_at` — lead received date and time. Available constraints: `lte` (less than or equal), `gte` (greater than or equal).

```http
/api/v1/lead_ads/lead_forms/17/leads.csv?_created_at__lte=2022-01-01%2000:00:00
/api/v1/lead_ads/lead_forms/17/leads.csv?_created_at__gte=2022-01-01%2000:00:00
```

- `_ad_plan_id` — ad campaign IDs

```http
/api/v1/lead_ads/lead_forms/17/leads.csv?_ad_plan_id__in=6617841,6711647
```

- `_ad_group_id` — ad group IDs

```http
/api/v1/lead_ads/lead_forms/17/leads.csv?_ad_group_id__in=6617841,6711647
```

- `_banner_id` — ad (banner) IDs

```http
/api/v1/lead_ads/lead_forms/17/leads.csv?_banner_id__in=6617841,6711647
```

Possible response codes

- **200** — ad saved
- **404** — lead form not found
