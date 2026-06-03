# UserRegions

Object containing information about regions for installation when creating advertisements.

Used in objects: [User](https://ads.vk.com/en/doc/api/object/User), [User](https://ads.vk.com/en/doc/api/object/User)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| allowed | list of type | readabledefault\_field | List of region IDs where user is allowed to create ads. |
| required | list of type | readabledefault\_field | List of region IDs where user is required to create ads. |
| required\_one\_of | list of type | readabledefault\_field | List of region IDs where user is allowed to create ads with one of them. |
