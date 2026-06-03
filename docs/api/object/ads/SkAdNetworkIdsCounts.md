# SkAdNetworkIdsCounts

This object describes the number of SkAd Network campaign identifiers owned by the user and those issued to agents. It is used in the [MobileApps](https://ads.vk.com/en/doc/api/resource/MobileApps) resource as part of the [MobileApps](https://ads.vk.com/en/doc/api/object/MobileApps) object.

Used in objects: [MobileApps](https://ads.vk.com/en/doc/api/object/MobileApps)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| available | integer | readabledefault\_fieldmin\_value=0max\_value=100 | Number of SkAd Network campaign identifiers that belong to the user and are not used in ad campaigns |
| inherited\_available | integer | readabledefault\_fieldmin\_value=0max\_value=100 | Number of SkAd Network campaign identifiers that were issued to agents but have not been used by them in ad campaigns |
| inherited\_total | integer | readabledefault\_fieldmin\_value=0max\_value=100 | Number of SkAd Network campaign identifiers that were issued to agents (including those used by them in ad campaigns) |
| inherited\_used | integer | readabledefault\_fieldmin\_value=0max\_value=100 | Number of SkAd Network campaign identifiers that were issued to agents and used by them in ad campaigns |
| total | integer | readabledefault\_fieldmin\_value=0max\_value=100 | Total number of SkAd Network campaign identifiers owned by the user (including those used in campaigns, but excluding those issued to agents) |
| used | integer | readabledefault\_fieldmin\_value=0max\_value=100 | Number of SkAd Network campaign identifiers occupied by the user's campaigns |
