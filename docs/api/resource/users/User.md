# User

## /api/v3/user.json

A resource that allows you to collect basic information about the user.

Used object: [User](https://ads.vk.com/en/doc/api/object/User)

### GET

Request example:

```http

   GET /api/v3/user.json
```

Response example:

```http

   {
       "username": "ya.user@bk.ru",
       "status": "active",
       "language": "ru",
       "firstname": "Pavel",
       "lastname": "Kalashnikov",
       "info_currency": "RUB",
       "id": 55555555,
       "currency": "RUB",
       "email": "ya.user@bk.ru",
       "types": [\
           "advert"\
       ],
       "email_settings": [\
            {\
                "type": "user",\
     	        "email": "ya.user@bk.ru"\
           },\
           {\
                "type": "additional",\
                "email": "ya.user.additional@bk.ru"\
           }\
       ],
       "mailings": {
           "news": {
               "email": []
           },
           "adv_campaigns": {
               "email": [\
                   "ya.user@bk.ru"\
               ]
           },
           "lead_ads": {
               "email": []
           },
           "finance": {
               "email": [\
                   "ya.user@bk.ru"\
               ]
           },
           "management_rule": {
               "email": [\
                   "ya.user@bk.ru"\
               ]
           },
           "event": {
               "email": [\
                   "ya.user@bk.ru",\
                   "ya.user.additional@bk.ru"\
               ]
           },
           "moderation": {
               "email": []
           },
           "other": {
               "email": []
           }
           "api_changes": {
               "email": []
           }
       },
       "regions": {
           "allowed": [1,2,3,-5,-6,-7,...],
           "required": [-5,-6,-7,...],
           "required_one_of": [1,2,3,...]
       },
       "ord": {
           "name": "string",
           "phone": "+72219494144448",
           "inn": "862583085719",
           "foreign_epayment_method": "string",
           "foreign_oksm_country_code": "strin",
           "foreign_registration_number": "string",
           "foreign_inn": "string",
           "site": "https://example.com/bla"
        }
   }
```

### POST

Request example:

```http

   POST /api/v3/user.json

   {
       "info_currency": "USD",
       "language": "en",
       "mailing": {
           "news": {
               "email": [\
                   "ya.user@bk.ru",\
                   "ya.user.additional@bk.ru"\
               ],
           },
           "lead_ads": {
               "email": [],
           },
           "adv_campaigns": {
               "email": [\
                   "ya.user@bk.ru"\
               ]
           }
       },
       "status": "active",
       "email_settings": [\
            {\
                "type": "user",\
     	        "email": "ya.user@bk.ru"\
           },\
           {\
                "type": "additional",\
                "email": "ya.user.additional@bk.ru"\
           }\
       ],
       "additional_info": {
           "phone": "89153724330",
           "name": "Ivanov Ivan Ivanovich"
       },
       "ord": {
           "name": "string",
           "phone": "+17038945571",
           "inn": "041339365002",
           "foreign_epayment_method": "string",
           "foreign_oksm_country_code": "strin",
           "foreign_registration_number": "string",
           "foreign_inn": "string",
           "site": "https://example.com/bla
      }
   }
```
