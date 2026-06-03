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

# LeadFormCopy

## /api/v1/lead\\_ads/lead\\_forms/<lead\\_form\\_id>/copy

A resource that allows you to create a full copy of a lead form.

### POST

Request example:

```http
POST /api/v1/lead_ads/lead_forms/17/copy
{
  "name": "Copy of lead form 17" // This field is optional. If omitted, the source lead form name will be used.
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

The response contains all fields of [LeadForm](https://ads.vk.com/en/doc/api/object/LeadForm).

Possible response codes

- **200** — ad saved
- **404** — lead form not found
