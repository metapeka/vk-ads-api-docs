# LeadFormResultInfo

An object describing the information for the final screen of a lead form.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| title | string | readablewritablerequiredmax\_length=25 | Title |
| description | string | readablewritablemax\_length=160 | Description |
| site\_url | url | readablewritablemax\_length=2000 | Company website URL |
| phone | phone | readablewritable | Phone number in the format +xxxxxxxxxxx |
| promo\_code | [PromoCode](https://ads.vk.com/en/doc/api/object/LeadFormPromoCode) | readablewriteable | Promo code for completing the form |
