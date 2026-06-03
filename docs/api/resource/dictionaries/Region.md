# Region

## /api/v2/regions.json

Resource that allows you to get information about geographical regions.

Used object: [Region](https://ads.vk.com/en/doc/api/object/Region)

### GET

Request returns information about the regions.

Example request:

```http

  GET /api/v2/regions.json
```

Example answer:

```http

  {
    "count": 5561,
    "items": [\
       {\
           "parent_id": -1,\
           "id": 188,\
           "name": "Russia",\
           "flags": ["rb_active","geo_tree_extended","geo_tree"]\
       }, {\
           "parent_id": 188,\
           "id": 53,\
           "name": "Krasnodar region",\
           "flags": ["rb_active","geo_tree_extended","geo_tree"]\
       }, {\
           ...\
       }\
    ]
  }
```

Filters

- \_id - Region's ID

```http

    /api/v2/regions.json?_id=53
    /api/v2/regions.json?_id__in=53,188
```

- \_parent\_id - Parent's region ID

```http

    /api/v2/regions.json?_parent_id=-1
    /api/v2/regions.json?_parent_id__in=-1,188
```

- \_q - full text search by region name

```http

    /api/v2/regions.json?_q=Sochi
```

- \_flags - search by flags in the region. Possible value: geo\_tree, geo\_tree\_extended, rb\_active. Multi-flag search finds those regions that have all the specified flags

```http

    /api/v2/regions.json?_flags=geo_tree_extended
    /api/v2/regions.json?_flags__in=geo_tree_extended,rb_active
```

In API [packages](https://ads.vk.com/en/doc/api/resource/Packages) in field options the following structure can come:

```http

   "items": [\
       {\
           "id": 613\
           "options": [\
              {\
                  "targetings": [\
                      {\
                          "name": "regions",\
                          "filter": {\
                              "flags": ["geo_tree", "rb_active"]\
                          }\
                      }\
                  ]\
              }\
           ]\
       }\
   ]
```

This means that regions that have flags "geo\_tree" and "rb\_active" are allowed in package 613. To get a list of such regions, you need to request an API with a filter on the specified flags. In this case it will be the following query:

```http

    /api/v2/regions.json?_flags__in=geo_tree,rb_active
```

API supports the HTTP header "Accept-Language". In the case of a non-empty value, the data is returned in the preferred supported language.

Currently, the following languages are supported: Russian, English. By default, the data is given in English. For example:

- When "Accept-Language" = "" data will be returned in English;

- When "Accept-Language" = "ru-RU,ru;q=0.9,en-US;q=0.8" data will be returned in Russian;

- When "Accept-Language" = "de,en-US;q=0.8,ru;q=0.5" data will be returned in English.
