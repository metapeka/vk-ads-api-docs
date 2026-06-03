# GoogleApp

## /api/v2/google\_apps/<app\_name>.json

The resource enables you to collect information about a Google Play application.

### GET

The request provides information about a Google Play mobile application.

Request example:

```http

  GET /api/v2/google_apps/com.bscotch.quadropus.json
```

Response example:

```http

    {
        "id": 5,
        "name": "com.bscotch.quadropus",
        "type": "game",
        "category_id": 14605,
        "content_rating": "3+",
        "title": "Quadropus Rampage",
        "description": "Some words about app.",
        "icon_image":
            {
                "preview_url": "http://rbui.trgqa.devmail.ru/img/04/B798CD.png",
                "height": 256,
                "width": 256,
                "content_id": 2141188,
                "type": "static",
                "id": 21966769,
                "size": 117374
            }
    }
```

Response status codes:

404 - The app cannot be found.

### POST

The request updates information about a Google Play mobile application.

Request example:

```http

  POST /api/v2/google_apps/com.bscotch.quadropus.json
```

Response example:

```http

    {
        "id": 5,
        "name": "com.bscotch.quadropus",
        "type": "game",
        "category_id": 14605,
        "content_rating": "3+",
        "title": "Quadropus Rampage",
        "description": "Some words about app.",
        "icon_image":
            {
                "preview_url": "http://rbui.trgqa.devmail.ru/img/04/B798CD.png",
                "height": 256,
                "width": 256,
                "content_id": 2141188,
                "type": "static",
                "id": 21966769,
                "size": 117374
            }
    }
```

Response status codes:

404 - The app cannot be found.
