## Managing Redirect URL


### Get Redirect URL

> Update the redirect URL using a `PUT` request

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/organization/redirect_url \
    -X PUT \
    -d "redirect_url=https://example.com/callback" \
    -H "Content-type: application/x-www-form-urlencoded" \    
    -H "Authorization: ${API_KEY}"
```

> The response indicates whether the update was successful or not.

```json
{
    "status": "ok",
    "details": "The redirect URL was set successfully"
}
```

<span class="api api-put"></span> <code>/organization/redirect_url</code>

This endpoint is used to configure the URL where your users are redirected to after completing a consent flow.  Whether the flow succeeds or not, the `redirect_url` will be used to redirect the user agents back to your platform.

The `redirect_url` must be an absolute URL and it must be URL-encoded.

| Field            | Location | Type     | Description                                       |
| :--------------- | -------- | -------- | ------------------------------------------------- |
| **redirect_url** | Body     | *string* | The URL where users are sent after a consent flow |

### Set Redirect URL

> Retrieve the current redirect URL using a `GET` request

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/organization/redirect_url \
    -H "Authorization: ${API_KEY}"
```

> The `details.redirect_url` key contains the current redirect URL

```json
{
    "status": "ok",
    "details": {
        "redirect_url": "https://example.com/callback"
    }
}
```

<span class="api api-get"></span> <code>/organization/redirect_url</code>

This endpoint is used to retrieve the currently configured redirect URL.
