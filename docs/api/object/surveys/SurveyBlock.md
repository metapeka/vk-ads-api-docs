# SurveyBlock

An object describing a survey block.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | string | readablewritabledefault\_field | Survey block identifier. When creating a survey and using conditions, you must pass a temporary id for each block (must have the `new_` prefix). This is required because in [SurveyConditionAnswerExists](https://ads.vk.com/en/doc/api/object/SurveyConditionAnswerExists) conditions are defined based on the block id. After the survey is created, the temporary id will be replaced with the real one. When updating a survey, the `new_` prefix is required only for new blocks that are used in conditions. |
| block\_data | [BlockData](https://ads.vk.com/en/doc/api/object/SurveyBlockData) | readablewriteablerequired | Survey block data |
