# SharingKeyUser

## /api/v2/sharing_keys/<key>.json

The resource enable you to activate and delete the keys that grant access to external data sources (users lists, counters, etc.). When the key is activated, the segments that can be accessed with it are added to the data sources pool of the current user. Only the key owner can delete the key.

Used object: [SharingKeyUser](https://ads.vk.com/en/doc/api/object/SharingKeyUser)

### POST

The request activates access key and adds some or all of its data sources to user data sources.

Request example:

```http
  POST /api/v2/sharing_keys/abcdefg.json
```

Response example:

```http
	{
	  "id": 200000,
	  "sources": [
	    {
	      "object_id": 2500000,
	      "object_type": "users_list",
	      "params": {
	        "entries_count": 18350,
	        "id": 2500000,
	        "name": "Interests 1",
	        "type": "vk"
	      }
	    },
	    {
	      "object_id": 1000500,
	      "object_type": "counter",
	      "params": {
	        "id": 1000500,
	        "name": "My counter"
	      }
	    }
	  ],
	  "username": "user@na.me"
	}
```

You can use the "sources" parameters to activate some data sources from the pool available for a key.

Example of a request with partial activation:

```http
  POST /api/v2/sharing_keys/abcdefg.json
  {
  	"sources": {
	      "object_id": 2500000,
	      "object_type": "users_list"
  	}
  }
```

Response example:

```http
	{
	  "id": 200000,
	  "sources": [
	    {
	      "object_id": 2500000,
	      "object_type": "users_list",
	      "params": {
	        "entries_count": 18350,
	        "id": 2500000,
	        "name": "Interests 1",
	        "type": "vk"
	      }
	    }
	  ],
	  "username": "user@na.me"
	}
```

Response status codes:

200 - The key was successfully activated.

403 - The user does not have access to the private key.

404 - The "sources" parameter contains a non-existent data source.

400 - Other errors.

Error example(s):

```http
	400 Bad Request
	{"error": {"code": "validation_failed", "fields": { <fields with errors> }}}
	- Data error.

	{"error": {"code": "is_owner", "message": "Cannot activate key for owner"}}
	- An attempt to activate a personal key.

	{"error": {"code": "cannot_add_source", "message": "Counter with counter_id 100500 already exists", "arguments": {"source_type": "remarketing_counters",  "source_ids": [100400]}}}
	- An attempt to activate a key with a counter already used by the user. The "source_ids" field contains IDs of the counters that caused the error.

	{"error": {"code": "cannot_add_source", "message": "Counter with counter_id 100500 is not added to account", "arguments": {"source_type": "remarketing_pricelists",  "source_ids": [100600]}}}
	- An attempt to activate a key with the price list linked to a counter that is unavailable to the user or for this key. The "source_ids" field contains IDs of the price lists that caused the error.

	403 Forbidden
	{"error": {"code": "access_denied", "message": "Key not available"}}
	- The user does not have access to the private key.

	404 Not Found
	{"error": {"code": "source_not_found", "message": "Object <object_type> with id <object_id> not found"}}
	- The "sources" parameter contains a non-existent data source.
```

### DELETE

The request deletes a key. User access to all data sources that were added using this key is revoked; all campaigns using these data sources are stopped.

Request example:

```http
  DELETE /api/v2/sharing_keys/abdef.json
```

Response status codes:

204 - The key was deleted.

404 - The key cannot be found.
