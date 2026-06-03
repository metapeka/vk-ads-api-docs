# LeadFormAgreementTemplateDocument

An object describing the standard lead form user agreement.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| company\_title | string | readablewritablerequiredmax\_length=255 | For individuals: full name. For legal entities: the company's (organization's) legal name |
| registration\_address | string | readablewritablerequiredmax\_length=255 | For individuals: residential registration address. For legal entities: the company's (organization's) registered address |
| email | email | readablewritablemax\_length=255 | Company email |
| ogrn\_or\_inn | string | readablewritablemax\_length=32 | OGRN or INN (legal entities only) |
