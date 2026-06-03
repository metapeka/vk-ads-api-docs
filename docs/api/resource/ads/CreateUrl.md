# CreateUrl

## /api/v2/urls.json

The resource enables you to test the advertised URLs before sending the ad to moderation.

All URLs used in ads must pass VK Ads autotests. This resource allows you to test your URL beforehand and speed up the moderation process.

Used object: [URL](https://ads.vk.com/en/doc/api/object/URL)

### POST

The request creates a new [URL object](https://ads.vk.com/en/doc/api/object/URL) in the system and verifies it. The test is considered passed when the "url\_types" field in the object is filled-in.

Request example:

```http

  POST /api/v2/urls.json
  {
    "url":"http://example.com/123456789?1=1"
  }
```

Response example:

```http

  {
    "id": 13123171
  }
```

Response status codes:

201 - The URL was queued for testing.
400 - Validation error.

Possible errors:

- unknown\_scheme - The system does not support the schema used in the URL. Supported schemas are: http, https, market, itms, itms-apps.
- invalid\_url - Error in the URL body.
