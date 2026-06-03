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

# TestLeadSending

## /api/v1/lead\\_ads/lead\\_forms/<lead\\_form\\_id>/send\\_test\\_lead

A resource that allows you to send a test lead for the specified form.

### POST

Send a test lead.

Request example

```http
POST /api/v1/lead_ads/lead_forms/10/send_test_lead
```

Response example

```http
{
  "is_operation_processed": true,
  "message": "test lead was successfully sent",
  "seconds_before_next_sending": 5
}
```

In the response, the `is_operation_processed` field indicates whether the lead was sent. The `message` field duplicates this information in text form.

Regardless of the other fields, `seconds_before_next_sending` contains the number of seconds until the next allowed sending.
