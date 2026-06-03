# Segment

Audience segment.

Used in resources: [Segments](https://ads.vk.com/en/doc/api/resource/Segments), [Segment](https://ads.vk.com/en/doc/api/resource/Segment)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| campaign\_ids | list of integer | readablemin\_value=-2147483647max\_value=2147483647 | IDs of the campaigns targeting the segment. |
| created | datetime | readabledefault\_field | Date and time of segment creation. |
| flags | list of string | readabledefault\_field | Flags. "sharing\_forbidden" - segment cannot be shared with other users because it contains external data sources and/or segments. |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Segment identifier. |
| name | string | readablerequiredwritabledefault\_field | Segment name. |
| pass\_condition | integer | readablerequiredwritabledefault\_fieldmax\_value=2147483647 | Condition for including user in a segment depending on the number of segment's data sources the user belongs to. Minimum value is "1" - the user must belong to at least one data source in the segment. Maximum value is "relations\_count" - the user must belong to every data source in the segment. |
| relations | list of [SegmentRelation](https://ads.vk.com/en/doc/api/object/SegmentRelation) | readablerequiredwritablecreate\_only | Data sources in the segment. |
| relations\_count | integer | readablemax\_value=2147483647 | Number of data sources in the segment. |
| updated | datetime | readabledefault\_field | Date and time of segment update. |
| users | list of [SegmentUser](https://ads.vk.com/en/doc/api/object/SegmentUser) | readable | Users who can access the segment. |
