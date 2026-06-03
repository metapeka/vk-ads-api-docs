# CounterGoals

## /api/v2/remarketing/counters/<counter_id>/goals.json

The resource enables you to manage the [Top@Mail.ru](https://top.mail.ru/) counter goals.

Used object: [RemarketingCounterGoal](https://ads.vk.com/en/doc/api/object/RemarketingCounterGoal)

### GET

The request returns a list of all goals for the specified counter.

Request example:

```http
  GET /api/v2/remarketing/counters/2500000/goals.json
```

Response example:

```http
  {"items": [
    {
      "substr":"/order",
      "value":null,
      "name":"Cart",
      "condition":"uss"
    },
    {
      "substr":"order_accepted",
      "value":45,
      "name":"Purchase completed",
      "condition":"jse"
    },
  ]}
```

### POST

The request creates a goal for the specified counter.

Request example:

```http
  POST /api/v2/remarketing/counters/2500000/goals.json
  {
    "substr":"order_accepted",
    "value":45,
    "name":"Purchase completed",
    "condition":"jse"
  }
```

Response example:

```http
  {
    "substr":"order_accepted",
    "value":45,
    "name":"Purchase completed",
    "condition":"jse"
  }
```

Response status codes:

200 - The goal was successfully created.

400 - Validation error.

404 - The counter cannot be found.

Error example(s):

```http
  {"error": {"message": "Can not create goal for unconfirmed counter"}}
 - The user is not the owner of the counter and the counter denied them access.

  {"error": {"message": "Can not create goal for shared counter"}}
 - The user accesses the counter with their VK Ads access key.
```
