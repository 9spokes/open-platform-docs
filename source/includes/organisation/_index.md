# Organisation

The organisation endpoint is used to manage settings & preferences for your account.

## Redirect URL

> Update the redirect URL using a PUT request

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/organisation/redirect_url \
    -X PUT \
    -d "redirect_url=https://example.com/callback" \
    -H "Authorization: ${API_KEY}"
```

> The response indicates whether the update was successful or not.

```json
{
    "status": "ok",
    "details": "The redirect URL was set successfully"
}
```

<span class="api api-put"></span> <code>/organisation/redirect_url</code>

This endpoint is used to configure the URL where your users are redirected to after completing a consent flow.  Whether the flow succeeds or not, the `redirect_url` will be used to redirect the user agents back to your platform.

The `redirect_url` must be an absolute URL and it must be URL-encoded.

| Field            | Location | Type     | Description                                       |
| :--------------- | -------- | -------- | ------------------------------------------------- |
| **redirect_url** | Body     | *string* | The URL where users are sent after a consent flow |

## App Credentials

> Enable an App by providing the OAuth2 client credentials in the body

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/organisation/apps/xero \
    -X PUT \
    -d "client_id=91E5715...BC1648&client_secret=4e7747ce...0775166c5f&recurring=true" \
    -H "Authorization: ${API_KEY}"
```

> The response indicates whether the update was successful or not.

```json
{
    "status": "ok",
    "details": "The Xero app credentials were updated successfully"
}
```

<span class="api api-put"></span> <code>/organisation/apps/{app}</code>

This endpoint is used to enable an App integration and updating the OAuth2 client credentials.  The `client_id` and `client_secret` are required whereas the `recurring` field defaults to `false` if omited.

| Field             | Location | Type     | Description                                                                      |
| :---------------- | -------- | -------- | -------------------------------------------------------------------------------- |
| **app**           | Path     | *string* | The app to update                                                                |
| **client_id**     | Body     | *string* | The OAuth2 client ID                                                             |
| **client_secret** | Body     | *string* | The OAuth2 client secret                                                         |
| **recurring**     | Body     | *bool*   | Whether to continously pull data for this connection or not, defaults to `false` |
