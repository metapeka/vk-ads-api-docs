# LeadFormNotificationDestination

An object describing where lead form notifications are sent.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| type | string | readablewritablerequired<br>choices = <br>- email \- Email<br>- vk \- VK Messenger | Destination type for sending notifications |
| settings | object | readablewritable | Notification delivery settings. For `type=email`, an object like `{"email": "email@address.com"}` is expected. For `type=vk`, `settings` is not required. |
