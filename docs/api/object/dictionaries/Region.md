# Region

An object that contains information about the region.

Used in resources: [Region](https://ads.vk.com/en/doc/api/resource/Region)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| flags | list of string | readabledefault\_field | Flags that show the region's belonging to a particular subtree. The example is in the associated [method](https://ads.vk.com/en/doc/api/resource/Region) |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | The ID of the region. |
| iso\_alpha\_3 | string | readable | Country code in the format ISO 3166-1 alpha-3. |
| name | string | readabledefault\_field | Name of the region. |
| parent\_id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | ID of the parent region. |
| type | string | readable | Type of region. |
