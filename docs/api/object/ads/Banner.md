# Banner

An object describing a campaign ad.

Used in resources: [Banners](https://ads.vk.com/en/doc/api/resource/Banners), [Banner](https://ads.vk.com/en/doc/api/resource/Banner)

Used in objects: [AdGroup](https://ads.vk.com/en/doc/api/object/AdGroup)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | uint32 | readabledefault\_field | Ad identifier |
| created | datetime | readable | Creation time |
| updated | datetime | readable | Last update time |
| name | string | readablewritable | Banner name |
| status | string | readablewritable<br>choices = <br>- active \- Active<br>- deleted \- Deleted<br>- blocked \- Blocked | Ad status. The `deleted` status may also be returned for deleted banners. For an ad with status `deleted`, only the status can be changed. |
| ad\_group\_id | uint32 | readabledefault\_field | Ad group identifier |
| content | object with [BannerContent](https://ads.vk.com/en/doc/api/object/BannerContent) as values | readablewritable | Banner content. Must match the `content` structure of the [banner field](https://ads.vk.com/en/doc/api/object/BannerField) in the ad group's package. |
| delivery | string | readable | Banner delivery status. Possible values: `pending` — banner is awaiting moderation; `delivering` — banner can be shown; `not_delivering` — banner cannot be shown; reasons are described in the `issues` field. |
| issues | list of object | readable | Description of reasons why the ad is not being shown:<br>- ACCOUNT\_INACTIVE \- Account is inactive.<br>- BANNER\_STOPPED \- The banner is stopped.<br>- BANNER\_ARCHIVED \- The banner is removed.<br>- CAMPAIGN\_STOPPED \- The campaign is stopped.<br>- CAMPAIGN\_ARCHIVED \- The campaign is removed.<br>- BANNER\_BANNED \- The banner is rejected by moderation.<br>- BANNER\_ON\_MODERATION \- The banner is on moderation. |
| moderation\_reasons | list of [ModerationReason](https://ads.vk.com/en/doc/api/object/ModerationReason) | readable | Reasons why the ad was banned |
| moderation\_status | string | readabledefault\_field | Ad moderation status. Possible values: `pending` — not moderated; `allowed` — approved; `banned` — rejected. |
| textblocks | object with [Textblock](https://ads.vk.com/en/doc/api/object/Textblock) as values | readablewritable | Text content blocks. Must match the `textblocks` structure of the [banner field](https://ads.vk.com/en/doc/api/object/BannerField) in the ad group's package. |
| urls | object with [Urls](https://ads.vk.com/en/doc/api/object/Urls) as values | readablewritable | Link objects. Must match the `urls` structure of the [banner field](https://ads.vk.com/en/doc/api/object/BannerField) in the ad group's package. |
| ord\_marker | string | readablemax\_length=32default\_field | Creative labeling token |
