# LeadFormImage

## /api/v1/lead\\_ads/upload\\_image/<image\\_role>

A resource that allows you to upload an image for subsequent use in a lead form. Currently, the following image roles are available:

- `logo` — logo
- `main_image` — form cover image

### POST

Request example

```http
POST /api/v1/lead_ads/upload_image/logo
{
  "name": "VK Ads. Updated lead form"
}
```

The request must be of type `multipart/form-data`.

Images must be uploaded to: `https://ads.vk.com/api/v1/lead_ads/upload_image/<image_role>`. PNG or JPEG images up to 5 MB are supported.

Request example:

```http
curl -X POST \
  -H "Authorization: Bearer LIDM…Io4Qj" \
  -H "Content-Type: multipart/form-data" \
  -F "file=@[object Object]" \
  "https://ads.vk.com/api/v1/lead_ads/upload_image/logo"
```

Response example

```http
HTTP 200
{
  "id": "2ed5b1a9-b799-e103-106a-a8fc00371fe6",
  "variants": {
    "original": "https://d.mradx.net/pictures/93/76/6AE2.jpeg",
    "56x56": "https://d.mradx.net/56x56/s3/pictures/93/76/6AE2.jpeg",
    "112x112": "https://d.mradx.net/112x112/s3/pictures/93/76/6AE2.jpeg",
    "256x256": "https://d.mradx.net/256x256/s3/pictures/93/76/6AE2.jpeg"
  }
}
```

Possible response codes

- **200** — ad saved
- **400** — validation error
