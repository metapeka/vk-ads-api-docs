# ProjectionPrediction

An object containing information about the audience reach forecast depending on the event cost.

Used in methods: [ProjectionPrediction](https://ads.vk.com/en/doc/api/resource/ProjectionPrediction)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| campaign\_id | id | writabledefault\_fieldmin\_value=1max\_value=2147483647 | Ad group identifier. Request only. |
| cr\_ctr | list of [PredictedRate](https://ads.vk.com/en/doc/api/object/PredictedRate) | readable | List of CR/CTR values for the package and the histogram ID corresponding to this package. Response only. |
| histograms | list of [Histogram](https://ads.vk.com/en/doc/api/object/Histogram) | readable | List of histograms with prices/reach. Response only. The same histogram may correspond to different packages; the relevant one is determined by the histogram ID in the cr\_ctr field. Response only. |
| package\_ids | list of integer | writablemin\_value=-2147483647max\_value=2147483647 | List of package IDs. Request only. |
| targetings | [ProjectionTargetings](https://ads.vk.com/en/doc/api/object/ProjectionTargetings) | requiredwritable | Targetings for reach calculation. Request only. |
