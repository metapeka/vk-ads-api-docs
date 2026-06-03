# AuditPixelCheck

An object that provides information about whether an audit pixel is used in campaigns.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| audit\_pixel | url | readablerequiredwritabledefault\_field | Audit pixel URL. |
| generated\_audit\_pixels | list of [GeneratedAuditPixel](https://ads.vk.com/en/doc/api/object/GeneratedAuditPixel) | readable | Array of generated audit pixels and their roles. |
