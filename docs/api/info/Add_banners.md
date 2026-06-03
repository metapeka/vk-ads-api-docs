# Add banners

# Adding an ad to an existing ad group

To add an ad to an existing ad group, make a POST request.`/api/v2/ad_groups/{{ad_group_id}}/banners.json`, where `ad_group_id` is the identifier of the existing ad group. You must first obtain the link IDs, as well as the images and videos.

Example of a request for an advertising campaign on the VKontakte community with the target action "Join the community" / "Write to the community":

```bash
POST /api/v2/ad_groups/{{ad_group_id}}/banners.json
Host: ads.vk.com
Authorization: Bearer {{access_token}}

{
    "name": "Ad 2023-09-01",
    "urls": {
        "primary": {
          "id": 12345
        }
    },
    "content": {
        "icon_256x256": {
            "id": 20414
        },
        "image_1080x607": {
            "id": 20416
        }
    },
    "textblocks": {
        "text_2000": {
        "text": "Bags and accessories made of genuine leather, created especially for you!"
        },
        "cta_community_vk": {
        "text": "signUp"
        },
        "about_company_115": {
        "text": "Sitnikova Elena Yuryevna, TIN 250300980000"
        },
        "title_40_vkads": {
        "text": "Genuine leather bags"
        }
    }
}
```

Response example:

```json
{
  "id": 410
}
```

Explanation of the fields in the request:

- \`urls' - links
- \`content' - creatives (static images, videos, etc.)
- `textblocks` \- ad text blocks

The ad structure must match [banner patterns](https://ads.vk.com/doc/api/object/BannerPattern), defined in [package](https://ads.vk.com/doc/api/object/Package) ad groups ( [AdGroup](https://ads.vk.com/doc/api/object/AdGroup)), where the ad is placed. To specify objects, it is enough to use identifiers. There is no need to specify variations for the content section or url, url\_object\_type for the urls section.

Example of a request to add an ad to advertise products from the pricelist in the VKontakte community:

```bash
POST /api/v2/ad_groups/{{ad_group_id}}/banners.json
Host: ads.vk.com
Authorization: Bearer {{access_token}}

{
  "name": "Ad 2023-09-25",
  "urls": {
    "primary": {
      "id": 87674394
    }
  },
  "content": {
    "icon_256x256": {
      "id": 21930207
    },
    "video_landscape_30s": {
      "id": 20546947
    }
  },
  "textblocks": {
    "cta_pricelist_full": {
      "text": "buy"
    },
    "text_220": {
      "text": "Unique polymer clay jewelry! Order your jewelry right now and we will deliver them all over Russia."
    },
    "text_50": {
      "text": "Catalog of polymer clay jewelry"
    },
    "text_125": {
      "text": "{{product.name}} {{product.price}}"
    },
    "title_40": {
      "text": "{{product.name}}"
    },
    "text_47": {
      "text": "{{product.price}}"
    },
    "title_25": {
      "text": "Ceramics Workshop"
    }
  }
}
```

Response example:

```json
{
  "id": 411
}
```

`{{product.name }}` and `{{product.price}}` specified in the query example are macros that allow you to display the properties of the feed's product items in an ad. A list of available macros can be found in the article [Macros in product advertising from the catalog](https://ads.vk.com/en/help/articles/feed_macro).

Example of a request to create a banner in the Carousel format:

```bash
POST /api/v2/ad_groups/{{ad_group_id}}/banners.json
Host: ads.vk.com
Authorization: Bearer {{access_token}}

{
    "content": {
        "icon_256x256": {
            "id": 34236123
        },
        "image_600x600_slide_1": {
            "id": 34236124
        },
        "image_600x600_slide_2": {
            "id": 34236125
        },
        "image_600x600_slide_3": {
            "id": 34236126
        }
    },
    "urls": {
        "primary": {
            "id": 83641232
        },
        "url_slide_1": {
            "id": 83641233
        },
        "url_slide_2": {
            "id": 83641234
        },
        "url_slide_3": {
            "id": 83641235
        }
    },
    "textblocks": {
        "title_40_vkads": {
            "text": "<heading>"
        },
        "text_90": {
            "text": "<text>"
        },
        "about_company_115": {
            "text": "<legal information about the company>"
        },
        "cta_sites_full": {
            "text": "visitSite"
        },
        "title_40_slide_1": {
            "text": "Text of slide 1"
        },
        "title_40_slide_2": {
            "text": "Text of slide 2"
        },
        "title_40_slide_3": {
            "text": "Text of slide 3"
        }
    }
}
```

Response example:

```json
{
  "id": 412
}
```

Possible response codes:

- 200 - the ad is saved
- 400 - validation error

Possible error codes:

- active\_banners\_limit - exceeded the number of banners of active banners for the user
- invalid\_ad\_group - the ad group does not exist
- ad\_group\_banners\_limit - the limit on the number of ads for a group has been exceeded.
- bad\_width - incorrect content width value
- bad\_height - incorrect content height value
- bad\_size - exceeding the maximum content size
- bad\_type - incorrect content type
- bad\_length - the content has an invalid playback duration.
- bad\_bitrate - the content has an invalid bitrate
- dynamic\_content - dynamic content is used in an invalid role
- custom\_params - incorrect video parameters
- excluation\_signs\_limit - the limit on exclamation marks in the banner text block has been exceeded.
- invalid\_macros - an unauthorized macro is used in the banner text block.
- persistent\_urls - changing links is prohibited in the package
- one\_url\_object\_id - links leading to various objects are prohibited in the package.
- campaign\_one\_url - various links are prohibited in the package
- url\_not\_checked - the use of unverified links is prohibited
- url\_not\_valid - the link does not fit the specified role.
- max\_value - the value is greater than the maximum
- min\_value - the value is less than the minimum
- bad\_value - incorrect format or type of value
- required - required field
- unallowed\_value - the value is not included in the list of valid values.
- bad\_items - the list contains incorrect values.
- unallowed\_field - the field is unavailable
- read\_only\_field - updating an immutable field

In general, the error message has the following format:

```json
{
  "error": {
    "fields": {
      "<field_name_1>": {
        "message": "<error_message_1>",
        "code": "<error_code_1>"
      },
      "<field_name_2>": {
        "message": "<error_message_2>",
        "code": "<error_code_2>"
      }
    },
    "message": "Validation failed",
    "code": "validation_failed"
  }
}
```

where field\_name\_N is the name of the field where the error occurred, error\_message\_N is the error description, and error\_code\_N is the error code.

Example:

```json
{
  "error": {
    "fields": {
      "urls": {
        "message": "Url must be same with other banners in this package",
        "code": "campaign_one_url"
      }
    },
    "message": "Validation failed",
    "code": "validation_failed"
  }
}
```
