# AdPlanMassAction

## /api/v2/ad\_plans/mass\_action.json

A resource that allows you to bulk update campaign data (no more than 200 campaigns at a time).

Used object: [AdPlanMassAction](https://ads.vk.com/en/doc/api/object/AdPlanMassAction)

### POST

The request body must contain a structure like:

```http
[\
  {\
    "id": 2147483647,\
    "status": "active",\
    "budget_limit_day": 10000,\
    "date_start": "2022-11-27",\
    "date_end": "2022-11-27",\
    "max_price": 21474836.47\
  }\
]
```

Request example:

```http
POST /api/v2/ad_plans/mass_action.json
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

1. Exceeding the limit of campaigns in the request:

```http
{
  "error": {
    "message": "Too much items. Limit is 200",
    "code": "limit_exceeded"
  }
}
```

2. The request contains non-existent campaigns:

```http
{
  "error": {
    "message": "Unknown ad_plans: 144, 42, 100500",
    "code": "unknown_ad_plans"
  }
}
```
