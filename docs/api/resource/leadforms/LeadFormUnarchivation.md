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

# LeadFormUnarchivation

## /api/v1/lead\\_ads/lead\\_forms/unarchive

A resource that allows you to move a lead form back from the archive.

### POST

Request example:

```http

   POST /api/v1/lead_ads/lead_forms/unarchive?_form_ids__in=43,3952,552
```

Response example:

```http
    HTTP 200
    [\
        {\
            "id": 43,\
            "status": 1\
            ...\
        },\
        {\
            "id": 3952,\
            "status": 1\
            ...\
        },\
        {\
            "id": 552,\
            "status": 1\
            ...\
        }\
    ]

```

The response contains all fields of [LeadForm](https://ads.vk.com/en/doc/api/object/LeadForm).

Please note that unarchiving can succeed only if all specified forms exist and are currently archived.

Possible response codes

- 200 — lead form saved
- 404 — lead form not found
