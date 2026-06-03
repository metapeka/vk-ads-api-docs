# PackagesPads

## /api/v2/packages\_pads.json

The resource enables you to collect data on the sites used in the default package targeting.

Used object: [PackagePad](https://ads.vk.com/en/doc/api/object/PackagePad)

### GET

Request example:

```http

   GET /api/v2/packages_pads.json
```

Response example:

```http

    {
        "items": [\
            {\
                "eye_url": {\
                   "url": "https://e.mail.ru/cgi-bin/msglist",\
                   "id": 9,\
                   "description": "View in the Mail"\
                },\
                "description": "Social networks and services (240x400 banner)",\
                "id": 6142,\
                "name": "odkl_messages_abstract"\
            }\
       ]
   }
```
