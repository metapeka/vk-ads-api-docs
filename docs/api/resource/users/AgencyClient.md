# AgencyClient

## /api/v2/agency/clients/<id>.json

The resource enables user to manage agency client accounts.

Available only to the users with agency accounts.

Used object: [AgencyClient](https://ads.vk.com/en/doc/api/object/AgencyClient)

### POST

The request modifies client data and/or access permissions.

Example of the request to modify client data:

```http

  POST /api/v2/agency/clients/17668.json
  {
    "access_type":"full_access",
    "user": {
      "additional_emails": ['test@mail.ru'],
      "additional_info": {
        "client_info": "Note",
        "client_name": "Vasily Ivanov",
      }
    }
  }
```

where 17668 is the client ID.

Response status codes:

204 - The client data was successfully modified.

400 - Validation error.

404 - The client cannot be found.

Error example(s):

```http

  {"error": {"code": "validation_failed", "fields": { <fields with errors> }}}
 - Data error.
```

### DELETE

The request deletes a client from the list of the agency clients. Only the clients whose account balance is zero or negative and uses the same currency as the agency can be deleted ( [User](https://ads.vk.com/en/doc/api/object/User).currency). This request does not remove the client account from VK Ads.

Request example:

```http

  DELETE /api/v2/agency/clients/17668.json
```

where 17668 is the client ID.

Response status codes:

204 - The client was deleted successfully.

400 - One of the following errors occurred:

- The client account balance is positive (the "invalid\_user" code);
- The client currency differs from the agency currency (the "invalid\_user" code).

404 - The client cannot be found.

Error example(s):

```http

  {"error": {"fields": {"user": {"code": "invalid_user", "message": "Can't delete client with amount on hold"}}}}
 - At attempt to delete a client with a positive account balance.

  {"error": {"fields": {"user": {"code": "invalid_user", "message": "Can't delete client, money transfer error"}}}}
 - At attempt to delete a client whose currency differs from the agency's.
```
