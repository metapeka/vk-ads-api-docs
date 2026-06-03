# LeadFormNotification

An object describing a lead form event notification.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| type | string | readablewritablerequired<br>choices = <br>- new\_lead \- New lead received | Event type that triggers notifications |
| conditions | object | readablewritable | Condition settings that must be met for a notification to be sent for the event. For `type=new_lead`, an empty object `{}` is expected. |
| destinations | list of [Destination](https://ads.vk.com/en/doc/api/object/LeadFormNotificationDestination) | readablewritablerequiredmax\_items=16 | List of destinations where the notification is sent |
