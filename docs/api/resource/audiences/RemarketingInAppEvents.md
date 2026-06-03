# RemarketingInAppEvents

## /api/v2/remarketing/inapp_events.json

The resource enables you to get a list of events in the mobile apps you can add to audience segments. These events can be used for targeting application users who did/did not perform specific actions in the app. You can track user actions with various mobile application trackers.

Used object: [RemarketingInAppEvent](https://ads.vk.com/en/doc/api/object/RemarketingInAppEvent)

### GET

The request returns a list of all events registered in mobile apps that you can add to audience segments.

Request example:

```http
  GET /api/v2/remarketing/inapp_events.json
```

Response example:

```http
  [
    {
      "app_name":"Android test",
      "trackers":[
        {
          "events":[
            {
              "id":1,
              "name":"purchase"
            },
            {
              "id":2,
              "name":"addToCart"
            }
          ],
          "id":133,
          "name":"myTracker"
        },
        {
          "events":[
            {
              "id":3,
              "name":"viewItem"
            }
          ],
          "id":233,
          "name":"anotherTracker"
        }
      ],
      "url":"https://play.google.com/store/apps/details?id=com.test",
      "created":"2018-04-15 22:42:25",
      "platform":"android",
      "url_object_id":"com.test",
      "rb_mobile_app_id":1,
      "status":"new"
    },
    {
      "app_name":"IOS test",
      "trackers":[
        {
          "events":[
            {
              "id":1,
              "name":"purchase"
            },
            {
              "id":2,
              "name":"addToCart"
            }
          ],
          "id":133,
          "name":"myTracker"
        },
        {
          "events":[
            {
              "id":3,
              "name":"viewItem"
            }
          ],
          "id":233,
          "name":"anotherTracker"
        }
      ],
      "url":"https://itunes.apple.com/ru/app/id12345",
      "created":"2018-04-15 22:42:25",
      "platform":"ios",
      "url_object_id":"12345",
      "rb_mobile_app_id":2,
      "status":"approved"
    }
  ]
```

Additional GET parameters:

The following GET parameters enable you to filter data:

- limit - The number of the returned clients. Default value is 20. Maximum value is 50.

```http
    GET /api/v2/remarketing/inapp_events.json?limit=10
```

- offset - The offset starting point in the list. Default value is 0.

```http
    GET /api/v2/remarketing/inapp_events.json?limit=5&offset=15
```
