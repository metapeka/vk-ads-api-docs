# RemarketingUsersLists

## /api/v3/remarketing/users_lists.json

The resource enables you to manage a users lists. Such lists are used for targeting external audiences.

Used object: [RemarketingUsersList](https://ads.vk.com/en/doc/api/object/RemarketingUsersList)

### GET

The request returns all users lists uploaded by the user.

Request example:

```http
  GET /api/v3/remarketing/users_lists.json?_q=comments
```

Response example:

```http
  {
    "items":[
      {
        "status":"ready",
        "name":"Likes and comments in VK",
        "created":"2017-05-29 18:01:05",
        "base":0,
        "entries_count":5001,
        "ids_count":5001,
        "type":"vk",
        "id":2500000,
        "has_history": false,
        "matched_ids_count": 5001
      },
      {
        "status":"ready",
        "name":"Classes and comments in Odnoklassniki",
        "created":"2017-06-16 16:40:54",
        "base":0,
        "entries_count":5001,
        "ids_count":5001,
        "type":"ok",
        "id":2500001,
        "has_history": false,
        "matched_ids_count": 5001
      }
    ]
  }
```

Filters

- _q - Full text search parameter by name. It is optional and cannot be longer than 255 characters.

### POST

The request uploads the users list as a data source. A successful request returns an object of the RemarketingUsersList type.

```note
    The list must contain no less than 2000 and no more than 5000000 lines. Maximum file size: 128 MB.
```

Format of the file with the type='ok':
ID of the users uploaded from the app; one record per line.

Format of the file with the type='dmp_id':
First line contains partner code. The remaining lines contain user IDs.

Format of the file of other types:
Plain-text list with one record per line.

CSV format:
Comma separated list. For lists with type='dmp_id', the first line is the partnet code. Then the csv header with the column names: id - user ID (required field), client_user_id - a string without commas.

```important
   Request type: multipart/form-data. The file that must be uploaded is passed as part of a multipart request with the name "file".
```

Request example:

```http
  POST /api/v3/remarketing/users_lists.json
  Content-Type: multipart/form-data
  file=File
  name=Likes+and+comments+in+VK
  type=vk
```

Response example:

```http
{
    "status":"receiving",
    "name":"Likes and comments in VK",
    "created":"2017-05-29 18:01:05",
    "base":0,
    "entries_count":5001,
    "ids_count":5001,
    "type":"vk",
    "id":2500000,
    "has_history": false,
    "matched_ids_count": 5001,
    "error": null
}
```

You can add/remove users to/from a list that have already been uploaded. To do this, upload a new list with one the following values of the "base" parameter:

- "<previous_list_ID>" to add users that are missing in the previous file version
- "-<previous_list_ID>" to remove users from the previous file version

A differential list must contain no less than 25 and more than 5000000 lines.

Example of a request for uploading a differential list:

```http
  POST /api/v3/remarketing/users_lists.json
  Content-Type: multipart/form-data
  file=File
  name=Likes+and+comments+in+VK
  type=vk
  base=10000
```

Response example:

```http
{
    "status":"receiving",
    "name":"Likes and comments in VK",
    "created":"2017-05-29 18:01:05",
    "base":10000,
    "entries_count":30,
    "ids_count":30
    "type":"vk",
    "id":2500000,
    "has_history": true,
    "matched_ids_count": 5001,
    "error": null
}
```

Response status codes:

200 - The list was successfully uploaded.

400 - Validation error.

403 - An attempt to upload a differential list by a user other than the owner of the source list.

Error examples:

```http
{"error": {"fields": {"file": [{"line_number": 10, "line": "example", "code": "invalid_email"}]}}}
- Incorrect email

{"error": {"fields": {"file": [{"code": "too_many_ids"}]}}}
- Too many IDs in the list

{"error": {"fields": {"base": [{"code": "not_found", "message": "Unknown base list"}]}}}
- The base list with the given ID doesn't exist

{
    "id": 2500000,
    "error": [
        {
            "line_number": 1,
            "line": "qwerty",
            "error_code": "invalid_uint"
        }
    ]
}
- Invalid format of one or more list items. The rest of the list items have been uploaded
```

Error codes:

- unallowed_value - Differential list cannot be based on another differential list.
- not_found - The base list with the given ID doesn't exist.
- access_denied - No permission to change base list.
- type_mismatch - Differential list must have same type as base.
- csv_line_column_index_error - The line content of the CSV file does not match the header.
- invalid_csv_header - The CSV file header doesn't contain an ID column.
- empty_user_id_with_non_empty_client_user_id - The CSV file line contains an empty user_id column, but the client_user_id column is filled.
- empty_user_id_with_non_empty_date_time - The CSV file line contains an empty user_id column, but the date_time column is filled.
- invalid_date_time - The string couldn't be converted to date and time.
- invalid_uint - The string couldn't be converted to an unsigned integer.
- invalid_email - The string couldn't be converted to email.
- invalid_phone - The string couldn't be converted to a phone number.
- invalid_mac - The string couldn't be converted to a MAC address.
- invalid_md5 - The string couldn't be converted to MD5.
- too_many_ids - Too many IDs in the list.
- not_enough_ids - Too few IDs in the list.
- invalid_file_header - Invalid file header (for dmp_id and dmp_type lists).
- status_not_receiving - The status of the user list is not equal to "receiving".
- file_reading_error - Error reading file.
- duplicated_user_id - The line with this user id is already in the file.
