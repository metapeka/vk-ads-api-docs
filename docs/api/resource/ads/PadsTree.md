# PadsTree

## /api/v2/pads\_trees.json

The resource provides information about pads trees used for targeting the pads specified when campaign is created. Pads trees help to visualize the connections between the end nodes IDs and physical locations of the pads.

Used object: [PadsTree](https://ads.vk.com/en/doc/api/object/PadsTree)

### GET

Request example:

```http

   GET /api/v2/pads_trees.json
```

Response example:

```http

    {
        "items": [\
          {\
            "tree": [\
              {\
                "name": "Desktop",\
                "children": [\
                  {\
                    "name": "MRG",\
                    "children": [\
                      {\
                        "id": 76765\
                      },\
                      {\
                        "id": 76766\
                      },\
                      {\
                        "id": 76767\
                      }\
                    ]\
                  },\
                  {\
                    "id": 76878\
                  }\
                ]\
              },\
              {\
                "name": "Mobile",\
                "children": [\
                  {\
                    "name": "MRG",\
                    "children": [\
                      {\
                        "id": 76879\
                      },\
                      {\
                        "id": 76880\
                      },\
                      {\
                        "id": 76881\
                      }\
                    ]\
                  },\
                  {\
                    "id": 76882\
                  }\
                ]\
              }\
            ],\
            "id": 393\
          },\
          {\
            "tree": [\
              {\
                "name": "Desktop",\
                "children": [\
                  {\
                    "name": "MRG",\
                    "children": [\
                      {\
                        "id": 76920\
                      },\
                      {\
                        "id": 76921\
                      },\
                      {\
                        "id": 76922\
                      }\
                    ]\
                  },\
                  {\
                    "id": 76923\
                  }\
                ]\
              },\
              {\
                "name": "Mobile",\
                "children": [\
                  {\
                    "name": "MRG",\
                    "children": [\
                      {\
                        "id": 76924\
                      },\
                      {\
                        "id": 76925\
                      },\
                      {\
                        "id": 76926\
                      }\
                    ]\
                  },\
                  {\
                    "id": 76927\
                  }\
                ]\
              }\
            ],\
            "id": 396\
          },\
        ]
   }
```
