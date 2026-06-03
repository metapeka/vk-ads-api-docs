# MobileApps

## /api/v1/mobile\_app\_users.json

A resource that provides information about applications available to the user.

Used object: [MobileApps](https://ads.vk.com/en/doc/api/object/MobileApps)

### GET

The request returns data about available mobile applications.

Request example:

```http

  GET /api/v1/mobile_app_users.json?fields=app_name,platform,url,url_object_id,users,rb_mobile_app_id,campaign_ids,preview_url,sk_ad_network_ids,category_id&limit=50
```

Response example:

```http

{
    "count": 1,
    "items": [\
        {\
            "app_name": "Application name",\
            "campaign_ids": [\
                123456\
            ],\
            "platform": "iOS",\
            "preview_url": "http://domain/image/path.png",\
            "rb_mobile_app_id": 1234567,\
            "category_id": 1234,\
            "sk_ad_network_ids": {\
                "available": 66,\
                "inherited_available": 0,\
                "inherited_total": 0,\
                "inherited_used": 0,\
                "total": 67,\
                "used": 1\
            },\
            "url": "https://apps.apple.com/ru/app/id123456789",\
            "url_object_id": "12345",\
            "users": [\
                {\
                    "allowed_access": [\
                        "statistics",\
                        "segments",\
                        "lookalike"\
                    ],\
                    "sk_ad_network_ids": {\
                        "available": 66,\
                        "inherited_available": 0,\
                        "inherited_total": 0,\
                        "inherited_used": 0,\
                        "total": 67,\
                        "used": 1\
                    },\
                    "status": "approved",\
                    "type": "master",\
                    "user": {\
                        "additional_info": {\
                            "email": "app_owner@example.com",\
                            "name": ""\
                        },\
                        "agency_user": null,\
                        "firstname": "",\
                        "id": 123456,\
                        "lastname": "",\
                        "username": "app_owner@example.com"\
                    }\
                },\
                {\
                    "allowed_access": [\
                        "segments",\
                        "lookalike",\
                        "statistics"\
                    ],\
                    "sk_ad_network_ids": {\
                        "available": 27,\
                        "inherited_available": 0,\
                        "inherited_total": 0,\
                        "inherited_used": 0,\
                        "total": 27,\
                        "used": 0\
                    },\
                    "status": "approved",\
                    "type": "slave",\
                    "user": {\
                        "additional_info": {\
                            "email": "app_ad_agent@example.com",\
                            "name": "Somebody"\
                        },\
                        "agency_user": null,\
                        "firstname": "",\
                        "id": 12345678,\
                        "lastname": "",\
                        "username": "app_ad_agent@example.com"\
                    }\
                },\
            ]\
        }\
    ],\
    "limit": 50,\
    "offset": 0
}
```

The response contains an "items" array consisting of [MobileApps](https://ads.vk.com/en/doc/api/object/MobileApps) objects.
