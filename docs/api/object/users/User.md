# User

The object contains user data and links to related objects.

Used in resources: [User](https://ads.vk.com/en/doc/api/resource/User)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| account | object | readable | Financial data of the user. |
| active\_banners | integer | readablemin\_value=-2147483647max\_value=2147483647 | Number of active banners. |
| additional\_emails | list of email | readablewritable | List of additional user's emails. |
| additional\_info | [AdditionalUserInfo](https://ads.vk.com/en/doc/api/object/AdditionalUserInfo) | readablewritable | The object that contains additional information about the user. |
| agency | [Agency](https://ads.vk.com/en/doc/api/object/Agency) | readable | User agency information. It is returned only for the agency tokens acquired with the Client Credentials Grant method. |
| agency\_username | string | readable | Main user agency name, if applicable. |
| available\_mailings | list of string | readable | User available mailing lists. |
| branch\_username | string | readable | Main agency user name, if applicable. |
| currency | string | readabledefault\_field | User currency. |
| email | email | readabledefault\_field | Email |
| firstname | string | readabledefault\_field | First name |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | User ID. |
| info\_currency | string | readablewritabledefault\_field | User currency. |
| language | string | readablewritabledefault\_field<br>choices = <br>- ru \- Russian<br>- en \- English | User language. |
| lastname | string | readabledefault\_field | Last name |
| mailings | list of string | readablewritable | User mailing lists. |
| max\_active\_banners | integer | readablemin\_value=-2147483647max\_value=2147483647 | Maximum number of active banners. |
| permissions | object | readable | List of user permissions specified in the following format: 'permission' -> 'true/false'. For example: {'can\_create\_ads': true}. |
| regions | [UserRegions](https://ads.vk.com/en/doc/api/object/UserRegions) | readable | Object containing information about regions for installation when creating advertisements. |
| status | string | readablewritabledefault\_field<br>choices = <br>- active \- Active<br>- deleted \- Deleted<br>- blocked \- Blocked | Status |
| types | list of string | readabledefault\_field | User types. |
| username | string | readabledefault\_field | User login in the service. |
