# Urls

An object that describes ad URLs.

Used in objects: [Banner](https://ads.vk.com/en/doc/api/object/Banner), [BannerMassAction](https://ads.vk.com/en/doc/api/object/BannerMassAction)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | id | readablerequiredwritabledefault\_fieldmin\_value=1max\_value=2147483647 | URL identifier |
| url | url | readable | URL |
| url\_object\_id | string | readable | Identifier of the linked object |
| url\_object\_type | string | readable | Type of the linked object |
| url\_types | list of string | readable | URL types that were detected automatically. To be used in ads, the URL must include a type specified in the [banner format](https://ads.vk.com/en/doc/api/object/BannerFormat) in the `fields` field. |
