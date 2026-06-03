# Goals

## /api/v2/goals.json

The resource enables user to get a list of all goals that can be used for targeting or statistics. The list contains [Top@Mail.ru](https://top.mail.ru/) counter goals, apps and social network groups events, and mobile apps installations.

Used object: [Goals](https://ads.vk.com/en/doc/api/object/Goals)

### GET

The request returns a list of all available goals.

Request example:

```http
  GET /api/v2/goals.json
```

Response example:

```http
    {
      "ok_game":[
        {
          "goal":"ok_game_join",
          "description":"Odnoklassniki app installation"
        }
      ],
      "ok_group":[
        {
          "goal":"ok_group_join",
          "description":"New membership in a VKontakte group"
        }
      ],
      "mobile_install":[
        {
          "goal":"mobile_app",
          "description":"App installtion"
        }
      ],
      "topmailru":[
        {
          "counter_name":"Top.Mail.Ru counter",
          "goal":"uss:goal_1",
          "counter_id":8,
          "description":"Goal 1"
        },
        {
          "counter_name":"Top.Mail.Ru counter",
          "goal":"uss:goal_2",
          "counter_id":8,
          "description":"Goal 2"
        }
      ]
    }
```
