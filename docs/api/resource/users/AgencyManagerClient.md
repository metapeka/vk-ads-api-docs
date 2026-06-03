# AgencyManagerClient

## /api/v2/agency/managers/<manager\_id>/clients/<client\_id>.json

## /api/v2/agency/managers/<manager\_username>/clients/<client\_username>.json

The resource enables user to manage accounts of an agency's manager clients.

Available only to the users with agency accounts.

Used object: [AgencyManagerClient](https://ads.vk.com/en/doc/api/object/AgencyManagerClient)

### POST

The request modifies data and/or access permissions of a client from the manager's client list.

Example of the request to modify client data:

```http

  POST /api/v2/agency/managers/123/clients/17668.json
  {
    "access_type":"full_access",
  }
```

where:
123 is an agency account manager ID

17668 is the client ID

Response status codes:

204 - The client data was successfully modified.

400 - Validation error (the "validation\_failed" code).

404 - The client cannot be found.

Error example(s):

```http

  {"error": {"code": "validation_failed", "fields": { <fields with errors> }}}
 - Data error.
```

### DELETE

The request deletes a client from the list of the manager's clients. This request does not remove the client account from VK Ads or the agency's client list.

Request example:

```http

  DELETE /api/v2/agency/managers/123/clients/17668.json
```

where:
123 is an agency account manager ID

17668 is the client ID

Response status codes:

204 - The client was successfully deleted from the manager's client list.

404 - One of the following errors occurred:

- The client cannot be found on the manager's client list.
- The manager does not belong to the agency.
