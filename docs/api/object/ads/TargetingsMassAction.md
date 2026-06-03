# TargetingsMassAction

Targetings available for modification in the [campaign bulk update API](https://ads.vk.com/en/doc/api/object/CampaignMassAction).

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| age | [AgeTargeting](https://ads.vk.com/en/doc/api/object/AgeTargetingMassAction) | readablewritable | Age (list of ages). `0` — show to users whose age is not defined. |
| geo | [GeoTargeting](https://ads.vk.com/en/doc/api/object/GeoTargetingMassAction) | readablewritable | Geo targeting. |
| interests | list of integer | readablewritable | User interests. [List of available interests](https://ads.vk.com/en/doc/api/resource/TargetingsTree). |
| sex | list of string | readablewritable | Gender (combinations of `male` and `female`). |
