# RemarketingUsersList

Data source is a users list.

Used in resources: [RemarketingUsersLists](https://ads.vk.com/en/doc/api/resource/RemarketingUsersLists), [RemarketingUsersList](https://ads.vk.com/en/doc/api/resource/RemarketingUsersList)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| base | integer | readablewritabledefault\_fieldcreate\_onlymin\_value=-2147483647max\_value=2147483647 | Source list ID that is used to update the lists. Possible commands: - "base = 0" - the current source list - "base = N" - adds IDs from the new list to the current souce list - "base = -N" - removed IDs from the new list from the current source list. |
| can\_create\_portrait | boolean | readable | Possibility to build an audience profile. |
| created | datetime | readabledefault\_field | Time of the list creation. |
| entries\_count | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Number of list entries that were uploaded. |
| has\_history | boolean | readabledefault\_field | Flag of source list revision history. |
| history | list of [RemarketingUsersListHistory](https://ads.vk.com/en/doc/api/object/RemarketingUsersListHistory) | readable | Source list revision history. |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | List ID. |
| ids\_count | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Original list size. |
| matched\_ids\_count | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Number of source IDs for which corresponding IDs have been found. |
| name | string | readablerequiredwritabledefault\_field | List name. |
| status | string | readabledefault\_field<br>choices = <br>- receiving \- List is being sent for processing (default status).<br>- received \- List was received for processing.<br>- mapping \- List is being processed (comparison in progress).<br>- mapped \- List has been processed.<br>- writing \- Processed list is being written to the database.<br>- ready \- List is written to the database and ready for use.<br>- pending\_delete \- User has marked the list for deletion.<br>- deleting \- List is being deleted from the database.<br>- deleted \- List has been deleted.<br>- deleted\_to\_notify \- List was deleted at VK Ads requests and user may not be aware of it. | Processing status. |
| type | string | readablerequiredwritabledefault\_fieldcreate\_only<br>choices = <br>- ok \- List of Odnoklassniki users IDs.<br>- mm \- LIst of my.mail.ru gamers IDs.<br>- phones \- List of phone numbers or their hash sums.<br>- emails \- List of emails or their hash sums.<br>- device\_id \- List of Android devices hardware IDs.<br>- android\_id \- List of Android devices software IDs.<br>- advertising\_id \- List of Google Advertising ID.<br>- idfa \- List of Apple mobile devices IDs.<br>- dmp\_id \- List of external user IDs from partner DMP providers.<br>- dmp\_top \- List of first-party data IDs.<br>- vk \- List of VKontakte users IDs.<br>- mac \- List of MAC addresses.<br>- mparticle \- List of mParticle users.<br>- human \- Common list makes it possible to load several types of identifiers in one file. | List type. For more information about list types, see [this article](https://target.my.com/adv/help/remarketing/#user_list). |
| updated | datetime | readable | Time of the list last update. |
| users | list of [RemarketingUsersListUser](https://ads.vk.com/en/doc/api/object/RemarketingUsersListUser) | readable | Users who can access the list. |
| users\_count | integer | readablemin\_value=-2147483647max\_value=2147483647 | Number of users who can access the list. |
