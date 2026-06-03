# BannerPatterns

## /api/v2/banner\_patterns.json

Pattern registry

Used object: [BannerPattern](https://ads.vk.com/en/doc/api/object/BannerPattern)

### GET

Request example:

```http

   GET /api/v2/banner_patterns.json
```

Response example:

```http
  {
    "count": 137,
    "items": [\
      {\
        "description": "Teaser for games in MM, 90x70, image only",\
        "format": [\
          {\
            "field": "url",\
            "required": true,\
            "role": "primary"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "image_90x70"\
          }\
        ],\
        "id": 41,\
        "interface": {},\
        "name": "games_teaser_90x70",\
        "status": "active"\
      },\
      {\
        "description": "Teaser for games in MM, 90x70, image + title",\
        "format": [\
          {\
            "field": "url",\
            "required": true,\
            "role": "primary"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "title_25"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "image_90x70"\
          }\
        ],\
        "id": 42,\
        "interface": {},\
        "name": "teaser_90x70_with_title",\
        "status": "active"\
      },\
      {\
        "description": "Teaser for games in MM, 143x113 image + title",\
        "format": [\
          {\
            "field": "url",\
            "required": true,\
            "role": "primary"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "title_25"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "image_143x113"\
          }\
        ],\
        "id": 43,\
        "interface": {},\
        "name": "teaser_143x113_with_title",\
        "status": "active"\
      },\
      {\
        "description": "Multiformat with a landscape image for MM games",\
        "format": [\
          {\
            "field": "url",\
            "required": true,\
            "role": "primary"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "title_25"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "text_90"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "cta_games"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "image_1080x607"\
          }\
        ],\
        "id": 44,\
        "interface": {},\
        "name": "multiformat_landscape_img_games",\
        "status": "active"\
      },\
      {\
        "description": "Multiformat, landscape image, no text, apps",\
        "format": [\
          {\
            "field": "url",\
            "required": true,\
            "role": "primary"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "title_25"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "cta_apps_full"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "image_1080x607"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "icon_300x300_app"\
          }\
        ],\
        "id": 45,\
        "interface": {},\
        "name": "multiformat_landscape_img_notext_app",\
        "status": "active"\
      },\
      {\
        "description": "Multiformat, landscape image, no icon, apps",\
        "format": [\
          {\
            "field": "url",\
            "required": true,\
            "role": "primary"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "title_25"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "text_90"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "cta_apps_full"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "image_1080x607"\
          }\
        ],\
        "id": 46,\
        "interface": {},\
        "name": "multiformat_landscape_img_noicon_app",\
        "status": "active"\
      },\
      {\
        "description": "Multiformat, landscape image, no text, no icon, apps",\
        "format": [\
          {\
            "field": "url",\
            "required": true,\
            "role": "primary"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "title_25"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "image_1080x607"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "cta_apps_full"\
          }\
        ],\
        "id": 47,\
        "interface": {\
          "projectionFactor": 0.04\
        },\
        "name": "multiformat_landscape_img_notext_noicon_app",\
        "status": "active"\
      },\
      {\
        "description": "Teasers with an app icon, with CTA",\
        "format": [\
          {\
            "field": "url",\
            "required": true,\
            "role": "primary"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "title_25"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "text_90"\
          },\
          {\
            "field": "textblock",\
            "required": false,\
            "role": "cta_apps_full"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "icon_300x300_app"\
          }\
        ],\
        "id": 48,\
        "interface": {\
          "projectionFactor": 0.19\
        },\
        "name": "teaser_256x256_title_text_app",\
        "status": "active"\
      },\
      {\
        "description": "90x90 teasers with an app icon, without CTA",\
        "format": [\
          {\
            "field": "url",\
            "required": true,\
            "role": "primary"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "title_25"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "text_90"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "icon_300x300_app"\
          }\
        ],\
        "id": 49,\
        "interface": {},\
        "name": "teaser_90x90_nocta_app",\
        "status": "active"\
      },\
      {\
        "description": "90x90 teasers from app icons, no text, with CTA",\
        "format": [\
          {\
            "field": "url",\
            "required": true,\
            "role": "primary"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "title_25"\
          },\
          {\
            "field": "textblock",\
            "required": true,\
            "role": "cta_apps_full"\
          },\
          {\
            "field": "content",\
            "required": true,\
            "role": "icon_300x300_app"\
          }\
        ],\
        "id": 50,\
        "interface": {},\
        "name": "teaser_90x90_notext_app",\
        "status": "active"\
      }\
    ],\
    "limit": 10,\
    "offset": 40
  }
```
