# RemarketingCounters

## /api/v2/remarketing/counters.json

The resource that enables you to manage the [Top@Mail.ru](https://top.mail.ru/) counters that user adds to the pool of the data sources that can be used on target audiences. Such counters are used for targeting the users who visited a site where the counter is installed.

Used object: [RemarketingCounter](https://ads.vk.com/en/doc/api/object/RemarketingCounter)

### GET

The request returns a list of all counters that were added to the data sources.

Request example:

```http
  GET /api/v2/remarketing/counters.json
```

Response example:

```http
  {
    "items":[
      {
        "status":"active",
        "working":true,
        "name":"Counter 1",
        "counter_id":2000000,
        "created":"2015-07-31 14:40:12",
        "system_status":"active",
        "flags":[],
        "id":17668
      },
      {
        "status":"active",
        "working":false,
        "name":"Counter 2",
        "counter_id":2500000,
        "created":"2017-03-21 13:25:00",
        "system_status":"active",
        "flags":[
          "cookie_sync"
        ],
        "id":51645
      }
    ]
  }
```

Filters

- _counter_id - Top counter id

```http
    /api/v2/remarketing/counters.json?_counter_id=250000
    /api/v2/remarketing/counters.json?_counter_id__in=250000,250001
```

- _domain - counter domain

```http
    /api/v2/remarketing/counters.json?_domain=example.com
    /api/v2/remarketing/counters.json?_domain__in=example.com,example2.com
```

### POST

The request creates a new counter or adds an existing one to the data sources.

Example of request for creating a counter:

```http
  POST /api/v2/remarketing/counters.json
  {
    "name":"New counter",
    "url":"http://example.com",
    "email":"test@example.com",
    "password":"12345678"
  }
```

Example of request for adding a counter to the available data sources:

```http
  POST /api/v2/remarketing/counters.json
  {
    "counter_id": 2000500,
    "name":"New counter",
    "flags": ["cookie_sync"]
  }
```

A counter can be added to the pool only by the counter owner (their email is the same as the one specified in the VK Ads account) or a user who has access to the counter (the owner can grant access to the counter by specifying the other person's email in their VK Ads profile). If you do not have access to the counter you add, it will be registered as inactive ("system_status" = "blocked") and an approval request will be sent to the owner. If the owner approves the operation, the counter will be activated automatically.

Response example:

```http
  {
    "status":"active",
    "working":null,
    "name":"New counter",
    "counter_id":2000000,
    "created":"2015-07-31 14:40:12",
    "system_status":"active",
    "flags":[],
    "id":17668
  }
```

Response status codes:

200 - The counter successfully created/added.

400 - One of the following events:

- The request cannot be validated. Error code is "validation_failed".
- An attempt to create/add a counter that has already been added. Error code is "duplicate_error".
- Error when creating a counter in [Top@Mail.ru](https://top.mail.ru/). Error code is "top_error".

404 - The counter with the specified "counter_id" does not exist. This error can occur only when adding a counter.

Error example(s):

```http
  {"error": {"code": "validation_failed", "fields": { <fields with errors> }}}
 - Data error.

  {"error": {"code": "duplicate_error", "message": "Counter with counter_id 12345 already exists"}}
 - An attempt to create/add a counter that already exists/has been added.

  {"error": {"code": "top_error", "message": "<error description>"}}
 - Error when creating a counter in [Top@Mail.ru](https://top.mail.ru).
```
