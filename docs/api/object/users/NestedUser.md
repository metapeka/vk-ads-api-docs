# NestedUser

The object contains info described an user in objects.

Used in objects: [SharingKey](https://ads.vk.com/en/doc/api/object/SharingKey)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| additional\_info | [AdditionalUserInfo](https://ads.vk.com/en/doc/api/object/AdditionalUserInfo) | readable | The object that contains additional information about the user. |
| agency | [Agency](https://ads.vk.com/en/doc/api/object/Agency) | readable | User agency information. It is returned only for the agency tokens acquired with the Client Credentials Grant method.. |
| agency\_username | string | readable | Main user agency name, if applicable. |
| available\_mailings | list of string | readable | User available mailing lists. |
| branch\_username | string | readable | Main agency user name, if applicable. |
| email | email | readabledefault\_field | Email. |
| firstname | string | readabledefault\_field | First name. |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | User ID. |
| language | string | readabledefault\_field<br>choices = <br>- ru \- russian<br>- en \- english | User language. |
| lastname | string | readabledefault\_field | Last name. |
| mailings | list of string | readable | User mailing lists. |
| partner | [Partner](https://ads.vk.com/en/doc/api/object/Partner) | readable | Information about user's partner account. |
| status | string | readablewritabledefault\_field<br>choices = <br>- active<br>- deleted<br>- blocked | Status. |
| types | list of string | readabledefault\_field | User types. |
| username | string | readabledefault\_field | User login in the service. |
