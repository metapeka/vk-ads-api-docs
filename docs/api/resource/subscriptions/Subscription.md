Information

Resources

Audiences and data sources

Users

Dictionaries

Ads

Finance

Lead forms

Subscriptions

[Subscriptions](https://ads.vk.com/en/doc/api/resource/Subscriptions) [Subscription](https://ads.vk.com/en/doc/api/resource/Subscription)

Surveys

Objects

# Subscription

## /api/v3/subscription/<subscription\\_id>.json

A resource that allows you to delete subscriptions to notifications about changes to a resource. It supports only subscriptions created via this method; subscriptions from `v2/subscriptions.json` are not supported.

### DELETE

Deletes a user's subscription.

Request example:

```http
DELETE /api/v3/subscription/123.json
```

Returned status codes:

- **204** — subscription successfully deleted.
- **404** — subscription not found.
