# BannerMassAction

## /api/v2/banners/mass\_action.json

The resource enables you to update statuses of a large number of banners simultaneously (200 banners per request maximum). The process is transaction-based, so if the update of at least one object ends with an error, then none of the updates is applied.

Used object: [BannerMassAction](https://ads.vk.com/en/doc/api/object/BannerMassAction)

### POST

The request body has the following structure:

```http

   [\
       {\
           "id": <banner_id\>,\
           "status": <new_status_value\>\
       },\
       {\
           ...\
       },\
   ]
```

where <banner\_id> is a banner identifier; <new\_status\_value> are status new value. The "id" field is required.
You can change properties (parameters) of a deleted banner. To do this, restore the banner by specifying the "blocked" or "active" value in the "status" field of the request.
Request example:

```http

   POST /api/v2/banners/mass_action.json

   [\
       {\
           "id": 123456,\
           "status": "active",\
       },\
       {\
           "id": 234567,\
           "status": "blocked"\
       },\
   ]
```

A successful request returns a response with status 204.

Possible errors:

1. The maximum number of banners per request is exceeded:

```http

   {
       "error": {
           "message": "Too much items. Limit is 200",
           "code": "limit_exceeded"
       }
   }
```

2. The request contains non-existent banners:

```http

   {
       "error": {
           "message": "Unknown banners: 144, 42, 100500",
           "code": "unknown_banners"
       }
   }
```

3. An attempt to update a deleted banner without specifying its status:

```http

   {
       "error": {
           "banners": [\
               "arguments": {\
                   "id": <banner_id\>\
               }\
               "code": "banner_deleted",\
               "message": "Banner is deleted",\
               "fields": {}\
           ]           "message": "Validation failed",
           "code": "validation_failed"
       }
   }
```

where <banner\_id> is the identifier of the affected banner.
