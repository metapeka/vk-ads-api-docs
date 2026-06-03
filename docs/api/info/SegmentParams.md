# SegmentParams

### Parameters of data sources in segments

**[List of user IDs](https://ads.vk.com/en#userID)**

General parameters:

|     |     |     |
| --- | --- | --- |
| type | Ad impression condition | positive — for those included in the source<br>negative — for yt included in the source |

General parameters for time intervals:

|     |     |     |
| --- | --- | --- |
| right | The beginning of the time interval is indicated as the number of days before the request. | 0 <= right <= 365, left >right |
| left | The end of the time interval, indicated as the number of days before the request | 0 <= left <= 365, left >right |

## List of user IDs

Allows you to include users from the list uploaded to VK Ads in the audience segment.

**object\_type:** remarketing\_users\_list

**Source:** [RemarketingUsersList](https://ads.vk.com/en/doc/api/object/RemarketingUsersList)

**Time interval:** No

Parameters:

|     |     |
| --- | --- |
| source\_id | ID of the user list (RemarketingUsersList.id) |

Example:

```html
{
    "object_type":"remarketing_users_list",
    "params":{
        "source_id":28612,
        "type":"positive"
    }
}
```
