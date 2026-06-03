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

# TransactionGroups

## /api/v2/billing/transaction\\_groups.json

Resource returns transaction groups info

Used object: [TransactionGroup](https://ads.vk.com/en/doc/api/object/TransactionGroup)

### GET

Resource returns user's transaction groups info

Filterable fields: id, amount, date, first\\_at, last\\_at, description, object\\_id, object\\_type.

Sortable fields: id, amount, date, first\\_at, last\\_at, object\\_id, object\\_type.

Request example:

```http

   GET /api/v2/billing/transaction_groups.json
```

Response example:

```http

    {
        "count": 2,
        "limit": 50,
        "offset": 0,
        "items": [\
            {\
                "amount": "3540.00",\
                "client_id": null,\
                "date": "2018-11-01",\
                "description": "Account top-up #3650997 for the amount of 3540 RUB (3000 RUB - 540 RUB). Transaction code: e9c66246278a4e6a85a4c9ba51d33583.",\
                "first_at": "2018-11-03 16:24:25",\
                "id": 31364364,\
                "invoices": [3650997],\
                "is_commercial": true,\
                "last_at": "2018-11-03 16:24:25",\
                "payments_total": "3540",\
                "receipt": "https://money.mail.ru/fiscal/get/9ccecf52-6da2-4893-a9d9-47b6f749adfe?format=pdf",\
                "tax_amount": "540",\
                "type": "deposit",\
                "object_id": 0,\
                "object_type": "none"\
            },\
            {\
                "amount": "10000.00",\
                "client_id": 1234567,\
                "date": "2018-11-01",\
                "description": "Transfer to the client",\
                "first_at": "2018-11-05 16:24:25",\
                "id": 31364381,\
                "invoices": [],\
                "is_commercial": false,\
                "last_at": "2018-11-21 13:12:37",\
                "payments_total": "0.00",\
                "receipt": null,\
                "tax_amount": "0.00",\
                "type": "charge",\
                "object_id": 0,\
                "object_type": "none"\
            }\
        ]
   }
```
