# SegmentRelation

The object shows the relationship between the segment and its data source or embedded segment.

Used in resources: [SegmentRelations](https://ads.vk.com/en/doc/api/resource/SegmentRelations), [SegmentRelationsDelete](https://ads.vk.com/en/doc/api/resource/SegmentRelationsDelete), [SegmentRelation](https://ads.vk.com/en/doc/api/resource/SegmentRelation)

Used in objects: [Segment](https://ads.vk.com/en/doc/api/object/Segment)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Relationship identifier. |
| object\_id | integer | readablewritabledefault\_fieldcreate\_onlymin\_value=-2147483647max\_value=2147483647 | Object identifier. |
| object\_type | string | readablerequiredwritabledefault\_fieldcreate\_only<br>choices = <br>- remarketing\_player \- Users who run apps on the platform.<br>- interest\_categories \- Interest categories.<br>- remarketing\_vk\_app \- Users of the VKontakte mobile app.<br>- remarketing\_inapp\_event \- App events.<br>- remarketing\_search\_phrases \- List of search phrases.<br>- remarketing\_campaign\_list \- Campaign list.<br>- remarketing\_local\_geo \- Local geography.<br>- interest\_visits \- Interest visits<br>- remarketing\_game\_player \- Users of the Odnoklassniki mobile app.<br>- remarketing\_mobile\_app \- Mobile app users.<br>- remarketing\_vk\_group \- Users who joined a group in VKontakte.<br>- interest \- Interests.<br>- remarketing\_group \- Users who joined a group in Odnoklassniki.<br>- remarketing\_users\_list \- List of user identifiers.<br>- remarketing\_user\_geo \- User geography.<br>- remarketing\_pricelist \- Dynamic remarketing price list.<br>- remarketing\_lookalike\_audience \- Lookalike audience.<br>- segment \- Embedded segment.<br>- remarketing\_game\_payer \- Users who bought the Odnoklassniki mobile app.<br>- remarketing\_app\_category \- Age.<br>- age \- Embedded segment.<br>- remarketing\_counter \- [Top@Mail.ru](https://top.mail.ru/) counter.<br>- remarketing\_custom\_audience \- Typical audience.<br>- remarketing\_payer \- Users who paid on the platform. | Embedded object type. |
| params | object | readablewritable | Data source parameters. For more information about parameters for different data source types, see [this article](https://ads.vk.com/en/doc/api/info/SegmentParams). |
