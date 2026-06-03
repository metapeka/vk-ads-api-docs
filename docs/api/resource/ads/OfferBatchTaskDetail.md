# OfferBatchTaskDetail

## /api/v2/remarketing/pricelists/<pricelist\_id>/batch/<task\_id>.json

Method to get detailed information on product batch create, update, delete task result.

Use [OfferBatchTaskCreate](https://ads.vk.com/en/doc/api/resource/OfferBatchTaskCreate) to submit new tasks.

Batch task execution report is available by:

```js
GET /api/v2/remarketing/pricelists/<pricelist_id>/batch/<task_id>.json
```

Response example:

```http
{
   "errors":[\
      {\
         "code":"JSON_LINE_DECODE_ERROR",\
         "count":1,\
         "errors":[\
            {\
               "comment":"",\
               "created":"2022-08-30 17:01:24",\
               "element":null,\
               "message":"Failed to parse JSON line",\
               "offer_id":"",\
               "offer_name":"",\
               "pricelist_id":26825\
            }\
         ],\
         "event":"feed_failure",\
         "field":"",\
         "last_start_ts":1661868084,\
         "pricelist_id":26825\
      },\
      {\
         "code":"DYNAMIC_IMAGES_PICTURE_NOT_FOUND",\
         "count":1,\
         "errors":[\
            {\
               "comment":"",\
               "created":"2022-08-30 17:01:24",\
               "element":"http://example.org/1.jpg",\
               "message":"Picture download error HTTP 404 Not found",\
               "offer_id":"o1",\
               "offer_name":"",\
               "pricelist_id":26825\
            }\
         ],\
         "event":"offer_error",\
         "field":"picture",\
         "last_start_ts":1661868084,\
         "pricelist_id":26825\
      }\
   ],
   "id":10,
   "status":"done"
}
```

In this response, `errors` attribute contains a grouped list of errors and warnings during batch task execution. Every error contains:

- `event` – error level;
- `code` – error code;
- `field` – corresponding field name;
- `count` – count of similar errors;
- `errors` – particular error examples.

The `event` can be:

- `feed_failure` – critical error, failing entire batch task execution, such as broken JSON.
- `offer_error` – error resulting a particular product could not be validated and saved.
- `offer_warning` – product saved, but with some assumptions, inaccuracies or recommendations.

Possible response codes:

- 200 – batch task found.
- 404 – catalog or batch task not found, or catalog has source type other than "Updated through API".
