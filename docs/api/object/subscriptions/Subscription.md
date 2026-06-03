# Subscription

An object providing information about a user's subscription to receive notifications about changes to a resource.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| callback\_url | url | readablewritablerequired | The address to which the event notification will be sent. Must use the https:// scheme. |
| id | id | readable | Subscription identifier. |
| resource | string | readablewritablerequired<br>choices = <br>- BANNER \- Ads<br>- AD\_GROUP \- Ad groups<br>- LEAD \- Form leads<br>- LEAD\_FORM \- Lead forms<br>- SEGMENT \- Segments<br>- USER \- User | The name of the resource for which the subscription is created to receive notifications about changes to all of its objects. |
