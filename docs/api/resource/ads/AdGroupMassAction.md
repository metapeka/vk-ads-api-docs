# AdGroupMassAction

## /api/v2/ad\_groups/mass\_action.json

A resource that allows you to bulk update ad group data (no more than 200 groups at a time). The update is transactional: if an error occurs in at least one group, none of the changes will be applied.

### POST

The request body must contain a structure like:

```http

   [\
       {\
           "id": <ad_group_id>,\
           "status": <new_status_value>,\
           "max_price": <new_max_price_value>\
       },\
       {\
           ...\
       },\
   ]
```

where <ad\_group\_id> is the group identifier; <new\_status\_value> is the new status value; <new\_max\_price\_value> is the new max price value. The "id" field is required.

You can change values of a deleted group, but you will need to restore it. When updating a deleted group, you must set the "status" field to either "blocked" or "active".

Request example:

```http
POST /api/v2/ad_groups/mass_action.json
[\
  {\
    "id": 123456,\
    "status": "active",\
    "max_price": 200\
  },\
  {\
    "id": 234567,\
    "status": "blocked"\
  }\
]
```

If successful, the response will have status 204.

Possible errors:

1. Exceeding the limit of groups in the request:

```http
{
  "error": {
    "message": "Too much items. Limit is 200",
    "code": "limit_exceeded"
  }
}
```

2. The request contains non-existent groups:

```http
{
  "error": {
    "message": "Unknown ad_groups: 144, 42, 100500",
    "code": "unknown_ad_groups"
  }
}
```

3. Attempt to update a deleted group without updating its status:

```http
{
  "error": {
    "ad_groups": [\
      {\
        "arguments": {\
          "id": "<ad_group_id>"\
        },\
        "code": "ad_group_deleted",\
        "message": "AdGroup is deleted",\
        "fields": {}\
      }\
    ],
    "message": "Validation failed",
    "code": "validation_failed"
  }
}
```

where <ad\_group\_id> is the identifier of the group where the error occurred.

5. Exceeding the maximum allowed max price in the package:

```http
{
  "error": {
    "ad_groups": [\
      {\
        "arguments": {\
          "id": <ad_group_id>\
        },\
        "code": "validation_failed",\
        "message": "Validation failed",\
        "fields": {\
          "max_price": {\
            "message": "Value is more than maximum allowed",\
            "code": "max_value",\
            "arguments": {\
              "max_value": "<max_available_value>"\
            }\
          }\
        }\
      }\
    ],
    "message": "Validation failed",
    "code": "validation_failed"
  }
}
```

where <ad\_group\_id> is the identifier of the group where the error occurred; <max\_available\_value> is the maximum allowed max price.

Errors can be returned for multiple groups at the same time:

```http
{
  "error": {
    "ad_groups": [\
      {\
        "arguments": {\
          "id": 3\
        },\
        "code": "validation_failed",\
        "message": "Validation failed",\
        "fields": {\
          "max_price": {\
            "message": "Value is more than maximum allowed",\
            "code": "max_value",\
            "arguments": {\
              "max_value": "<max_available_value>"\
            }\
          }\
        }\
      },\
      {\
        "arguments": {\
          "id": 2\
        },\
        "code": "ad_group_deleted",\
        "message": "AdGroup is deleted",\
        "fields": {}\
      }\
    ],
    "message": "Validation failed",
    "code": "validation_failed"
  }
}
```
