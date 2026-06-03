# BannerFields

## /api/v2/banner\_fields.json

Banner field registry

Used object: [BannerField](https://ads.vk.com/en/doc/api/object/BannerField)

### GET

Request example:

```http

   GET /api/v2/banner_fields.json
```

Response example:

```http
  {
    "count": 193,
    "items": [\
      {\
        "description": "link",\
        "field": "url",\
        "format": {\
          "max_length": 1000\
        },\
        "id": 1,\
        "interface": {\
          "placeholder": "url",\
          "type": "url"\
        },\
        "role": "url",\
        "status": "active"\
      },\
      {\
        "description": "about the company, max. 240 characters",\
        "field": "textblock",\
        "format": {\
          "text": {\
            "max_length": 115\
          }\
        },\
        "id": 2,\
        "interface": {\
          "help": "bannerRolesTextblockAboutCompany",\
          "placeholder": "about",\
          "type": "textarea"\
        },\
        "role": "about_company_115",\
        "status": "active"\
      },\
      {\
        "description": "icon image 90x90, static (logo)",\
        "field": "content",\
        "format": {\
          "max_height": 90,\
          "max_width": 90,\
          "min_height": 90,\
          "min_width": 90,\
          "type": "static",\
          "variants": {\
            "90x90": {\
              "height": 90,\
              "width": 90\
            }\
          }\
        },\
        "id": 3,\
        "interface": {\
          "type": "image"\
        },\
        "role": "icon_90x90",\
        "status": "active"\
      },\
      {\
        "description": "button text, all options, websites",\
        "field": "textblock",\
        "format": {\
          "text": {\
            "choices": [\
              "visitSite",\
              "to_shop",\
              "signUp",\
              "choose",\
              "book",\
              "download",\
              "order",\
              "enroll",\
              "register",\
              "playGame",\
              "buy",\
              "buy_ticket",\
              "see_menu",\
              "begin",\
              "open",\
              "apply",\
              "learnMore",\
              "call",\
              "get",\
              "try",\
              "contactUs",\
              "listen",\
              "watch",\
              "create",\
              "learn"\
            ]\
          }\
        },\
        "id": 4,\
        "interface": {\
          "help": "bannerRolesCta",\
          "type": "select"\
        },\
        "role": "cta_sites_full",\
        "status": "active"\
      },\
      {\
        "description": "title, max. 25 characters",\
        "field": "textblock",\
        "format": {\
          "text": {\
            "max_length": 25\
          }\
        },\
        "id": 5,\
        "interface": {\
          "help": "bannerRolesTextblockTitle",\
          "placeholder": "title",\
          "type": "input"\
        },\
        "role": "title_25",\
        "status": "active"\
      },\
      {\
        "description": "title, max. 90 characters",\
        "field": "textblock",\
        "format": {\
          "text": {\
            "max_length": 90\
          }\
        },\
        "id": 6,\
        "interface": {\
          "help": "bannerRolesTextblockText",\
          "placeholder": "text",\
          "type": "textarea"\
        },\
        "role": "text_90",\
        "status": "active"\
      },\
      {\
        "description": "promo image 600x600, static",\
        "field": "content",\
        "format": {\
          "max_height": 600,\
          "max_width": 600,\
          "min_height": 600,\
          "min_width": 600,\
          "type": "static",\
          "variants": {\
            "240x240": {\
              "height": 240,\
              "width": 240\
            },\
            "256x256": {\
              "height": 256,\
              "width": 256\
            },\
            "300x300": {\
              "height": 300,\
              "width": 300\
            },\
            "480x480": {\
              "height": 480,\
              "width": 480\
            },\
            "600x600": {\
              "height": 600,\
              "width": 600\
            },\
            "90x90": {\
              "height": 90,\
              "width": 90\
            }\
          }\
        },\
        "id": 7,\
        "interface": {\
          "placeholder": "image",\
          "type": "image"\
        },\
        "role": "image_600x600",\
        "status": "active"\
      },\
      {\
        "description": "promo image 1080x607, static",\
        "field": "content",\
        "format": {\
          "max_height": 607,\
          "max_width": 1080,\
          "min_height": 607,\
          "min_width": 1080,\
          "type": "static",\
          "variants": {\
            "1080x607": {\
              "height": 607,\
              "width": 1080\
            },\
            "150x84": {\
              "height": 84,\
              "width": 150\
            },\
            "240x135": {\
              "height": 135,\
              "width": 240\
            },\
            "300x168": {\
              "height": 168,\
              "width": 300\
            },\
            "320x180": {\
              "height": 180,\
              "width": 320\
            },\
            "480x270": {\
              "height": 270,\
              "width": 480\
            },\
            "492x277": {\
              "height": 277,\
              "width": 492\
            },\
            "530x298": {\
              "height": 298,\
              "width": 530\
            },\
            "548x308": {\
              "height": 308,\
              "width": 548\
            },\
            "600x336": {\
              "height": 336,\
              "width": 600\
            },\
            "800x450": {\
              "height": 450,\
              "width": 800\
            }\
          }\
        },\
        "id": 8,\
        "interface": {\
          "placeholder": "image",\
          "type": "image"\
        },\
        "role": "image_1080x607",\
        "status": "active"\
      },\
      {\
        "description": "html5, 240x400",\
        "field": "content",\
        "format": {\
          "height": 400,\
          "size": 1536000,\
          "type": "html5",\
          "width": 240\
        },\
        "id": 9,\
        "interface": {\
          "placeholder": "html5",\
          "type": "html5"\
        },\
        "role": "html5_240x400",\
        "status": "active"\
      },\
      {\
        "description": "image 240x400, static, animated",\
        "field": "content",\
        "format": {\
          "max_height": 400,\
          "max_width": 240,\
          "min_height": 400,\
          "min_width": 240,\
          "type": [\
            "static",\
            "animated"\
          ],\
          "variants": {\
            "240x400": {\
              "height": 400,\
              "width": 240\
            }\
          }\
        },\
        "id": 10,\
        "interface": {\
          "placeholder": "image",\
          "type": "image"\
        },\
        "role": "image_240x400",\
        "status": "active"\
      },\
      {\
        "description": "multiple link 1",\
        "field": "url",\
        "format": {\
          "max_length": 1000\
        },\
        "id": 11,\
        "interface": {\
          "autoComplete": true,\
          "help": "bannerRolesUrlLink",\
          "placeholder": "url",\
          "type": "url"\
        },\
        "role": "link_1",\
        "status": "active"\
      },\
      {\
        "description": "multiple link 2",\
        "field": "url",\
        "format": {\
          "max_length": 1000\
        },\
        "id": 12,\
        "interface": {\
          "help": "bannerRolesUrlLink",\
          "placeholder": "url",\
          "type": "url"\
        },\
        "role": "link_2",\
        "status": "active"\
      },\
      {\
        "description": "multiple link 3",\
        "field": "url",\
        "format": {\
          "max_length": 1000\
        },\
        "id": 13,\
        "interface": {\
          "help": "bannerRolesUrlLink",\
          "placeholder": "url",\
          "type": "url"\
        },\
        "role": "link_3",\
        "status": "active"\
      },\
      {\
        "description": "multiple link 4",\
        "field": "url",\
        "format": {\
          "max_length": 1000\
        },\
        "id": 14,\
        "interface": {\
          "help": "bannerRolesUrlLink",\
          "placeholder": "url",\
          "type": "url"\
        },\
        "role": "link_4",\
        "status": "active"\
      },\
      {\
        "description": "multiple link 5",\
        "field": "url",\
        "format": {\
          "max_length": 1000\
        },\
        "id": 15,\
        "interface": {\
          "help": "bannerRolesUrlLink",\
          "placeholder": "url",\
          "type": "url"\
        },\
        "role": "link_5",\
        "status": "active"\
      },\
      {\
        "description": "horizontal video",\
        "field": "content",\
        "format": {\
          "aspect_ratio": "16:9",\
          "max_length": 30,\
          "min_height": 360,\
          "min_length": 1,\
          "min_width": 640,\
          "size": 10485760,\
          "type": "video",\
          "variants": {\
            "1280x720x1600": {\
              "bitrate": 1600,\
              "height": 720,\
              "last_frame": true,\
              "width": 1280\
            },\
            "1280x720x1600-ogg": {\
              "bitrate": 560,\
              "format": "ogg",\
              "height": 360,\
              "width": 640\
            },\
            "1280x720x1600-webm": {\
              "bitrate": 560,\
              "format": "webm",\
              "height": 360,\
              "width": 640\
            },\
            "1920x1080x3000": {\
              "bitrate": 3000,\
              "height": 1080,\
              "last_frame": true,\
              "width": 1920\
            },\
            "1920x1080x3000-ogg": {\
              "bitrate": 560,\
              "format": "ogg",\
              "height": 360,\
              "width": 640\
            },\
            "1920x1080x3000-webm": {\
              "bitrate": 560,\
              "format": "webm",\
              "height": 360,\
              "width": 640\
            },\
            "640x360x560-ogg": {\
              "bitrate": 560,\
              "format": "ogg",\
              "height": 360,\
              "width": 640\
            },\
            "640x360x560-webm": {\
              "bitrate": 560,\
              "format": "webm",\
              "height": 360,\
              "width": 640\
            },\
            "640x360x800": {\
              "bitrate": 800,\
              "height": 360,\
              "last_frame": true,\
              "width": 640\
            },\
            "master-hls": {\
              "bitrate": 1,\
              "format": "hls",\
              "height": 1,\
              "width": 1\
            }\
          }\
        },\
        "id": 16,\
        "interface": {\
          "placeholder": "video",\
          "type": "video"\
        },\
        "role": "video_horizontal",\
        "status": "active"\
      },\
      {\
        "description": "video overlay 1080x607, static",\
        "field": "content",\
        "format": {\
          "max_height": 607,\
          "max_width": 1080,\
          "min_height": 607,\
          "min_width": 1080,\
          "type": "static",\
          "variants": {\
            "1080x607": {\
              "height": 607,\
              "width": 1080\
            },\
            "128x72": {\
              "height": 72,\
              "width": 128\
            },\
            "150x84": {\
              "height": 84,\
              "width": 150\
            },\
            "240x135": {\
              "height": 135,\
              "width": 240\
            },\
            "300x168": {\
              "height": 168,\
              "width": 300\
            },\
            "320x180": {\
              "height": 180,\
              "width": 320\
            },\
            "480x270": {\
              "height": 270,\
              "width": 480\
            },\
            "600x336": {\
              "height": 336,\
              "width": 600\
            },\
            "640x360": {\
              "height": 360,\
              "width": 640\
            },\
            "720x405": {\
              "height": 405,\
              "width": 720\
            },\
            "800x450": {\
              "height": 450,\
              "width": 800\
            },\
            "960x540": {\
              "height": 540,\
              "width": 960\
            }\
          }\
        },\
        "id": 17,\
        "interface": {\
          "placeholder": "image",\
          "type": "image"\
        },\
        "role": "overlay_1080x607",\
        "status": "active"\
      },\
      {\
        "description": "External_new link",\
        "field": "url",\
        "format": {\
          "max_length": 1000\
        },\
        "id": 18,\
        "interface": {\
          "affect": [\
            {\
              "field": "textblock",\
              "path": "data.title",\
              "role": "title_25"\
            },\
            {\
              "field": "textblock",\
              "path": "data.text",\
              "role": "text_90"\
            },\
            {\
              "field": "content",\
              "path": "data.image",\
              "role": "icon_300x300_app"\
            },\
            {\
              "field": "content",\
              "path": "data.image",\
              "role": "icon_128x128_games"\
            }\
          ],\
          "autoComplete": true,\
          "help": "bannerRolesUrlPrimary",\
          "placeholder": "url",\
          "type": "url"\
        },\
        "role": "primary",\
        "status": "active"\
      },\
      {\
        "description": "dynrem promo image 600x600, static",\
        "field": "content",\
        "format": {\
          "choices": [\
            5\
          ],\
          "from_pricelist": true\
        },\
        "id": 19,\
        "interface": {\
          "placeholder": "image_dynamic",\
          "type": "image"\
        },\
        "role": "image_600x600_dynamic",\
        "status": "active"\
      },\
      {\
        "description": "button text, all options, apps",\
        "field": "textblock",\
        "format": {\
          "text": {\
            "choices": [\
              "install",\
              "to_shop",\
              "signUp",\
              "choose",\
              "book",\
              "download",\
              "order",\
              "enroll",\
              "register",\
              "playGame",\
              "buy",\
              "buy_ticket",\
              "see_menu",\
              "begin",\
              "open",\
              "visitSite",\
              "apply",\
              "learnMore",\
              "call",\
              "get",\
              "try",\
              "contactUs",\
              "listen",\
              "watch",\
              "create",\
              "learn"\
            ]\
          }\
        },\
        "id": 20,\
        "interface": {\
          "type": "select"\
        },\
        "role": "cta_apps_full",\
        "status": "active"\
      }\
    ],\
    "limit": 20,\
    "offset": 0
  }
```
