# AppleApp

The object contains data on an App Store mobile app.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| category\_id | integer | readablerequireddefault\_fieldmax\_value=2147483647 | Unique system ID of the mobile app category. For details, see [MobileCategory](https://ads.vk.com/en/doc/api/object/MobileCategory). |
| content\_rating | string | readablerequireddefault\_field | Age limit requirements for the mobile app users. Possible values: 0+, 3+, 4+, 7+, 9+, 12+, 16+, 17+, 18+. |
| description | string | readablerequireddefault\_field | Mobile app description. |
| icon\_image | [IconImage](https://ads.vk.com/en/doc/api/object/IconImage) | readablerequireddefault\_field | Unique system ID of the mobile app icon. |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Unique system ID of the object. |
| name | string | readablerequireddefault\_field | App ID in App Store. |
| title | string | readablerequireddefault\_field | Mobile app name. |
| type | string | readablerequireddefault\_field | Mobile app type (game, application). |
