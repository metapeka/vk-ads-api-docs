# TargetingsTreeElement

The object provides information about an interest.

Used in objects: [TargetingsTree](https://ads.vk.com/en/doc/api/object/TargetingsTree)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| children | list of object | readabledefault\_field | List of embedded interests represented as {"name": str, "id": int}. |
| id | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Interest ID. |
| name | string | readabledefault\_field | Interest name. |
| synonyms | list of string | readabledefault\_field | Interest synonyms. |
