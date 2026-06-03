Information

Resources

Audiences and data sources

Users

Dictionaries

Ads

Finance

[TransactionGroups](https://ads.vk.com/en/doc/api/resource/TransactionGroups) [Transaction](https://ads.vk.com/en/doc/api/resource/Transaction)

Lead forms

Subscriptions

Surveys

Objects

# Transaction

## /api/v2/billing/transactions/<mode>/<user\\_id>.json

Resource transfers money between an agency and its client

Used object: [Transaction](https://ads.vk.com/en/doc/api/object/Transaction)

### POST

Request structure:

```http

   {"amount": "10000.00"}
```

where <amount> - money amount

<mode> - transfer direction, it can have 2 values:
to - transfer to client from agency;
from - transfer from agency to client

Request example for transfer to a client:

```http

   POST /api/v2/billing/transactions/to/1234567.json
```

Response example:

```http

   {
       "amount": "10000.00",
       "created_at": "2018-11-21 13:51:28",
       "client_balance": "23000.00",
       "agency_balance": "150000.00",
       "client_username": "name@agency_client",
   }
```

Response contains data after the transaction.

Users must have enough balances for the operation. Response codes:

200 - transaction is successfully done

400 - transfer error (code "transfer\\_error").
Check balances and retry the request later.

400 - failed result client's balance (code "failed\\_amount").
Amount exceeds the available limit, see details in "message".

400 - client user is not active (code "blocked\\_user")

404 - client user is not found (### POST

Request structure:

```http

   {"amount": "10000.00"}
```

where <amount> - money amount

<mode> - transfer direction, it can have 2 values:
to - transfer to client from agency;
from - transfer from agency to client

Request example for transfer to a client:

```http

   POST /api/v2/billing/transactions/to/1234567.json
```

Response example:

```http

   {
       "amount": "10000.00",
       "created_at": "2018-11-21 13:51:28",
       "client_balance": "23000.00",
       "agency_balance": "150000.00",
       "client_username": "name@agency_client",
   }
```

Response contains data after the transaction.

Users must have enough balances for the operation. Response codes:

200 - transaction is successfully done

400 - transfer error (code "transfer\\_error").
Check balances and retry the request later.

400 - failed result client's balance (code "failed\\_amount").
Amount exceeds the available limit, see details in "message".

400 - client user is not active (code "blocked\\_user")

404 - client user is not found (code "not\\_found")

Response example with error:

```http

   {
       "error": {
           "message": "Can't transfer amount 10000.00",
           "code": "transfer_error",
       }
   }
```

"not\\_found")

Response example with error:

```http

   {
       "error": {
           "message": "Can't transfer amount 10000.00",
           "code": "transfer_error",
       }
   }
```
