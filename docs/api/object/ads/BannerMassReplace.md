# BannerMassReplace

An object that allows you to bulk update banner text and links.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| change\_from | string | readablerequiredwritable | Text that will be found and replaced. |
| change\_to | string | readablerequiredwritable | New text that will be used after replacement. |
| field | string | readablerequiredwritable<br>choices = <br>- urls \- links<br>- textblocks \- text blocks | Field in which the replacement will be performed. |
| ids | list of id | readablerequiredwritablemin\_value=1max\_value=2147483647 | Banner identifiers. |
