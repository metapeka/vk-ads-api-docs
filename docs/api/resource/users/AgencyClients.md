# AgencyClients

## /api/v2/agency/clients.json

The resource enables user to get data on existing agency clients and create new ones.

Available only to the users with agency accounts.

Used object: [AgencyClient](https://ads.vk.com/en/doc/api/object/AgencyClient)

### GET

The request returns a list of all agency clients.

Request example:

```http

   GET /api/v2/agency/clients.json
```

Additional GET parameters:

The following GET parameters enable you to filter data:

- limit - The number of the returned clients. Default value is 20. Maximum value is 50.
- offset - The offset starting point in the list. Default value is 0.
- \_user\_\_id - Client user id.
- \_user\_\_id\_\_in - Comma-separated list of client user id.
- \_user\_\_username - Client name.
- \_user\_\_username\_\_in - Comma-separated list of client names in the following format: "username1,username2,...,usernameN".
- \_user\_\_status, \_user\_\_status\_\_ne - Client status.
- \_user\_\_status\_\_in - Comma-separated list of statuses.
- \_status, \_status\_\_ne - Relationship status between client and agency.
- \_status\_\_in - Comma-separated list of statuses.
- \_q - Full text search by user.username, user.additional\_info.client\_name, user.additional\_info.client\_info

Example of a request with additional parameters:

```http

   GET /api/v2/agency/clients.json?limit=50&offset=100&_user__username=Vasily Ivanov
```

Response example:

```http

    {
        "count": 1,
        "items": [\
            {\
                "access_type": "full_access",\
                "status": "active",\
                "user": {\
                   "account": {\
                      "id": 17668,\
                      "balance": 3000,\
                      "a_balance": 0,\
                      "type": "physical",\
                      "currency_balance_hold": 300,\
                   },\
                   "additional_emails": ["test@mail.ru"],\
                   "additional_info": {\
                      "name": "Vasily Ivanov",\
                      "email": "test@example.com",\
                      "phone": "89153724330",\
                      "address": "",\
                      "client_info": "Note",\
                      "client_name": "Vasily Ivanov",\
                   },\
                   "id": 17668,\
                   "status": "active",\
                   "username": "Vasily Ivanov",\
                },\
            },\
            ...\
       ],
       "limit": 20,
       "offset": 0
   }
```

### POST

The request creates a new client or adds an existing one to the list of agency clients.
To add an existing client, their account must meet the following requirements:

- The account has the "active" status
- The owner is a direct advertiser
- The account is not assigned to an agency or agency branch
- The account uses the same currency as the agency ( [User](https://ads.vk.com/en/doc/api/object/User).currency).

Example of a request for creating a new client:

```http

  POST /api/v2/agency/clients.json
  {
    "access_type":"full_access",
    "user": {
      "additional_emails": ["test@mail.ru"],
      "additional_info": {
        "client_info": "Note",
        "client_name": "Vasily Ivanov",
      }
    }
  }
```

Example of a request for adding an existing client to a client list:

```http

  POST /api/v2/agency/clients.json
  {
    "access_type":"full_access",
    "user": {
      "id":17668,
      "additional_emails": ["test@mail.ru"],
      "additional_info": {
        "client_info": "Note",
        "client_name": "Vasily Ivanov",
      }
    }
  }
```

```http

  POST /api/v2/agency/clients.json
  {
    "access_type":"full_access",
    "user": {
      "username":"client_username",
      "additional_emails": ["test@mail.ru"],
      "additional_info": {
        "client_info": "Note",
        "client_name": "Vasily Ivanov",
      }
    }
  }
```

Response example:

```http

  {
    "user": {
      "id":17668,
      "username":"client_username"
    }
  }
```

Response status codes:

200 - The client was successfully added to the client list.

400 - One of the following errors occurred:

- Validation error (the "validation\_failed" code).
- The client is inactive or assigned to an agency (the "invalid\_user" code).
- The client and the agency use different currency (the "invalid\_user" code).
- Additional emails contain the main user email (the "duplicate\_value" code)

404 - The client with the specified ID does not exist.

Error example(s):

```http

  {"error": {"code": "validation_failed", "fields": { <fields with errors> }}}
 - Data error.

  {"error": {"fields": {"user": {"code": "invalid_user", "message": "Cant join agency"}}}}
 - An attempt to add a client that is already assigned to an agency.

  {"error": {"fields": {"user": {"code": "invalid_user", "message": "Different currency for agency and client"}}}}
 - At attempt to add a client whose currency differs from the agency's.

  {"error": {"fields": {"additional_emails": {"code": "duplicate_value", "message": "Additional emails contain the main user email"}}, "message": "Validation failed", "code": "validation_failed"}}
- At attempt to add the same additional email as the main user email.
```
