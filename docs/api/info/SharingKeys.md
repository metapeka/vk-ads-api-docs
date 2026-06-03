# SharingKeys

### Sharing segments

In VK Ads [there is an option](https://target.my.com/help/advertisers/sharesegment/ru) share your own data lists and counters [Top@Mail.ru](https://top.mail.ru/) with other users.

The procedure itself is as follows: the owner of the source generates a special key, provides it to the client, and the client activates the key, which gives him access to use this source.

### Methods of the list owner

Request for key generation:

```html
POST /api/v2/sharing_keys.json
```

```html
{
"sources": [\
     {\
       "object_type": "users_list",\
       "object_id": 123456,\
     },\
     ....]
  "users": [ {"username": "lamoda@mail.ru"}, ...],
  "send_email": true/false,
  "price": float,
  "payment_type": "free"|"fixed_cpm",
  "is_marketplace": true/false
}
```

- Object\_type:
  - users\_list – for lists of users;
  - counter – for counters.
- Object\_id – ID of the source to share
- Users – list of VK Ads user accounts that will be able to activate the key. If the list of users is empty (\[\]), the key will be considered public, i.e. every user who received the key will be able to activate it. The list may include any email addresses. If a user with the specified address is not registered in VK Ads, then they will have access to the list during registration.
- Send\_email – a flag indicating if users should be notified that this source has been shared with them. Only private keys can be sent (when the list of users/addresses is known).
- price - price in rubles per 1000 impressions for a paid model (available only for DMP)
- payment\_type - key type by business model, paid or not (available only for DMP)
- is\_marketplace - flag that determines if segments are included in the marketplace (only available for DMP). To publish in the marketplace the users array must be empty (\[\])

Response:

```html
{
  "sharing_key": "absgd124ldsg0900",
  "sharing_url": "https://ads.vk.com/activate_sharing_key?key=absgd124ldsg0900"
}
```

Important! Generating a key does not automatically grant the client the right to use the list. The user must activate the key to get access to using the list.

View shared sources:

```html
GET /api/v2/sharing_keys.json
```

Response:

```html
{
  "items": [\
    {\
      "sources": [ {"object_type": "users_list", "object_id": 123456}, ...],\
      "owner": {"id": 431, "username": "user_list_owner_name"},\
      "users": [ {"id": 432, "username": "user_list_client_name"}, ... ],\
    }\
  ]
}
```

The response contains all users, regardless of whether they have activated the key or not yet.

You can revoke access by using a request:

```html
DELETE /api/v2/sharing_keys/<key>.json
```

### Client methods

Key activation:

```html
POST /api/v2/sharing_keys/<key>.json
```

```html
{"status": "active"}
```

The client can delete the source they activated just as well as their own. For user lists:

```html
DELETE /api/v1/remarketing_users_list/{users_list_id}.json
```

For counters [Top@Mail.ru](https://top.mail.ru/):

```html
DELETE /api/v1/remarketing_counters/<counter_id>.json
```
