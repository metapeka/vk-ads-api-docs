# RemarketingPricelist

## Price List Management API

The price list API is needed to upload product lists for dynamic advertising, including dynamic remarketing and attracting new users.
The product list is also called a feed.

Methods for price list manipulation:
Viewing a list of your price lists

```js
GET /api/v2/remarketing/pricelists.json
```

Uploading a new price list

```js
POST /api/v2/remarketing/pricelists.json
```

Detailed view of price list

```js
GET /v2/remarketing/pricelists/{id}.json
```

Updating existing price list

```js
POST /v2/remarketing/pricelists/{id}.json
```

Deleting a price list

```js
DELETE /v2/remarketing/pricelists/{id}.json
```

### Creating new price list

There are several types of sources from where you can download a product list.

1. url: the price list will be downloaded at the link provided. The data format must comply with the requirements
Example of a query to create such a
feed:

```js
POST /api/v2/remarketing/pricelists.json
{
  "name": "My shop",
  "status": "active",
  "export_url": "https://user@pass:example.org",
  "remove_utm_tags": true,
  "refresh_period": 720,
  "source_type": "url"
}
```

Fields value

"name": Price list name.

"status": Price list status.

"export\_url": Link to the source of the price list with the product list. May contain http authentication data.

"remove\_utm\_tags": Specifying that utm links must be removed from products during importing.

"refresh\_period": Update period in hours. 1 hour minimum.

"source\_type": "url" - source type.
In order for the feed to download successfully, you need to consider that the feed must be available for the bot to download.
The bot will make requests from IP addresses

- 92.242.35.250
- 92.242.34.58

The necessary permissions must be entered in access lists and firewalls.

The bot will make requests with the header User-Agent: Rb.Mail.Ru/2.0

The format of the content must conform to one of the specifications [https://ads.vk.com/help/articles/ecomm\_catalog](https://ads.vk.com/help/articles/ecomm_catalog)

The feed may be in an archive (zip or gzip).

If a link to VK community is specified in export\_url, the price list will be retrieved from the VK community the link points to.

```js
POST /api/v2/remarketing/pricelists.json
{
  "name": "My shop",
  "status": "active",
  "export_url": "https://vk.com/club1234567890",
  "remove_utm_tags": true,
  "refresh_period": 720,
  "source_type": "url"
}
```

2. ozon\_api, wildberries: Marketplaces: goods will be retrieved from marketplaces via API. The currently supported marketplaces are Ozon and Wildberries

Ozon example

```js
POST /api/v2/remarketing/pricelists.json
{
  "name": "My shop",
  "status": "active",
  "export_url": "https://www.ozon.ru/seller/a-b-c-123456789/products/?miniapp=seller_123456789",
  "remove_utm_tags": true,
  "refresh_period": 720,
  "source_type": "ozon_api",
  "credentials": {
    "client_id": "string",
    "api_key": "string"
  },
}
```

export\_url must point to the seller's Ozon address.

Please note that for requests to Ozon you will need to specify client\_id and api\_key - parameters of access to the Ozon seller's cabinet. You can get them in the personal account of the seller Ozon

Wildberries example

```js
POST /api/v2/remarketing/pricelists.json
{
  "name": "My shop",
  "status": "active",
  "export_url": "https://www.wildberries.ru/seller/1234567890",
  "remove_utm_tags": true,
  "refresh_period": 720,
  "source_type": "wildberries",
  "credentials": {
    "api_key": "string"
  },
}
```

export\_url must point to the seller's Wildberries address.

api\_key must contain an access key to the Wildberries merchant account

3. Manual product list management
In this case export\_url is not required, there will be no periodic updates to the product list.

```js
POST /api/v2/remarketing/pricelists.json
{
  "name": "My shop",
  "status": "active",
  "remove_utm_tags": true,
  "source_type": "api"
}
```

A price list without products is created. Products can be added using API [OfferBatchTaskDetail](https://ads.vk.com/en/doc/api/resource/OfferBatchTaskDetail)

### Price list modification

You can modify the parameters specified at creation except source\_type.

```js
POST /v2/remarketing/pricelists/{id}.json
{
  "name": "One more shop",
  "status": "active",
  "remove_utm_tags": true,
  "export_url": "https://test.ru",
}
```

### Price list archiving

status can be changed in blocked.

This will indicate that the price list is archived. All advertising campaigns to which this price list is linked will be stopped.

The price list can be further unzipped.

The price list that is not used for a long time (3 days) is archived automatically. The feed products will need to be updated again when they are removed from the archive.

### Deleting the price list

Price list deletion is available if all campaigns and segments to which the price list is linked are inactive

```js
DELETE /v2/remarketing/pricelists/{id}.json
this action is irreversible
```
