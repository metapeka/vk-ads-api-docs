# MailingType

An object that stores the lists of the user's addresses subscribed to receive notifications.

Used in objects: [User](https://ads.vk.com/en/doc/api/object/User)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| email | list of email | readablewritabledefault\_field | List of addresses subscribed to the mailing list. If the list is empty, it means this mailing is available, but none of the user's addresses are subscribed to it. |
