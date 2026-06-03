# FulltimeTargeting

Campaign display schedule.

Used in objects: [Targetings](https://ads.vk.com/en/doc/api/object/Targetings)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| flags | list of string | readablewritable | use\_holidays\_moving — Take into account moved public holidays; cross\_timezone — Take time zones into account |
| fri | list of integer | readablewritablemax\_value=23 | Hours on Friday |
| mon | list of integer | readablewritablemax\_value=23 | Hours on Monday |
| sat | list of integer | readablewritablemax\_value=23 | Hours on Saturday |
| sun | list of integer | readablewritablemax\_value=23 | Hours on Sunday |
| thu | list of integer | readablewritablemax\_value=23 | Hours on Thursday |
| tue | list of integer | readablewritablemax\_value=23 | Hours on Tuesday |
| wed | list of integer | readablewritablemax\_value=23 | Hours on Wednesday |
