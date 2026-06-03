# TargetingsTree

## /api/v2/targetings\_tree.json

The resource enables you to get a tree of user interests. Note that collecting data on some specific interests may be available only in some packages.

Used object: [TargetingsTree](https://ads.vk.com/en/doc/api/object/TargetingsTree)

### GET

Request example:

```http

   GET /api/v2/targetings_tree.json
```

Response example:

```http

   [\
       {\
            "interests_short": [\
               {\
                   "children": [\
                       {\
                           "id": 8490,\
                           "name": "Country life"\
                       },\
                       {\
                           "id": 10255,\
                           "name": "Beekeeping"\
                       },\
                       {\
                           "id": 10257,\
                           "name": "Gardening utensils"\
                       },\
                       {\
                           "id": 10256,\
                           "name": "Seeds and sprouts"\
                       }\
                   ],\
                   "id": 7299,\
                   "name": "Household"\
               },\
               {\
                   "children": [\
                       {\
                           "id": 9291,\
                           "name": "Aquarium"\
                       }\
                   ],\
                   "id": 7304,\
                   "name": "Pets"\
               }\
            ],\
            "interests_soc_dem": [\
               {\
                   "children": [\
                       ...\
                   ],\
                   "id": 7328,\
                   "name": "TV groups"\
               },\
               ...\
            ],\
            "interests_stable": [\
               ...\
            ],\
            "interests": [\
               ...\
            ]\
       }\
   ]
```

By default, the response contains 4 fields:

- "interests" (basic interests)
- "interests\_soc\_dem" (extended socio-demographic characteristics)
- "interests\_stable" (persisting interests)
- "interests\_short" (spontaneous interests)
To get specific subtrees of interests, use the "targetings" optional parameter whose value is specified as a comma-separated list of the required tree names: "interests", "interests\_stable", "interests\_short", "interests\_soc\_dem".

Request example:

```http

   GET /api/v2/targetings_tree.json?targetings=interests_soc_dem,interests_short
```

Response example:

```http

   [\
       {\
            "interests_short": [\
               ...\
            ],\
            "interests_soc_dem": [\
               ...\
            ]\
       }\
   ]
```
