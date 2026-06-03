# BannerContent

An object that describes the content of an ad.

Used in objects: [Banner](https://ads.vk.com/en/doc/api/object/Banner), [BannerMassAction](https://ads.vk.com/en/doc/api/object/BannerMassAction)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | id | readablerequiredwritabledefault\_fieldmin\_value=1max\_value=2147483647 | Content identifier |
| type | string | readable | Content type. Possible values: `static`, `animated`, `rollovered`, `video`, `html5`, `audio` |
| variants | object with [ContentVariant](https://ads.vk.com/en/doc/api/object/ContentVariant) as values | readable | Available content variants |
