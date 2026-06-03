# PredictedRate

Information about the predicted CR and CTR for a package or an ad group.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| avg\_cr | float | readable | Predicted conversion rate |
| avg\_ctr | float | readable | Predicted click-through rate |
| calc\_by\_package | boolean | readable | `true` — the forecast is calculated without considering the ad group's history; `false` — the forecast is calculated with the ad group's history taken into account |
| campaign\_id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Ad group identifier. Returned only if the forecast was requested for an ad group |
| histogram\_id | string | readable | Histogram ID. This field allows linking the CR/CTR for a package/ad group with the histogram |
| package\_id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Package ID |
