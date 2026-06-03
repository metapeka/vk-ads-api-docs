# SkAdNetworkIdentityShare

This object is used to allocate available SkAd Network campaign identifiers to an agent or to withdraw them from the agent.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| count | integer | readablerequiredwritablemin\_value=1max\_value=100 | Number of SkAd Network campaign identifiers to allocate/withdraw |
| username | string | readablerequiredwritable | Username of the user to whom identifiers are transferred, or from whom they are withdrawn |
