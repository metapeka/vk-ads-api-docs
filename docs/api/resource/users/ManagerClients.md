# ManagerClients

## /api/v3/manager/clients.json

The resource enables you to collect data about a manager clients.

The resource is available only for users with type manager.

### GET

Return a list of all manager clients.

Request example:

```http

   GET /api/v3/manager/clients.json
```

Response example:

```http

    {
        "count": 1,
        "items": [\
            {\
                "access_type": "full_access",\
                "status": "active",\
                "agency": {\
                   "id": 1007892,\
                   "username": 'test-target-6@mail.ru',\
                },\
                "user": {\
                   "account": {\
                      "id": 17668,\
                      "balance": 3000,\
                      "a_balance": 0,\
                      "type": "physical",\
                      "currency_balance_hold": 300,\
                   },\
                   "additional_emails": ['test@mail.ru'],\
                   "additional_info": {\
                      "name": "Kurt Cobain",\
                      "email": "test@example.com",\
                      "phone": "89153724330",\
                      "address": "",\
                      "client_info": "Note",\
                      "client_name": "Kurt Cobain",\
                   },\
                   "id": 17668,\
                   "status": "active",\
                   "username": "Ivan Smit",\
                },\
            },\
            ...\
       ],
       "limit": 20,
       "offset": 0
   }
```

Additional GET parameters:

- limit - The number of the returned leads. Default value is 20. Maximum value is 50.
- offset - The offset starting point in the list. Default value is 0.

The following GET parameters enable you to filter data:

- \_user\_\_id - Client user id.
- \_user\_\_id\_\_in - Comma-separated list of client user id.
- \_user\_\_username - Username.
- \_user\_\_username\_\_in - Comma separated list of usernames.
- \_user\_\_status, \_user\_\_status\_\_ne - Client status.
- \_user\_\_status\_\_in - Comma-separated list of statuses.
- \_status, \_status\_\_ne - Relationship status between client and manager.
- \_status\_\_in - Comma-separated list of statuses.

Request example:

```http

   GET /api/v3/manager/clients.json?limit=50&offset=100&_user__username__in=Kurt Cobain,Ivan Smit
```
