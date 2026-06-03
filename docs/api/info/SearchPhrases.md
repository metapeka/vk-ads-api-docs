# SearchPhrases

### Contextual targeting

| **action** | **method** | **request** | **parameters** |
| --- | --- | --- | --- |
| Create search phrases | POST | /api/v3/search\_phrases.json?name=<name> | `name` \- name of the new list, |
| View search phrases | GET | /api/v3/search\_phrases/<id>.json | `id` \- list ID |
| View errors | GET | /api/v3/search\_phrases/<id>.json?errors=1 | `id` \- list ID |
| View all/selected lists of search phrases | GET | /api/v3/search\_phrases.json<br>/api/v3/search\_phrases.json?ids=<id1>,...,<idN> | `ids` \- the IDs of the selected lists are separated by commas |
| Rename search phrases | POST | /api/v3/search\_phrases/<id>/rename.json?name=<name> | `id` \- list ID `name` \- new list name |
| Change search phrases | PUT | /api/v3/search\_phrases/<id>.json? | `id` \- list ID, |
| Delete search phrases | DELETE | /api/v3/search\_phrases/<id>.json | `id` \- list ID |
| Download the original csv file | GET | /api/v3/search\_phrases/<id>.csv | `id` \- list ID |

### **Creating a list of contextual phrases**

POST request

/api/v3/search\_phrases.json?name=<name>

Parameters:

name - name of the new list

**Request example:**

Request URL: https://ads.vk.com/api/v3/search\_phrases.json?name=my\_test\_list

Request Method: POST

Request Heders:

Content-Type: text/csv; charset=UTF-8;

X-Trg-User-Id: <here is the user's ID>

**Request Body:**

phrase,expires

one,12d

two,12d

three,12d

**Request example json:**

Request URL: https://ads.vk.com/api/v3/search\_phrases.json?name=my\_test\_list

Request Method: POST

Request Heders:

Content-Type: Content-Type: application/json;

X-Trg-User-Id: <here is the user's ID>

**Request Body:**

`{`

```"phrases"``:["one,two,three"],`

```"stop_phrases"``:``:[sheep]``,`

```"expires"``:``:"12d"``,`

```"category"``: "test"`

`}`

**Example of a successful response**

`{`

```"id"``: 1,``// id of the created list`

```"name"``:``"test"``,`

```"status"``:``"ready"``,`

```"phrases_cnt"``: 4,`

```"stop_phrases_cnt"``: 6,`

```"errors_cnt"``: 3,``// number of errors (non-parsed lines)`

```"created"``:``"2018-01-24T11:17:59+03:00"``,`

```"updated"``:``"2018-01-24T14:35:50+03:00"`

```"category"``:``"test"``"

`}`

You can only set and receive the "category" field in the response if you have additional rights.

Example of a response exceeding the phrase limit

`{`

```"error"``: {`

```"message"``:``"limit 1 exceeded"``,`

```"code"``: 1008,`

```"details"``: {`

```"limit"``: 1`

```}`

```}`

`}`

### View a list of contextual phrases

GET Request

/api/v3/search\_phrases/<id>.json

Parameters:

`id` \- list ID

Response example

`{`

```"errors_cnt"``: 3,`

```"items"``: [`\
\
```{`\
\
```"phrase"``:``"Buy plastic windows"``,`\
\
```"stop_phrases"``: [``"interior doors"``,``"to Europe"``,``"now or never"``],`\
\
```"price_coeff"``: 1,`\
\
```"expires"``: 7200,`\
\
```"fading"``:``"inverse"``,`\
\
```"sub"``:``"Buy plastic windows"`\
\
```},`\
\
```{`\
\
```"phrase"``:``"Sell the garage urgently"``,`\
\
```"stop_phrases"``: [``"house"``,``"remove the block"``],`\
\
```"price_coeff"``: 0.8,`\
\
```"expires"``: 86520,`\
\
```"fading"``:``"linear"``,`\
\
```"sub"``:``"garage"`\
\
```},`\
\
```{`\
\
```"phrase"``:``"gifts"``,`\
\
```"stop_phrases"``: [ ],`\
\
```"price_coeff"``: 1,`\
\
```"expires"``: 864000,`\
\
```"fading"``:``"const"``,`\
\
```"sub"``:``"gifts"`\
\
```},`\
\
```]`

`}`

### View errors

GET Request

/api/v3/search\_phrases/<id>.json?errors=1

Response example

`{`

```"items"``: [`\
\
```{`\
\
```"line_number"``: 5,`\
\
```"source_line"``:``","``,`\
\
```"message"``:``"'phrase' is empty"``,`\
\
```"code"``: 1002`\
\
```},`\
\
```{`\
\
```"line_number"``: 6,`\
\
```"source_line"``:``"$OS, 1d"``,`\
\
```"message"``:``"'phrase' bad format"``,`\
\
```"code"``: 1003`\
\
```},`\
\
```{`\
\
```"line_number"``: 8,`\
\
```"source_line"``:``"tickets, 1d2h3"``,`\
\
```"message"``:``"'expires' bad format"``,`\
\
```"code"``: 1006`\
\
```}`\
\
```]`

`}`

### View all/selected lists of search phrases

GET Request

/api/v3/search\_phrases.json

/api/v3/search\_phrases.json?ids=<id1>,...,<idN>

Parameters:

`ids` \- the IDs of the selected lists are separated by commas

Response example

`{`

```"items"``: [`\
\
```{`\
\
```"id"``: 1,`\
\
```"name"``:``"sale"``,`\
\
```"status"``:``"ready"``,`\
\
```"phrases_cnt"``: 42,`\
\
```"stop_phrases_cnt"``: 5,`\
\
```"errors_cnt"``: 4,`\
\
```"created"``:``"2017-12-22T11:02:27+03:00"``,`\
\
```"updated"``:``"2017-12-22T14:02:27+03:00"``,`\
\
```"category"``: "test"`\
\
```},`\
\
```{`\
\
```"id"``: 2,`\
\
```"name"``:``"purchase"``,`\
\
```"status"``:``"ready"``,`\
\
```"phrases_cnt"``: 9,`\
\
```"stop_phrases_cnt"``: 0,`\
\
```"errors_cnt"``: 0,`\
\
```"created"``:``"2017-12-23T10:03:45+03:00"``,`\
\
```"updated"``:``"2017-12-23T10:03:45+03:00"``,`\
\
```"category"``: "test"`\
\
```},`\
\
```]`

`}`

### Rename search phrases

POST request

/api/v3/search\_phrases/<id>/rename.json?name=<name>

Parameters:

`id` \- list ID

`name` \- new list name

### Change search phrases

PUT request:

/api/v3/search\_phrases/<id>.json

Parameters:

`id` \- list ID

You can also change it using json.

Request Body:

`{`

```"phrases"``:["one,two,three"],`

```"stop_phrases"``:``:[sheep]``,`

```"expires"``:``:"12d"``,`

```"category"``: "test"`

`}`

Response example

`{`

```"id"``: 1,`

```"name"``:``"sale"``,`

```"status"``:``"ready"``,`

```"phrases_cnt"``: 42,`

```"stop_phrases_cnt"``: 5,`

```"errors_cnt"``: 0,`

```"created"``:``"2017-12-22T11:02:27+03:00"``,`

```"updated"``:``"2017-12-26T19:03:22+03:00",`

`}`

**Delete search phrases**

DELETE request:

/api/v3/search\_phrases/<id>.json

Parameters:

`id` \- list ID

**Download the original CSV file**

GET Request

/api/v3/search\_phrases/<id>.csv

Parameters:

`id` \- list ID

**Errors returned**

All erroneous answers are returned like this:

`{`

```"error"``: {`

```"code"``:``"ERROR_CODE"``,`

```"message"``:``"message text"`

```}`

`}`

| **http status** | **code** | **message** |
| --- | --- | --- |
| 400 Bad Request | ERROR | can't read request body |
| 400 Bad Request | BAD\_DATA | bad csv header <br>column 'phrase' is mandatory <br>bad csv file |
| 404 Not Found | NOT\_FOUND | search phrases not found |
| 409 Conflict | WAIT\_TIMEOUT | search phrases locked |
| 410 Gone | DELETED | search phrases not found |
| 410 Gone | NOT\_READY | search phrases not ready |
| 413 Request Entity Too Large | ERROR | too many phrases in the list |
| 500 Internal Server Error | ERROR |  |
