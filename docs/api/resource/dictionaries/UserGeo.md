# UserGeo

## /api/v2/user\_geo.json

The resource that enables you to get information about geographical regions specified by users in social network.

### GET

Request example:

```http

   GET /api/v2/user_geo.json
```

Response example:

```http

   {
       "items": [{\
           "id": 5499,\
           "name": "Abaza"\
       }, {\
           "id": 7002,\
           "name": "Abai"\
       }, {\
           ...\
       }],
       "count": 3732,
       "offset": 0
   }
```

The following GET parameters enable you to filter data:

- limit - The number of the returned objects. Default value is 20. Maximum value is 50.

```http

    /api/v2/user_geo.json?limit=10
```

- offset - The offset starting point in the list. Default value is 0.

```http

    /api/v2/user_geo.json?limit=5&offset=15
```

Filters:

- \_id - geographical region id:

```http

    /api/v2/user_geo.json?_id=7002
    /api/v2/user_geo.json?_id__in=7002,5499
```

- \_q - full text search by name:

```http

    /api/v2/user_geo.json?_q=New York
```
