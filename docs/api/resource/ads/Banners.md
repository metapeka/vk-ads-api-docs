# Banners

## /api/v2/banners.json

A resource that allows you to retrieve a list of all ads of the user. Banners are created using the [CampaignBanners](https://ads.vk.com/en/doc/api/resource/CampaignBanners) resource.

Used object: [Banner](https://ads.vk.com/en/doc/api/object/Banner)

### GET

Retrieving a list of ads

Request example

```http

    GET /api/v2/banners.json
```

Response example

```http

    {
        "count": 3,
        "offset": 0,
        "items": [\
            {\
                "id": 23826937\
                "campaign_id": 9367343\
            },\
            {\
                "id": 23826938\
                "campaign_id": 9367343\
            },\
            {\
                "id": 24582643\
                "campaign_id": 9401602\
            }\
        ]
    }
```

The resource supports pagination using the limit and offset parameters.

- limit — number of objects in the response. Default: 20

```http

    GET /api/v2/banners.json?limit=10
```

- offset — shift by N objects from the beginning of the current selection

```http

    GET /api/v2/banners.json?limit=5&offset=15
```

Filters

- \_id — ad ID

```http

    /api/v2/banners.json?_id=26617841
    /api/v2/banners.json?_id__in=26617841,26711647
```

- \_campaign\_id — ad campaign ID

```http

    /api/v2/banners.json?_campaign_id=6617841
    /api/v2/banners.json?_campaign_id__in=6617841,6711647
```

- \_campaign\_status — ad campaign status. Available statuses: "active", "blocked", "deleted"

```http

    /api/v2/banners.json?_campaign_status=active
    /api/v2/banners.json?_campaign_status__ne=active
    /api/v2/banners.json?_campaign_status__in=active,blocked
```

- \_status — ad status. Available statuses: "active", "blocked", "deleted"

```http

    /api/v2/banners.json?_status=active
    /api/v2/banners.json?_status__ne=active
    /api/v2/banners.json?_status__in=active,blocked
```

- \_updated — datetime of the last ad update. Available lookups: "lt" (less than), "lte" (less than or equal), "gt" (greater than), "gte" (greater than or equal)

```http

    /api/v2/banners.json?_updated__gt=2018-01-01 00:00:00
    /api/v2/banners.json?_updated__gte=2018-01-01 00:00:00
    /api/v2/banners.json?_updated__lt=2018-01-01 00:00:00
    /api/v2/banners.json?_updated__lte=2018-01-01 00:00:00
```

- \_url — full-text case-sensitive search by banner URLs

```http

    /api/v2/banners.json?_url=mail.ru
```

- \_textblock — full-text case-sensitive search by the contents of the banner text blocks

```http

    /api/v2/banners.json?_textblock=buy a pump
```
