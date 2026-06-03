# BannerRemoderation

## /api/v2/banners/remoderate.json

A resource that allows you to submit a banner for re-moderation.

### POST

Request example:

```http

   POST /api/v2/banners/remoderate.json?fields=id,remoderated

    {
        "banners": [\
            {\
                "id": 1527521\
            },\
            {\
                "id": 6543425\
            }\
        ]
    }
```

Response example:

```http

    {
        "banners": [\
            {\
                "id": 1527521,\
                "remoderated": False\
            },\
            {\
                "id": 6543425,\
                "remoderated": True\
            }\
        ]
    }
```

The response contains the `remoderated` field, which indicates whether the re-moderation request was successful.

Please note that not all banners can be submitted for re-moderation.

To find out which banners can be submitted for re-moderation, request the [Banners API](https://ads.vk.com/en/doc/api/resource/Banners) with the `id` and `user_can_request_remoderation` fields. If `user_can_request_remoderation = True`, the banner can be submitted for re-moderation.
