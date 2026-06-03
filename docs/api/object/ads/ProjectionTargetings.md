# ProjectionTargetings

Forecasting targetings resource.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| age | list of integer | readablewritablemax\_value=79 | Age (list of ages) |
| fulltime | [FulltimeTargeting](https://ads.vk.com/en/doc/api/object/FulltimeTargeting) | readablewritable | Time (days and hours) |
| interests | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Users' interests. [List of available interests](https://ads.vk.com/en/doc/api/resource/TargetingsTree) |
| interests\_soc\_dem | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Users' socio-demographic interests. [List of available interests](https://ads.vk.com/en/doc/api/resource/TargetingsTree) |
| interests\_stable | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Users' long-term interests. [List of available interests](https://ads.vk.com/en/doc/api/resource/TargetingsTree) |
| mobile\_operation\_systems | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Mobile operating systems. [List of available OSes](https://ads.vk.com/en/doc/api/resource/MobileOperationSystem) |
| mobile\_operators | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Mobile carriers. [List of available carriers](https://ads.vk.com/en/doc/api/resource/MobileOperator) |
| mobile\_types | list of string | readablewritable | Mobile device types. [List of available device types](https://ads.vk.com/en/doc/api/resource/MobileTypes) |
| mobile\_vendors | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Mobile device manufacturers. [List of available manufacturers](https://ads.vk.com/en/doc/api/resource/MobileVendors) |
| pads | list of id | readablerequiredwritablemin\_value=1max\_value=2147483647 | Ad placements. Available placements are defined in the package. |
| regions | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Regions (list of region IDs). [List of available regions](https://ads.vk.com/en/doc/api/resource/Region) |
| sex | list of string | readablewritable | Gender (combinations of `male` and `female`) |
