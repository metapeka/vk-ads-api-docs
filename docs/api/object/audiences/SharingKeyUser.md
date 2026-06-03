# SharingKeyUser

The object is used fro activating an access key.

Used in resources: [SharingKeyUser](https://ads.vk.com/en/doc/api/resource/SharingKeyUser)

Used in objects: [SharingKey](https://ads.vk.com/en/doc/api/object/SharingKey)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | User ID. |
| key | string | readable | Access key. |
| sources | list of [UserSegment](https://ads.vk.com/en/doc/api/object/UserSegment) | readablewritabledefault\_field | List of the data sources that can be accessed with the key. |
| username | string | readablerequiredwritabledefault\_fieldcreate\_only | User name. |
