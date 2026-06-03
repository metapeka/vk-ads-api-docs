# Authorization

### Authorization

# OAuth2 Protocol Implementation in the API

The OAuth2 protocol is used for authentication and authorization in the API. From its specification, two standard flows are implemented: [Client Credentials Grant](https://tools.ietf.org/html/draft-ietf-oauth-v2-31#section-4.4) and [Authorization Code Grant](https://tools.ietf.org/html/draft-ietf-oauth-v2-31#section-4.1), and one non-standard – [Agency Client Credentials Grant](https://ads.vk.com/en#AgencyClientCredentialsGrant).

**Client Credentials Grant** is used to work with data of your own account via the API.

**Agency Client Credentials Grant** is used to work with data of agencies'/managers' own clients.

**Authorization Code Grant** is used to obtain access to data of third-party VK Ads accounts.

The first two flows are available to every API client; access to the Authorization Code Grant flow is provided only if the conditions are met.

[Instructions for obtaining access to the API](https://ads.vk.com/en/help/articles/help_api)

Using any of these methods, you will receive an Access Token object containing the keys access\_token and refresh\_token. Every API request must be signed with the access\_token key:

```html
GET /api/v2/ad_plans.json HTTP/1.1
Host: ads.vk.com
Authorization: Bearer {access_token}
```

Keep in mind that access to an account's data is only possible with a token obtained for that account. This means, for example, that you cannot view an agency client's campaigns by signing the request with the agency's own token. More details about account types and the authorization process are available in the extended authorization guide.

## Client Credentials Grant

To obtain an access token, you need to send a request of the following form:

```html
POST /api/v2/oauth2/token.json HTTP/1.1
Host: ads.vk.com
Content-Type: application/x-www-form-urlencoded
grant_type=client_credentials&client_id={client_id}&client_secret={client_secret}
```

If successful, the response will look like this:

```html
HTTP/1.1 200 OK
Content-Type: application/json; charset=UTF-8

{
  "access_token": "{access_token}",
  "token_type": "bearer",
  "scope": "{scope}",
  "expires_in": "86400",
  "refresh_token": "{refresh_token}"
}
```

## Agency Client Credentials Grant

This OAuth2 flow is not standard. It was implemented to allow agencies and managers to create access tokens for their clients without confirmation from the client. The flow is very similar to the standard Client Credentials Grant, except that the request must include an additional parameter "agency\_client\_name" or "agency\_client\_id" (username or user id from the [AgencyClients](https://ads.vk.com/doc/api/resource/AgencyClients) or [ManagerClients](https://ads.vk.com/doc/api/resource/ManagerClients) request):

```html
POST /api/v2/oauth2/token.json HTTP/1.1
Host: ads.vk.com
Content-Type: application/x-www-form-urlencoded

grant_type=agency_client_credentials&client_id={client_id}&client_secret={client_secret}&{agency_client_name|agency_client_id}={client_username|client_user_id}
```

## Authorization Code Grant

This OAuth2 flow allows you to obtain a token of a third-party VK Ads user. When enabling access to the Authorization Code Grant flow, one or more "redirect\_uri" addresses must be specified — VK Ads will redirect users to it after they grant (or deny) access to their account to the API client.

The access acquisition algorithm is as follows:

The API client redirects the user to the special page https://ads.vk.com/hq/settings/access?action=oauth2, adding additional parameters

- "response\_type" (with the value "code"),
- "state" (a token generated on the client side, used to prevent CSRF — may contain an arbitrary set of characters),
- its "client\_id",
- "redirect\_uri" (must match one of the "redirect\_uri" values specified when registering the client)
- the list of access rights "scope":

```html
GET /hq/settings/access?action=oauth2&response_type=code&client_id={client_id}&state={state}&scope={scopes}&redirect_uri={redirect_uri} HTTP/1.1
Host: ads.vk.com
```

On the page, the user agrees to grant access, and the service redirects them to the address specified by the "redirect\_uri" parameter, passing the parameters "code" (a special token with a lifetime of one hour) and "state" (the same value that was passed in the initial request):

```html
GET {redirect_uri:path}?code={code}&state={state}&user_id={user_id} HTTP/1.1
Host: <redirect_uri:host>
```

The response also contains the user\_id parameter, which includes the identifier of the user granting access.

You can also obtain user\_id by code:

```html
POST /api/v2/oauth2/code_info.json HTTP/1.1
Host: ads.vk.com
Content-Type: application/x-www-form-urlencoded
code={code}&client_id={client_id}&client_secret={client_secret}
```

Example of a successful response:

```html
HTTP/1.1 200 OK
Content-Type: application/json; charset=UTF-8

{
 "user":
 {
    "id": 100500,
    "username": "<username>",
    "types": ["advert", "agency_client"]
 }
}
```

If your application already has a token for this user, you can continue using the existing one to avoid exceeding the token limit and not duplicate tokens.

After receiving the "code" parameter, the client can request "access\_token" for further work with the API on behalf of the user. To do this, send a request to /api/v2/oauth2/token.json, passing the parameters "grant\_type" (with the value "authorization\_code"), "code" (the token received during the redirect back to "redirect\_uri"):

```html
POST /api/v2/oauth2/token.json HTTP/1.1
Host: ads.vk.com
Content-Type: application/x-www-form-urlencoded

grant_type=authorization_code&code={code}&client_id={client_id}
```

Response:

```html
HTTP/1.1 200 OK
Content-Type: application/json; charset=UTF-8
{
  "access_token": "{access_token}",
  "token_type": "Bearer",
  "scope": ["{scope1}", "{scope2}"],
  "expires_in": 86400,
  "refresh_token": "{refresh_token}"
}
```

The obtained access token is used to authenticate requests sent to the API on behalf of the user:

```html
GET /api/v2/ad_plans.json HTTP/1.1
Host: ads.vk.com
Authorization: Bearer {access_token}
```

To obtain tokens for clients of the agency or manager that granted access, you must use the extended Agency Client Credentials flow. For this, in addition to the agency\_client\_name parameter and others, you must specify the obtained agency token in the access\_token parameter:

```html
POST /api/v2/oauth2/token.json HTTP/1.1
Host: ads.vk.com
Content-Type: application/x-www-form-urlencoded

grant_type=agency_client_credentials&client_id={client_id}&client_secret={client_secret}&agency_client_name={client_username}&access_token={agency_access_token}
```

If the request is successful, the response will contain an access token to perform operations on behalf of the agency's or manager's client.

### Scopes — access rights

Access rights determine what actions an API client can perform with the data of the account that granted access. The required rights are specified comma-separated in the "scope" parameter of the user access request in the Authorization Code Grant flow. Depending on the user type, the requested access rights are divided into three groups.

For a regular advertiser user:

- read\_ads — reading statistics and ad campaigns;
- read\_payments — reading monetary transactions and balance;
- create\_ads — creating and editing ad campaign settings, banners, audiences (bids, status, targeting, etc.).

For agency users and representative office users:

- create\_clients — creating new clients;
- read\_clients — viewing clients and performing operations on their behalf;
- create\_agency\_payments — transferring funds to clients' accounts and back.

For manager users:

- read\_manager\_clients — viewing clients and performing operations on their behalf;
- edit\_manager\_clients — changing client parameters;
- read\_payments — reading monetary transactions and balance;

A single request may include rights from different groups. VK Ads determines the account type of the current user and enables only the corresponding rights. Moreover, if, for example, all rights are listed in the request and the user is an agency, they will be prompted to choose which account they want to grant access to: the agency account with agency rights, one of the manager accounts with manager rights, or one of the client accounts with rights to client data.

## Working with tokens

### Token count limit

For each clientId — user pair, no more than 5 tokens may exist simultaneously, regardless of token status. If the same account is connected to two different applications, each application will be able to issue up to 5 tokens for that account. The limit is fixed and cannot be increased under any circumstances.

Non-permanent tokens are automatically deleted after one month of inactivity (specified in the "expires\_in" field).

When the limit is reached, an attempt to obtain a new token will return an error with HTTP status code 403.

To avoid such errors, you must correctly refresh issued tokens and not create excessive duplicates.

### Deleting tokens

When the token count limit is reached, you can delete all tokens of a specific user yourself. To do this, use a request of the following form:

```html
POST /api/v2/oauth2/token/delete.json HTTP/1.1
Host: ads.vk.com
Content-Type: application/x-www-form-urlencoded

client_id={client_id}&client_secret={client_secret}&{username|user_id}={username|user_id}
```

where "username" is the user login for which the tokens must be deleted. If the "username" parameter is not provided, the tokens of the account for which API access was granted will be deleted.

### Access token lifetime

Each obtained access token is valid for one day by default. This is indicated by the "expires\_in" property in the response to the access token request.
The limited lifetime helps protect the "access\_token" value more reliably. Even if an attacker obtains the value of an "access\_token", they will not be able to make requests with it after it expires or after the first token refresh.

### Refreshing an access token

The Access Token object also includes the "refresh\_token" key — a special token used to refresh the access\_token key and extend the object's lifetime. This is handled by the [Refreshing an Access Token](https://tools.ietf.org/html/draft-ietf-oauth-v2-31#section-6) flow in the OAuth2 protocol.

Request to refresh an access token:

```html
POST /api/v2/oauth2/token.json HTTP/1.1
Host: ads.vk.com
Content-Type: application/x-www-form-urlencoded

grant_type=refresh_token&refresh_token={refresh_token}&client_id={client_id}&client_secret={client_secret}
```

Response example:

```html
HTTP/1.1 200 OK
Content-Type: application/json; charset=UTF-8

{
  "access_token": "{new_access_token}",
  "token_type": "bearer",
  "scope": "{scope}",
  "expires_in": "86400",
  "refresh_token": "{refresh_token}"
}
```

It is important to note that refreshing a token does not create a new instance: the "access\_token" value changes, and the old key value stops working. This can cause issues when working with the API in multiple threads: two threads may simultaneously detect that the token has expired and send a refresh request. The request that arrives first will refresh the token and start using it, while the second thread will refresh the token again, and the first thread will try to use a token that no longer exists.

One way to solve this problem is to catch the error about a non-existent token in the first thread and retrieve the token again from a shared storage for the threads — for example, a database where each thread writes the token after refreshing. You should also consider that writes to the storage can also be concurrent and use, for example, locks.

Another way to solve this problem could be enabling the option to refresh the "refresh\_token" on every "access\_token" refresh. Then the first thread will refresh both "access\_token" and "refresh\_token", and in the second thread you need to handle the error about an unknown "refresh\_token" and reread the "access\_token" from storage. But when refreshing the "refresh\_token", you must store its latest value; otherwise you will no longer be able to refresh the "access\_token", and you will have to issue a new one. This OAuth client option can currently be enabled only upon request to support.

One more option: proactive refresh of all expiring tokens. It means you should regularly check whether you have tokens expiring, for example, within the next half hour, and refresh them in a background process. But if you combine it with real-time refresh in production processes, you will still need to handle errors due to possible conflicts.

## Errors when using invalid tokens

When calling any API method, various errors related to an incorrect value or state of "access\_token" may be returned.

Such errors have code 401 and a common structure:

```html
{"code": "Error code", "message": "Error description"}
```

The response will also contain the header

```html
WWW-Authenticate: Bearer realm="api", error="Error code", error_description="Error description"
```

Possible errors:

| Error | Reason | Solution |
| --- | --- | --- |
| {"code": "invalid\_token", "message": "Unknown access token"} | The specified "access\_token" does not exist. The error is also possible if the token was not refreshed for a month and was therefore automatically deleted. | Issue a new token for this user and repeat the request using this token. |
| {"code": "expired\_token", "message": "Access token is expired"} | The "access\_token" has expired, but it has not been deleted yet. | Refresh "access\_token" using the "refresh\_token" method. |
| {"code": "invalid\_client", "message": "Invalid client id or secret provided"} | The error may be returned in several cases:<br>Incorrect "client\_id".<br>Incorrect "client\_secret".<br>The OAuth2 client is blocked. The OAuth2 client (essentially, API access) may be blocked in case of violations of the API usage rules and similar cases. | Make sure you are passing the correct "client\_id" and "client\_secret" values. Contact support. |
| {"code": "invalid\_user", "message": "User is blocked"} | The user for whom the token was issued is blocked. | Send the request with a token of another user. |
| {"code": "revoked\_token", "message": "Access token has been revoked"} | The user who previously granted your application access to their account has revoked that access. | Request the user to grant access again. It is also recommended to stop any requests on behalf of this user until they grant access again. |
| {"code": "revoked\_token", "message": "Access token has been revoked"} | The user who obtained the token via the Agency Client Credentials flow (using an agency or manager token) is no longer a client of the agency or is no longer linked to the manager. |  |
