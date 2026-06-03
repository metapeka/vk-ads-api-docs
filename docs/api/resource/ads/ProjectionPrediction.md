# ProjectionPrediction

## /api/v3/projection.json

A resource that returns an audience reach forecast depending on the event cost.

Object used: [ProjectionPrediction](https://ads.vk.com/en/doc/api/object/ProjectionPrediction)

### POST

Getting a forecast for a campaign or packages

Request example

```http

   POST /api/v3/projection.json
   {
       "package_ids": [959, 999],
       "targetings":{
           "pads": [24567, 24568, 33649, 33652]
       }
   }
```

Response example

```http

   {
       "cr_ctr": [\
           {\
               "package_id": 999,\
               "histogram_id": 1,\
               "avg_cr": null,\
               "avg_ctr": 0.005839118541681293\
           },\
           {\
               "package_id": 959,\
               "histogram_id": 2,\
               "avg_cr": null,\
               "avg_ctr": 0.005123368281061198\
           }\
       ],
       "histograms": [\
           {\
               "id": 1,\
               "histogram": [\
                   ...\
                   {\
                       "price": 52.57,\
                       "uniqs": 50589000,\
                       "share": 51\
                   },\
                   {\
                       "price": 53.56,\
                       "uniqs": 50918000,\
                       "share": 51\
                   },\
                   ...\
               ]\
           },\
           {\
               "id": 2,\
               "histogram": [\
                   ...\
                   {\
                       "price": 120.48,\
                       "uniqs": 72347000,\
                       "share": 81\
                   },\
                   {\
                       "price": 121.4,\
                       "uniqs": 72420000,\
                       "share": 82\
                   },\
                   ...\
               ]\
           }\
       ]
   }
```

In the request, you must specify either campaign\_id or package\_ids.

If a campaign is specified, the forecast will take its history into account.

The campaign's existing targetings are not taken into account when building the forecast; you must pass them in the request.

If a list of package IDs is specified, a forecast will be built for a new campaign in each of the specified packages.

Under the targetings key, you can specify only the [targetings supported by the forecasting service](https://ads.vk.com/en/doc/api/object/ProjectionTargetings).

Only the pads targeting is required; its possible values are listed for each package in package.options.targetings.pads.values.

In targetings.pads you can specify any pads, but the forecast will be built only for the intersection of the submitted pads and the pads available for the package.

If the intersection is empty, the response for that package will contain an empty histogram.

The recommended effective bid is the one that reaches 75% or more of the audience.

The forecast returns information only for the impression price (priced\_event\_type = 0).

To calculate the cost for other event types, use:

- `price / (avg_ctr * avg_cr * 1000)` for the install event (priced\_event\_type = 7).
- `price / (avg_ctr * 1000)` for all other events.
