# SkAdNetworkIdentityWithdraw

## /api/v2/apple\_apps/<app\_id>/sk\_ad\_network\_ids/withdraw.json

This resource allows you to withdraw previously allocated SkAd Network campaign identifiers from an agent. Free identifiers are withdrawn first. If there are not enough, identifiers that are used in ad campaigns will be withdrawn. In this case, the campaigns will be stopped.

You can determine how many identifiers are available and how many have been allocated to agents using the [MobileApps](https://ads.vk.com/en/doc/api/resource/MobileApps) resource.

### POST

Request example:

```http
POST /api/v2/apple_apps/123456/sk_ad_network_ids/withdraw.json

{
  "count": 50,
  "username": "example@mail.ru"
}
```

Returns an empty response with status code 204.
