# RemarketingCounter

## /api/v2/remarketing/counters/<counter_id>.json

The resource enables you to manage the [Top@Mail.ru](mailto:Top@Mail.ru) counter. Such counters are used for targeting the users who visited a site where the counter is installed.

Used object: [RemarketingCounter](https://ads.vk.com/en/doc/api/object/RemarketingCounter)

### GET

The request returns data on the specified counter.

Request example:

```http
  GET /api/v2/remarketing/counters/2000000.json
```

Response example:

```http
  {
    "status":"active",
    "working":true,
    "name":"First counter",
    "counter_id":2000000,
    "created":"2015-07-31 14:40:12",
    "system_status":"active",
    "flags":[],
    "id":17668
  }
```

### POST

The request modifies parameters of the specified counter.

Request example:

```http
  POST /api/v2/remarketing/counters/2000000.json
  {
    "name":"New name",
    "flags":["cookie_sync"],
  }
```

where "2000000" is the "counter_id" field of the counter.

Response example:

```http
  {
    "status":"active",
    "working":null,
    "name":"New name",
    "counter_id":2000000,
    "created":"2015-07-31 14:40:12",
    "system_status":"active",
    "flags":["cookie_sync"],
    "id":17668
  }
```

Response status codes:

200 - The counter was successfully modified.

400 - Validation error.

404 - The counter cannot be found.

Error example(s):

```http
  {"error": {"code": "validation_failed", "fields": { <fields with errors> }}}
 - Data error.
```

### DELETE

The request deletes the specified counter from the pool of the available data sources. Only the counters that are not currently used in an audience configuration or provide basis for a lookalike can be deleted.

Request example:

```http
  DELETE /api/v2/remarketing/counters/2000000.json
```

where 2000000 is the "counter_id" field of the counter.

Response status codes:

204 - The counter was deleted.

404 - The counter cannot be found among user counters.

409 - The counter is used in an audience configuration or lookalike.
