# SharingKey

The object describes a sharing key to data sources.

Used in resources: [SharingKey](https://ads.vk.com/en/doc/api/resource/SharingKey)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| is\_marketplace | boolean | readablewritabledefault\_field | Show data sources from the key in DMP Marketplace (is available only for DMP users). |
| owner | [NestedUser](https://ads.vk.com/en/doc/api/object/NestedUser) | readabledefault\_field | The key owner. |
| payment\_type | string | readablewritabledefault\_field<br>choices = <br>- free \- free<br>- fixed\_cpm \- fixed price | A type of payment for using the sources contained in the key. |
| price | priceperunit | readablewritabledefault\_field | The price for using the sources contained in the key (for 1000 impressions in kopecks). |
| send\_email | boolean | writable | Send the key to user by email. |
| sharing\_key | string | readable | A key. |
| sharing\_url | string | readable | An url for key activation. |
| sources | list of [SharingKeySource](https://ads.vk.com/en/doc/api/object/SharingKeySource) | readablerequiredwritabledefault\_field | A data sources contained in the key. |
| type | string | readabledefault\_field<br>choices = <br>- public \- public key.<br>- private \- private key. | A type of the key. |
| users | list of [SharingKeyUser](https://ads.vk.com/en/doc/api/object/SharingKeyUser) | readablewritabledefault\_field | A users activated the key. |
