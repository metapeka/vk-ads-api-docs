# SharingKey

## /api/v2/sharing_keys.json

The resource enables user to create data sources [sharing key](https://target.my.com/adv/help/shared_sources/) .

Used object: [SharingKey](https://ads.vk.com/en/doc/api/object/SharingKey)

### GET

Return a list of all sharing keys, created by user.

Request example:

```http
   GET /api/v2/sharing_keys.json
```

Additional GET params:

- _key - sharing key.

Example of request with additional params:

```http
   GET /api/v2/sharing_keys.json?_key=aBcDe432
```

Response example:

```http
  {
    "items": [
      {
        "sharing_url": "https://ads.vk.com/segments/external/activate_key?key=aBcDe432",
        "sources": [{
             "object_type": "users_list",
             "object_id": 1
          }
        ],
        "price": "0",
        "sharing_key": "aBcDe432",
        "is_marketplace": false,
        "send_email": null,
        "payment_type": "free",
        "owner": {
          "username": "your.user@mail.ru",
          "id": 4000000
        },
        "type": "private",
        "users": [
          {
             "username": "shared.user@mail.ru",
             "id": 4100000
          }
        ]
      },
      {
        "sharing_url": "https://ads.vk.com/segments/external/activate_key?key=fGhKlM765",
        "sources": [
          {
            "object_type": "counter",
            "object_id": 2
          },
          {
            "object_type": "pricelist",
            "object_id": 3
          },
        ],
        "price": "200",
        "sharing_key": "fGhKlM765",
        "is_marketplace": true,
        "send_email": null,
        "payment_type": "fixed_cpm",
        "owner": {
          "username": "your.user@mail.ru",
          "id": 4000000
        },
        "type": "public",
        "users": [
          {
            "username": "shared.user@mail.ru",
            "id": 4100000
          }
        ]
      },
    ]
  }
```

### POST

Create the sharing key for data sources.

In "sources" field are listed data sources which will be provided by this key.

Supported types of data sources:

- "campaign_list",
- "counter",
- "custom_audience",
- "lookalike_audience",
- "pricelist",
- "segment",
- "users_list".

Data sources can be added to the key under the following conditions:

- user is owner of data source;
- in case of segments: user is owner of all included data sources and segments;
- a data source is active;
- in case of Look-Alike: Look-Alike audience has status loaded;
The "users" field lists the VK Ads usernames that will be able to activate the key. Instead of the name, you can specify the e-mail of an unregistered user. If you leave the field empty, the key will be public, and any user can activate it.

Request example:

```http
  POST /api/v2/sharing_keys.json
  {
    "sources": [
      {
        "object_type": "segment",
        "object_id": 300
      }
    ],
    "send_email": true,
    "users": [{"username": "to.share@mail.ru"}]
  }
```

Response example:

```http
  {
    "users": [{"username": "to.share@mail.ru"}],
    "price": "0",
    "sharing_key": "aBcDe23432",
    "is_marketplace": false,
    "sources": [
      {
        "object_type": "segment",
        "object_id": 300
      }
    ],
    "payment_type": "free",
    "owner": {
      "username": "your.user@mail.ru",
      "id": 4000000
    },
    "type": "private",
    "sharing_url": "https://ads.vk.com/segments/external/activate_key?key=aBcDe23432"
  }
```

Response status codes:

200 - The key was successfully created.

400 - In the following cases:

- Validation error.

Errors exaples:

- User is not data source owner.

```http
  {"error": {
    "fields": {"sources": {"items": [
      {"code": "unallowed_value",
       "message": "Object not found",
       "arguments": {"object_id": 59070, "object_type": "segment"}}
    ]}},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```

- Data source is not active.

```http
  {"error": {
    "fields": {"sources": {"items": [
      {"code": "unallowed_value",
       "message": "Object not active",
       "arguments": {"object_id": 59070, "object_type": "segment"}}
    ]}},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```

- Data source cannot be shared.

```http
 {"error": {
    "fields": {"sources": {"items": [
      {"code": "unallowed_value",
       "message": "Object not shareable",
       "arguments": {"object_id": 59070, "object_type": "segment"}}
    ]}},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```

- User is not DMP so the key cannot be published to DMP Marketplace.

```http
  {"error": {
    "fields": {"is_marketplace":
      {"code": "unallowed_value",
       "message": "Only DMP can publish to marketplace",
    }},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```

- User didn't specify name of DMP-provider so the key cannot be published to DMP Marketplace.

```http
  {"error": {
    "fields": {"is_marketplace":
      {"code": "unallowed_value",
       "message": "DMP user name has to be set to publish to marketplace",
    }},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```

- The key is private so it cannot be published to DMP Marketplace.

```http
  {"error": {
    "fields": {"is_marketplace":
      {"code": "unallowed_value",
       "message": "Cannot be set for private keys",
    }},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```

- Attempt to share private key with a owner.

```http
  {"error": {
    "fields": {"users":
      {"code": "unallowed_value",
       "message": "Cannot assign key to owner",
    }},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```

- E-mails are invalid.

```http
  {"error": {
    "fields": {"users":
      {"code": "invalid_email",
       "message": "Enter a valid email address or username",
       "value": ["invalid_email_1", "invalid_email_2"]
    }},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```

- Price is not specified for the paid key.

```http
  {"error": {
    "fields": {"price":
      {"code": "required",
       "message": "Price is required for fixed_cpm keys",
    }},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```

- User is not DMP so creating of a paid key is prohibited.

```http
  {"error": {
    "fields": {"price":
      {"code": "invalid_type",
       "message": "Only DMP partner can create CPM keys",
    }},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```

- Price is specified for the free key.

```http
  {"error": {
    "fields": {"price":
      {"code": "unallowed_value",
       "message": "Price is only for fixed_cpm keys",
    }},
    "message": "Validation failed",
    "code": "validation_failed"
  }}
```
