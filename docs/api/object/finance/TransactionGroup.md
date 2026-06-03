# TransactionGroup

Transaction group details

Used in resources: [TransactionGroups](https://ads.vk.com/en/doc/api/resource/TransactionGroups)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| amount | decimal | readabledefault\_field | Amount |
| client\_id | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Client user ID |
| date | date | readable | Month date (format YY-MM-01) |
| description | string | readabledefault\_field | Description |
| first\_at | datetime | readabledefault\_field | Date and time of the first transaction in the group |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Identifier |
| invoices | list of integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | List of invoices IDs |
| is\_commercial | boolean | readabledefault\_field | It is a commercial group |
| last\_at | datetime | readabledefault\_field | Date and time of the latest transaction in the group |
| object\_id | integer | readabledefault\_fieldmax\_value=2147483647 | Object identifier |
| object\_type | string | readabledefault\_field<br>choices = <br>- none \- none<br>- campaign \- campaign<br>- pad \- pad<br>- tps \- tps<br>- user \- user | Object type |
| payments\_total | decimal | readabledefault\_field | Payments total amount |
| receipt | url | readabledefault\_field | Receipt URL |
| tax\_amount | decimal | readabledefault\_field | Amount of tax |
| type | string | readabledefault\_field<br>choices = <br>- charge \- Outcome<br>- charge\_credit \- Credit outcome<br>- deposit \- Income<br>- deposit\_credit \- Credit income | Type |
