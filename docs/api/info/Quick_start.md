# Quick start

# Creation of the "VKontakte Community" advertising campaign

# Required data:

1. CLIENT\_ID and CLIENT\_SECRET for the API client (see [providing API access](https://ads.vk.com/en/help/articles/help_api))
2. The URL of the VKontakte community

# Procedure for creating an advertising campaign:

1. Getting an access token
2. Checking the community URL in VK and getting the url\_id
3. Uploading content and getting IDs of uploaded objects
4. Creating a campaign with an ad group and an ad

# Getting an access token

See also [Authorization in the API](https://ads.vk.com/en/doc/api/info/Authorization)

To work with the VK Advertising API, you must obtain an access token and periodically update it in the future.

```bash
POST /api/v2/oauth2/token.json HTTP/1.1
Host: ads.vk.com
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials&client_id={CLIENT_ID}&client_secret={CLIENT_SECRET}
```

In response, we get access\_token and refresh\_token:

```json
{
  "access_token": "VPw...skipped...K2t",
  "token_type": "Bearer",
  "expires_in": 86400,
  "scope": [],
  "refresh_token": "Vtv...skipped...gga",
  "tokens_left": 4
}
```

# Checking the community URL in VK and getting the url\_id

To get the link ID, make a GET request `/api/v1/urls/?url={URL}`

For example, let's take a community [vk.com/vk](https://vk.com/vk):

```bash
GET /api/v1/urls/?url=https%3A%2F%2Fvk.com%2Fvk
Host: ads.vk.com
Authorization: Bearer {ACCESS_TOKEN}
```

Response:

```json
{
  "id": 61732652,
  "url_types": ["external_new", "vk_group", "internal", "vk"],
  "url_object_id": "22822305",
  "counters": [],
  "preview_link": null,
  "applink": null,
  "has_bad_landing": false,
  "has_nonhts_redirects": false,
  "has_mobile_app": false,
  "mobile_app_type": null,
  "has_goals": false,
  "has_postback_trackers": false,
  "postback_trackers": []
}
```

When creating a campaign, we use the **id** field from the received response.

# Uploading content and getting IDs of uploaded objects

To upload static images, a POST request is sent to [https://ads.vk.com/api/v2/content/static](https://ads.vk.com/api/v2/content/static) .json with the multipart/form-data type. Allowed formats: jpg, png.

Example of loading a 256x256 icon:

```bash
curl -X POST \
  "https://ads.vk.com/api/v2/content/static.json" \
  -H "authorization: Bearer $ACCESS_TOKEN" \
  -F file=@img256x256.jpg
```

Response:

```json
{
  "id": 21506470,
  "variants": {
    "original": {
      "url": "https://r.mradx.net/img/88/91B08C.jpg",
      "height": 256,
      "width": 256,
      "size": 14407
    },
    "uploaded": {
      "url": "https://r.mradx.net/img/88/91B08C.jpg",
      "height": 256,
      "width": 256,
      "size": 14407
    }
  }
}
```

Similarly, we upload 600x600px and 1080x607px images. The received object IDs are used in the request to create an advertising campaign.

# Creating a campaign with an ad group and an ad

To create a campaign with a group and ads, the `POST /api/v2/ad_plans' request is used.json`. Specify the required value of the _package\_id field in the request._:

- 3122 - Join the community
- 3127 - Write to the community
- 3194 - Increase engagement

Accordingly, in the text blocks of the ad, specify the value of the _cta\_community\_vk_:

- "signUp", if _package\_id_ = 3122
- "contactUs", if _package\_id_ = 3127

The ad object will be different for _package\_id_ = 3194:

```json
{
  "name": "Test banner",
  "urls": {
    "vk_post": {
      "id": 87252892
    }
  }
}
```

Here, the vk\_post object is the ID of the link to the community post. The id value must first be obtained by requesting [https://ads.vk.com/api/v1/urls](https://ads.vk.com/api/v1/urls) specifying the URL of the post (similar to the example of getting the community link ID).

```bash
POST /api/v2/ad_plans.json
Host: ads.vk.com
Authorization: Bearer {ACCESS_TOKEN}

{
    "name": "Advertising campaign 2023-09-20",
    "status": "active",
    "date_start": "2023-09-20",
    "date_end": "2023-09-25",
    "autobidding_mode": "max_goals",
    "budget_limit_day": 1000,
    "budget_limit": null,
    "max_price": 0,
    "objective": "socialengagement",
    "ad_object_id": 61732652,
    "ad_object_type": "url",
    "ad_groups": [\
        {\
            "name": "Ad Group 2023-09-20",\
            "targetings": {\
                "geo": {\
                    "regions": [\
                        5506\
                    ]\
                },\
                "sex": [\
                    "female"\
                ],\
                "age": {\
                    "age_list": [\
                        0,\
                        19,\
                        20,\
                        21,\
                        22\
                    ]\
                }\
            },\
            "max_price": 0,\
            "budget_limit": null,\
            "budget_limit_day": 1000,\
            "date_start": "2023-09-20",\
            "date_end": null,\
            "age_restrictions": "0+",\
            "package_id": 3122,\
            "banners": [\
                {\
                    "name": "Ad 2023-09-20",\
                    "urls": {\
                        "primary": {\
                        "id": 61732652\
                        }\
                    },\
                    "content": {\
                        "icon_256x256": {\
                            "id": 21506470\
                        },\
                        "image_1080x607": {\
                            "id": 21507733\
                        }\
                    },\
                    "textblocks": {\
                        "text_2000": {\
                            "text": "Here is the description of the banner"\
                        },\
                        "cta_community_vk": {\
                            "text": "signUp"\
                        },\
                        "about_company_115": {\
                            "text": "Here is information about the advertiser"\
                        },\
                        "title_40_vkads": {\
                            "text": "Here is the banner title"\
                        }\
                    }\
                }\
            ]\
        }\
    ]
}
'
```

Response:

```json
{
  "ad_groups": [\
    {\
      "id": 321\
    }\
  ],
  "id": 340
}
```

## Explanation of the request fields:

###The top-level object is an "Advertising campaign" (ad\_plan)

- `ad_object_id` \- id of the advertised object
- `autobidding_mode` \- campaign budget optimization
- \`max\_price' is the upper limit for automatic price control in foreign currency rubles (0 is automatic bid control). See also [Guide to Automatic Bid Management](https://ads.vk.com/en/insights/vkads-autobidding-guide)
- \`ad\_groups' - list of "Adgroup" objects
- \`budget\_limit' - total campaign budget in foreign currency rubles
- \`budget\_limit\_day' - daily campaign budget in foreign currency rubles
- \`date\_start' - the start date of the campaign broadcast
- \`date\_end' - the end date of the broadcast campaign (may be null)
- `objective` \- the target action of the advertising campaign

Budget management can be set either at the level of the entire advertising campaign, or separately for each ad group. If campaign-level budget optimization is enabled (`autobidding_mode` is not null), then either the daily budget or the total budget and campaign duration must also be set (non-empty `date_end`). See also [Budget Optimization](https://ads.vk.com/en/help/features/optimization)

### The "Adgroup" object (ad\_group)

- \`age\_restrictions' - age marking (0+/6+/12+/16+/18+)
- ` banners` \- list of objects "banner"
- `budget_limit` \- total budget of the group in foreign currency rubles
- `budget_limit_day` \- the group's daily budget in foreign currency rubles
- \`date\_start' - the start date of the group broadcast (cannot be earlier than the start date of the campaign broadcast)
- \`date\_end' - the end date of the broadcast of the group (it can be null, then it will be inherited from the end date of the broadcast of the campaign)
- \`max\_price' is the upper limit for automatic price control in foreign currency rubles (0 is automatic bid control). See also \[Guide to Automatic Bid Management\]( [https://ads.vk.com/en/insights/vkads-autobidding-guide](https://ads.vk.com/en/insights/vkads-autobidding-guide)
- `package_id` is the identifier of the advertising package used for this advertising campaign.
- `targets` \- targeting, ad group settings that allow you to select a target audience. Learn more about targeting below.

If budget optimization is enabled at the campaign level, then in the ad group, the values of the budget\_limit, budget\_limit\_day, and max\_price fields must be set equal to the corresponding values of the upper-level campaign object.

### The "Ad" object (banner)

- \`urls' - links
- \`content' - creatives (static images, videos, etc.)
- `textblocks` \- ad text blocks

The list of available keys in the urls, content, and textblocks fields is determined by the advertising package to which the campaign is linked.

### Targeting

See also:

- [background information on targeting](https://ads.vk.com/en/help/features/technology)
- [The Targets API object](https://ads.vk.com/doc/api/object/Targetings)

The set of allowed targeting depends on the advertising package.

`geo` is a general geography targeting that combines geolocations and regions (a list of region IDs). Only one of the values can be set - local\_geo or regions. To get a list of regions with their IDs, make a GET request `/api/v2/regions.json`:

```bash
GET /api/v2/regions.json?_flags__in=geo_tree_extended,rb_active&fields=id,name,parent_id
Host: ads.vk.com
Authorization: Bearer {{access_token}}
Accept-Language: ru-RU,ru;q=0.9,en-US;q=0.8
```

Response:

```json
{
  "count": 632,
  "items": [\
    {\
      "id": 188,\
      "name": "Russia",\
      "parent_id": 100001\
    },\
    {\
      "id": 100001,\
      "name": "Former USSR",\
      "parent_id": -1\
    },\
    {\
      "id": 70,\
      "name": "Moscow Oblast",\
      "parent_id": 188\
    },\
    ...\
  ]
}
```

Specify the list of region IDs in geo/regions targeting when creating an advertising campaign.:

```json
{
    "name": "Ad Group 2023-09-20",
    "targetings": {
        "geo": {
            "regions": [\
                5506,\
                70\
            ]
        },
        ...
    },
    ...
}
```

`fulltime` \- targeting to limit the display time (days of the week/hours)

An example of targeting for impressions only on weekends. Flag values:

- `cross_timezone` \- take into account the local time
- `use_holidays_moving` \- take public holidays into account

```json
{
    "name": "Ad Group 2023-09-20",
    "targetings": {
        "fulltime": {
            "flags": ["cross_timezone", "use_holidays_moving"],
            "mon": [],
            "tue": [],
            "wed": [],
            "thu": [],
            "fri": [],
            "sat": [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23],
            "sun": [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23]
        },
        ...
    },
    ...
}
```

`age` \- age targeting (list of ages). 0 - show to those whose age has not been determined.

```json
{
    "name": "Ad Group 2023-09-20",
    "targetings": {
        "age": {
            "age_list": [\
                0,\
                19,\
                20,\
                21,\
                22\
            ]
        },
        ...
    },
    ...
}
```

`sex` \- targeting by gender. A list of two possible options: `male` \- men, `female` \- women.

```json
{
    "name": "Ad Group 2023-09-20",
    "targetings": {
        "sex": ["male"],
        ...
    },
    ...
}
```

`interests` \- targeting by user interests. Negative elements indicate exceptions.

```json
{
    "name": "Ad Group 2023-09-20",
    "targetings": {
        "interests": [\
            7352,\
            13612,\
            -7356\
        ],
        ...
    },
    ...
}
```

The list of interests can be downloaded using the `/api/v2/targetings_tree' GET request.json`:

```bash
GET /api/v2/targetings_tree.json?targetings=interests
Host: ads.vk.com
Authorization: Bearer {{access_token}}
```

Response:

```json
{
  "interests": [\
    {\
      "children": null,\
      "id": 14544,\
      "name": "Referer/Finance/Trading on the stock exchange/Binary Options",\
      "synonyms": [\
        "Purchase",\
        "Auto"\
      ],\
      "no_checkbox": false\
    },\
    {\
      "children": [\
        {\
          "id": 9018,\
          "name": "Cars and SUVs",\
          "no_checkbox": false,\
          "synonyms": [\
            "BCHD",\
            " Crossovers",\
            "Off-road vehicles"\
          ]\
        },\
        {\
          "id": 7355,\
          "name": "Premium class cars",\
          "no_checkbox": false,\
          "synonyms": []\
        },\
        ...\
    },\
    ...\
  ]\
}\
\
`segments` \- targeting by audience segments. This assumes that you already have pre-created audience segments. Specify a list of segment IDs. Negative values indicate exceptions.\
\
See also:\
\
- [Help on classroom segments](https://ads.vk.com/en/help/features/audiences_lists/audiences)\
- [Segments Resource](https://ads.vk.com/doc/api/resource/Segments)\
\
\`\`\`json\
{\
    "name": "Ad Group 2023-09-20",\
    "targetings": {\
        "segments": [\
            2811551,\
            -3650600\
        ],\
        ...\
    },\
    ...\
}\
\`\`\`\
\
To get a list of existing classroom segments and their IDs, use a GET request to `/api/v2/remarketing/segments.json`:\
\
\`\`\`bash\
GET /api/v2/remarketing/segments.json\
Host: ads.vk.com\
Authorization: Bearer {{access_token}}\
\`\`\`\
\
Response:\
\
\`\`\`json\
{\
  "limit": 20,\
  "offset": 0,\
  "items": [\
    {\
      "id": 2811551,\
      "name": "Audience 1",\
      "pass_condition": 1,\
      "flags": ["cross_device"],\
      "created": "2022-08-23 12:57:14",\
      "updated": "2022-08-23 12:57:14"\
    },\
    {\
      "id": 3650600,\
      "name": "Audience 2",\
      "pass_condition": 1,\
      "flags": ["cross_device"],\
      "created": "2023-05-12 09:46:47",\
      "updated": "2023-05-12 09:46:47"\
    }\
  ],\
  "count": 2\
}
```
