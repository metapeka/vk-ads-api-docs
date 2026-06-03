# UserAccount

The object contains data on the balance of an user.

Used in objects: [UserManagerClient](https://ads.vk.com/en/doc/api/object/UserManagerClient), [UserClient](https://ads.vk.com/en/doc/api/object/UserClient)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| a\_balance | decimal | readable | Liquid balance. |
| balance | decimal | readabledefault\_field | Balance. |
| currency\_balance\_hold | decimal | readabledefault\_field | The amount on hold to pay for the CPI. |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Unique system identifier of the user account |
| type | string | readabledefault\_field | Client type. |
