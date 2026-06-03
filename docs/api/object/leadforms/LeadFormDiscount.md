# LeadFormDiscount

An object describing the "discount" reward type. When a lead goes through the form, this information will be displayed on every page.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| type | string | readablewritablerequired<br>choices = <br>- money \- a fixed amount in rubles<br>- percent \- a percentage of the price | Discount type |
| value | integer | readablewritablerequired | Discount value. For type=money, the expected amount is from 1 to 10 million rubles. For type=percent, the expected value is an integer percentage from 1 to 100. |
