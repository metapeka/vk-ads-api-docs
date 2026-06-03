# CounterGoal

## /api/v2/remarketing/counters/<counter_id>/goals/<goal_id>.json

The resource enables you to edit the [Top@Mail.ru](https://top.mail.ru/) counter goals.

Used object: [RemarketingCounterGoal](https://ads.vk.com/en/doc/api/object/RemarketingCounterGoal)

### POST

The request edits specified counter goal. Available fields for editing: value, name, goal_type.

Request example:

```http
  POST /api/v2/remarketing/counters/2500000/goals/42.json
  {
    "value":45,
    "name":"Added to basket",
    "goal_type":"basket"
  }
```

Response example:

```http
  {
    "value":45,
    "name":"Added to basket",
    "goal_type":"basket"
  }
```

Response status codes:

200 - The goal was successfully edited.

400 - Validation error.

404 - The counter cannot be found.

Error example(s):

```http
  {"error": {"message": "Can not edit goal for unconfirmed counter"}}
 - The user is not the owner of the counter and the counter denied them access.

  {"error": {"message": "Can not edit goal for shared counter"}}
 - The user accesses the counter with their VK Ads access key.
```
