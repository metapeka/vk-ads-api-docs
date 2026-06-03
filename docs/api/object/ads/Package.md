# Package

Package identifier (ID).

Used in resources: [Packages](https://ads.vk.com/en/doc/api/resource/Packages)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| banner\_format\_id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | ID of the [banner format](https://ads.vk.com/en/doc/api/object/BannerFormat) used in the package. |
| banner\_url\_get\_params | string | readable | GET parameters to be added to the URL of each ad. |
| created | datetime | readabledefault\_field | Time of package creation. |
| description | string | readabledefault\_field | Package description. |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Package ID. |
| max\_price\_per\_unit | priceperunit | readabledefault\_field | Maximum price you can specify for a campaign based on the package. |
| max\_uniq\_shows\_limit | integer | readabledefault\_fieldmax\_value=2147483647 | Maximum number of times the ad is shown to a particular user that you can specify within the package. |
| name | string | readabledefault\_field | Package name. |
| objective | list of string | readabledefault\_field | Possible objectives for campaigns in this package. Possible values: reach - Reach; traffic - Traffic; appinstalls - App installs; reengagement - Remarketing in app; playersengagement - Social network gamers; videoviews - Video views; storeproductssales - Store products sales; engagement - Conversions; articleviews - Article views; audiolistening - Audio ads; socialengagement - Social network actions; storevisits - Store visits; premium\_reach - Premium network reach. |
| options | object | readable | Lists of the targetings and settings available for a campaign based on the package. Can contain the "defaults" and "values" fields that specify the default and possible targeting values respectively. For more information about the sites you can target, use the [PackagesPads](https://ads.vk.com/en/doc/api/resource/PackagesPads) method. |
| package\_request | string | readable | Status of package availability: - allowed - you can use the package - requested - you have requested the package, but it is not available yet - can\_be\_requested - you can request the package from the MyTarget support team: [support\_target@corp.my.com](mailto:support_target@corp.my.com) |
| pads\_tree\_id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | ID of the [pad tree](https://ads.vk.com/en/doc/api/object/PadsTree). If the tree has no branches, the value is 0. |
| paid\_event\_type | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | ID of the event for which you are charged: - 0 - 1000 shows - 1 - 1 click - 7 - convertion rate - 1013 - full video view - 1017 - view of the first 10 seconds of the video |
| price | priceperunit | readabledefault\_field | Default price of a campaign in the package. Unless you specify a custom price when creating a campaign, the default value will be used. |
| priced\_event\_type | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | ID of the event for which campaign are optimized: - 0 - 1000 shows - 1 - 1 click - 7 - convertion rate - 1013 - full video view - 1017 - view of the first 10 seconds of the video |
| related\_package\_ids | list of type | readabledefault\_field | IDs of the packages to which you can switch the existing campaigns based on the current package. |
| status | string | readablewritabledefault\_field<br>choices = <br>- active \- Active package.<br>- deleted \- Deleted package.<br>- blocked \- Blocked package. | Package status. You can create campaigns only using active packages. |
| updated | datetime | readabledefault\_field | Time of the last package update. |
| url\_types | object | readabledefault\_field | Link types allowed in the package. This is an object where the key is a link role and its value is an array of string arrays. The second-level arrays are lists of link types. In order for the link to have the specified role, it must belong to all the types listed in any of the second-level arrays. For example, if the field has the following value: \[\[type\_1, type\_2\]\[type\_1, type\_3\]\], the link must belong either to both "type\_1" and "type\_2" OR to both "type\_1" and "type\_3". |
