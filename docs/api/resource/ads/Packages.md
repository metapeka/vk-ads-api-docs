# Packages

## /api/v2/packages.json

The resource enables you to collect data on packages.
A package is a set of service parameters applied to the campaigns you create; for example, available targeting configurations or range of sites where the ads will be displayed. Package is a must for creating an ad campaign.

Used object: [Package](https://ads.vk.com/en/doc/api/object/Package)

### GET

Request example:

```http

   GET /api/v2/packages.json
```

Response example:

```http

    {
        "items": [\
            {\
                "status": "blocked",\
                "max_uniq_shows_limit": 31,\
                "priced_event_type": 0,\
                "description": "(x) Odnoklassniki: external links, impressions",\
                "created": "2011-07-26 10:22:57",\
                "price": "0.006",\
                "updated": "2017-03-16 23:19:47",\
                "banner_format_id": 1,\
                "url_type": null,\
                "flags": [\
                    "teasers",\
                    "external"\
                ],\
                "related_package_ids": [ ],\
                "max_price_per_unit": "120",\
                "id": 16,\
                "name": "odkl_ext",\
                "objective": [ ]\
            },\
            {\
                "status": "active",\
                "max_uniq_shows_limit": 0,\
                "priced_event_type": 1,\
                "paid_event_type": 1,\
                "description": "Mobile advertising",\
                "created": "2016-11-30 14:50:02",\
                "price": "1.5",\
                "updated": "2017-05-29 18:38:36",\
                "banner_format_id": 113,\
                "url_type": null,\
                "flags": [\
                    "mobile_feed",\
                    "sync_url_check",\
                    "mobile_stats",\
                    "external",\
                    "soft_limit",\
                    "set_mobile_category",\
                    "extended_age_targetings"\
                ],\
                "related_package_ids": [\
                    382\
                ],\
                "max_price_per_unit": "120",\
                "id": 381,\
                "name": "tt_mobile_app_promo1080x607_all_android_cpc_multiformat_new",\
                "objective": [\
                   "reach",\
                   "traffic",\
                   "storevisits"\
                ]\
            }\
       ]
   }
```
