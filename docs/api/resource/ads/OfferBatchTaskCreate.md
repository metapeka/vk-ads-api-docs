# OfferBatchTaskCreate

## /api/v2/remarketing/pricelists/<pricelist\_id>/batch.json

Method used to batch create, update and delete products in the catalog, without full update from the source feed.

Use [OfferBatchTaskDetail](https://ads.vk.com/en/doc/api/resource/OfferBatchTaskDetail) to get detailed result of batch update.

### Gain API access

You need to switch your catalog source type to "Updated through API" to use this API. It can be done by request to technical support.

As a result, catalog will be excluded from periodic update schedule from the source feed, the API will become the only source of updates.

### POST

Submits a batch update task. The request body must be a Newline-Delimited JSON objects, where every JSON object is a single update. Line breaks inside JSON objects are not allowed.

Request body size limit is 200 MB.

Submitted tasks will start consequentially in creation order.

Every JSON object must consist of two attributes: method – type of action; data – object with attributes of updated product.

```http
{"method": "<action>", "data":<fields>}
{"method": "<action>", "data":<fields>}
{"method": "<action>", "data":<fields>}
```

Supported `method` values:

- `PUT` – create or update all attributes of provided product. The `data` property contains full set of attributes of created or updated product (it will be completely replaced in the database).
- `DELETE` – delete the product. The `data` object must contain the only `id` attribute of the product to be deleted.

Possible response codes:

- 201 – batch task had been enqueued.
- 400 – request validation error or response body too large.
- 404 – catalog not found or has source type other than "Updated through API".

Attribute names completely match ones supported in CSV feeds. Example `data` object (line breaks are just for readability, they are prohibited in JSON object inside real request):

```http
{
   "id":"DB_1",
   "title":"Dog Bowl In Blue",
   "ios_url":"example://electronic/db_1",
   "ios_app_store_id":"123",
   "ios_app_name":"Electronic Example iOS",
   "android_url":"example://electronic/db_1",
   "android_package":"com.electronic.example",
   "android_app_name":"Electronic Example Android",
   "windows_phone_url":"example-windows://electronic/db_1",
   "windows_phone_app_id":"64ec0d1b-5b3b-4c77-a86b-5e12d465edc0",
   "windows_phone_app_name":"Electronic Example Windows",
   "description":"Solid plastic Dog Bowl in marine blue color",
   "google_product_category":"Animals > Pet Supplies",
   "product_type":"Bowls & Dining > Food & Water Bowls",
   "link":"http://www.example.com/bowls/db-1.html",
   "image_link":"https://www.example.com/images/product_image_template.png?id=1",
   "condition":"new",
   "availability":"in stock",
   "price":"300.99 RUR",
   "sale_price":"",
   "sale_price_effective_date":"",
   "gtin":"",
   "brand":"Example",
   "mpn":"",
   "item_group_id":"DB_GROUP_1",
   "gender":"",
   "age_group":"",
   "color":"",
   "size":"",
   "shipping":"UK::Standard:9.95 EUR",
   "custom_label_0":"Made in Waterford, IE",
   "additional_image_link":"https://test.com/add_img1,https://test.com/add_img2"
}
```

Example request:

```http
POST /api/v2/remarketing/pricelists/<pricelist_id>/batch.json
{"method": "PUT", "data":{"id": "offer1", "product_type": "category1", "title": "Offer1","link": "http://example.org/1", "image_link": "http://example.org/1.jpg", "price": "100 RUB"}}
{"method": "PUT", "data":{"id": "offer2", "product_type": "category2", "title": "Offer2","link": "http://example.org/2", "image_link": "http://example.org/2.jpg", "price": "200 RUB"}}
{"method": "DELETE", "data":{"id": "offer3"}}
```

In this example, offer1 and offer2 products are updated or created, offer3 product is deleted.

Example response:

```http
HTTP 201
[\
    {"id": 6, "status": "pending"}\
]
```

### GET

Lists executing and recently complete tasks with their execution statuses.

```http
GET /api/v2/remarketing/pricelists/<pricelist_id>/batch.json
```

Example response:

```http
{
    "items": [\
        {\
            "id": 1,\
            "status": "done"\
        },\
        {\
            "id": 3,\
            "status": "error"\
        },\
        {\
            "id": 5,\
            "status": "process"\
        },\
        {\
            "id": 6,\
            "status": "pending"\
        },\
        {\
            "id": 7,\
            "status": "pending"\
        }\
    ]
}
```

In this example: task 1 is complete (including, with errors or warnings); task 3 is failed (with runtime error); task 5 is in progress right now, tasks 6 and 7 are pending execution in queue.

Possible response codes:

- 200 – list batch task for given catalog.
- 404 – catalog not found or has source type other than "Updated through API".

Use [OfferBatchTaskDetail](https://ads.vk.com/en/doc/api/resource/OfferBatchTaskDetail) to get detailed result of batch update.
