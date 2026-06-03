# AppleApp

## /api/v2/apple\_apps/<app\_name>.json

The resource enables you to collect information about an App Store application.

### GET

The request provides information about an App Store mobile application.

Request example:

```http

  GET /api/v2/apple_apps/535176909.json
```

Response example:

```http

    {
        "id": 5,
        "name": "535176909",
        "type": "game",
        "category_id": 4,
        "content_rating": "9+",
        "title": "BADLAND",
        "description": "Some words about app.",
        "icon_image":
            {
                "preview_url": "http://rbui.trgqa.devmail.ru/img/39/6AFC7B.jpg",
                "height": 256,
                "width": 256,
                "content_id": 2141189,
                "type": "static",
                "id": 21966770,
                "size": 59566
            }
    }
```

Response status codes:

404 - The app cannot be found.

### POST

The request updates information about an App Store mobile application.

Request example:

```http

  GET /api/v2/apple_apps/535176909.json
```

Response example:

```http

    {
        "id": 5,
        "name": "535176909",
        "type": "game",
        "category_id": 4,
        "content_rating": "9+",
        "title": "BADLAND",
        "description": "Some words about app.",
        "icon_image":
            {
                "preview_url": "http://rbui.trgqa.devmail.ru/img/39/6AFC7B.jpg",
                "height": 256,
                "width": 256,
                "content_id": 2141189,
                "type": "static",
                "id": 21966770,
                "size": 59566
            }
    }
```

Response status codes:

404 - The app cannot be found.
