# Overview

### Overview

The API is implemented as a set of " [resources](https://ads.vk.com/doc/api)" (domain objects) and "methods" (operations on resources), which to some extent corresponds to the REST ideology. The main difference is that many methods allow operating on resources with a complex structure that includes other resources with an arbitrary nesting level or lists of other resources. Many methods also support operations on multiple resources of the same type.

Each resource has one or more URL types. Different operations on a resource are implemented as different HTTP protocol methods. For example, retrieving a list of ad campaigns:

`GET /api/v2/ad_plans.json`

Creating a campaign:

```js
POST /api/v2/ad_plans.json
```

Retrieving parameters of a specific campaign:

```js
GET /api/v2/ad_plans/1.json
```

For the vast majority of methods, input and output data are represented in JSON format. Accordingly, HTTP requests and responses have the application/json content type. For GET or DELETE requests that do not have a body, specifying the type is optional.

To validate input and generate output data, one or more data structures are described for each resource. The description of each method specifies which structures it operates on.

## Authentication

OAuth2 is used for authentication and authorization in the API. Its implementation is described in a [separate article](https://ads.vk.com/doc/api/info/%D0%90%D0%B2%D1%82%D0%BE%D1%80%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F%20%D0%B2%20API). Client registration for working with the API via OAuth2 is currently performed manually upon request to Support (available in the service interface). How to get access to the API is described in the [instructions](https://ads.vk.com/help/articles/help_api).

## Basic data types

The API operates with the following set of basic data types:

| **Data type** | **JSON representation** |
| --- | --- |
| String (String) | "value" |
| Integer (Integer) | "123" |
| Decimal (Decimal) | "1.23" |
| Boolean (Boolean) | "true" or "false" |
| None (None) | null |
| Date (Date) | "2013-08-18", format YYYY-MM-DD unless another is explicitly specified |
| Datetime (Datetime) | "2013-08-28 16:49:34", format YYYY-MM-DD HH:MM:SS unless another is explicitly specified; time zone Europe/Moscow unless another is specified |
| List (List) | \["value1", "value2"\], list elements are homogeneous |
| Object (Object) | {"id": 1, "name": "Name"}, object properties may be heterogeneous |

Complex data types based on the basic ones are described in the [methods and resources documentation](https://ads.vk.com/doc/api/).

## Basic errors

Error responses have standard HTTP response statuses. The response body contains more detailed error information in JSON format (error response content type — application/json).

- 400 — validation error of the data structure sent in the request;
- 401 — missing signature for authentication or an invalid signature value (the Authorization header must contain a valid access\_token value);
- 403 — the operation is forbidden for the account whose secret key (access\_token) was used to sign the request;
- 404 — the requested resource was not found;
- 405 — the resource does not support this HTTP method;
- 413 — request body is too large;
- 429 — rate limit exceeded;
- 500 — unexpected error.

## Response compression

If your client supports compression, you can pass the following header in the request:

`Accept-Encoding: gzip, deflate`

## Rate limits (requests per unit time)

The service limits the number of requests per unit time. Limits apply to time intervals equal to a second, an hour, and a day. Limits are tied to calendar time periods.

User limits are calculated independently for each user. For example, if the system has a limit of 10 requests per minute for a certain method, this means that each user can make no more than 10 requests per minute.

Limits may be configured differently for different users or user groups. Therefore, you should always rely only on the data received in real time.

Current limits are returned in the HTTP response headers for any request (different methods will have different values):

`X-RateLimit-RPS-Limit: value     # number of requests per second
X-RateLimit-Hourly-Limit: value  # number of requests per hour
X-RateLimit-Daily-Limit: value   # number of requests per day`

The number of actions remaining until the threshold is reached is also returned in the HTTP response headers:

`X-RateLimit-RPS-Remaining: value    # how many requests can be made until the end of the current second
X-RateLimit-Hourly-Remaining: value # how many requests can be made until the end of the current hour
X-RateLimit-Daily-Remaining: value  # how many requests can be made until the end of the current day`

Information about limits for a specific user can also be obtained using the request

|     |
| --- |
| `GET /api/v2/throttling.json` |

The response contains the current limit values, as well as the number of remaining requests for resources for which limits are set.

|     |
| --- |
| `{`<br>`    "REMARKETINGUSERSLIST": {`<br>`        "v2": {`<br>`            "READ": {`<br>`                "remaining": {`<br>`                    "60": 1`<br>`                },`<br>`                "limits": {`<br>`                    "60": 1`<br>`                }`<br>`            },`<br>`            "CREATE": {`<br>`                "remaining": {`<br>`                    "60": 0`<br>`                },`<br>`                "limits": {`<br>`                    "60": 0`<br>`                }`<br>`            }`<br>`        },`<br>`        "v3": {`<br>`            "READ": {`<br>`                "remaining": {`<br>`                    "3600": 200`<br>`                },`<br>`                "limits": {`<br>`                    "3600": 200`<br>`                }`<br>`            },`<br>`            "CREATE": {`<br>`                "remaining": {`<br>`                    "3600": 10`<br>`                },`<br>`                "limits": {`<br>`                    "3600": 10`<br>`                }`<br>`            }`<br>`        },`<br>`        "all": {`<br>`            "READ": {`<br>`                "remaining": {`<br>`                    "3600": 200`<br>`                },`<br>`                "limits": {`<br>`                    "3600": 200`<br>`                }`<br>`            },`<br>`            "CREATE": {`<br>`                "remaining": {`<br>`                    "60": 1`<br>`                },`<br>`                "limits": {`<br>`                    "60": 1`<br>`                }`<br>`            }`<br>`        }`<br>`    }` |

For a resource, both global limits and limits for using a method of a specific version may be set. The version corresponds to the namespace. Thus, in the example above, using the method /api/v2/remarketing/users\_lists/<id>.json you can make no more than one GET request per minute, and you cannot create a new list; using /api/v2/remarketing/users\_lists/<id>.json you can read information for 200 lists per hour and create 10 lists per hour. At the same time, using requests of any versions in total, you cannot read information for more than 200 lists per hour, and you can create no more than 1 list per hour.

After a new version of a method is released, we will gradually reduce the usage limits for previous versions of the same resource.

# API Standards

The following rules apply to all methods.

## Request parameters

| Name | Format | Default | Description | Example |
| --- | --- | --- | --- | --- |
| fields | <field\_name>\[,<field\_name>\]\* | Depends on the resource | List of fields for the top-level object | fields=id,name |
| limit | integer | 20 | Number of objects in the response. Maximum 50 | limit=10 |
| offset | integer | 0 | Offset within the result set | offset=500 |
| sorting | \[-\]?<field\_name>\[,\[-\]?<field\_name>\]\* | - | Sorting by object fields. The list of sortable fields is unique for each resource. <field\_name> - ASC, -<field\_name> - DESC | sorting=id,-created |
| \_<field\_name>\_\_<field\_lookup> | <value>\[,<value>\]\* | - | Filters by object fields. The list of filterable fields is unique for each resource. You cannot filter by fields of nested objects. | \_id\_\_in=1,2,3 \_status\_\_ne=active \_updated\_\_gt=2018-01-01 00:00:00 |
| \_<field\_name> | <value> | - | Equality filter by an object field. Rules are the same as in \_<field\_name>\_\_<field\_lookup> | \_id=1 |

## Field lookups (standard names)

ne - not equal

lt - less than

lte - less than or equal

gt - greater than

gte - greater than or equal

## Response

Collection:

```bash
{ "count": int, // total number of objects after applying all other parameters "offset": int, // current offset "limit": int, // number of objects in the response "items": [{ "": field_value, ... }, ...] }
```

Object:

```bash
{ "": field_value, ... }
```
