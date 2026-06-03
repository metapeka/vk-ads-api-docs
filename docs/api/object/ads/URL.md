# URL

The object of the advertised URL.

Used in resources: [CreateUrl](https://ads.vk.com/en/doc/api/resource/CreateUrl), [ReadUrls](https://ads.vk.com/en/doc/api/resource/ReadUrls), [ReadUrl](https://ads.vk.com/en/doc/api/resource/ReadUrl)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| counters | list of string | readabledefault\_field | The counters located at the link landing. Examples: TOP\_MAIL\_RU, RAMBLER\_TOP100, GOOGLE\_ANALYTICS, YA\_METRICA, LI\_RU. |
| has\_goals | boolean | readabledefault\_field | The flag that marks if the application with the specified URL has the lead-to-installation conversion rate high enough to create a campaign with payments per installation. |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | ID of the created object. |
| preview\_link | string | readable | Preview link, if available. |
| url | url | readablerequiredwritabledefault\_field | The URL. It must use either the "http://" or "https://" schema. |
| url\_types | list of string | readabledefault\_field | URL types that were identified automatically. To be used in an ad, the URL must contain the type specified in the "fields" field of the [banner format resource](https://ads.vk.com/en/doc/api/object/BannerFormat)\_. |
