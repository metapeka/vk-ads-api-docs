# SkAdNetworkIdentityShare

## /api/v2/apple\_apps/<app\_id>/sk\_ad\_network\_ids/share.json

This resource allows you to allocate SkAd Network campaign identifiers to another user.

You can determine how many identifiers are available and how many have already been allocated to agents using the [MobileApps](https://ads.vk.com/en/doc/api/resource/MobileApps) resource.

### POST

Request example:

```http
POST /api/v2/apple_apps/123456/sk_ad_network_ids/share.json

{
  "count": 50,
  "username": "example@mail.ru"
}
```

Returns an empty response with status code 204.
