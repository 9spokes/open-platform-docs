## Managing Apps

### List Apps

> Use a `GET` request to fetch the list of apps configured

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/organization/apps \
    -H "Authorization: ${API_KEY}"
```

> The `details` key contains an array of apps and their status

```json
{
    "status": "ok",
    "details": [
        {
            "name": "xero",
            "status": "enabled",
            "client_id": "91E5715...BC1648",
            "client_secret": "4e7747ce...0775166c5f",
            "recurring": true
        },
        ...
    ]
}
```

<span class="api api-get"></span> <code>/organization/apps</code>

This endpoint is used to retrieve the status of all supported apps for your account.

### Enable App

> Enable an app by providing the OAuth2 client credentials in the body

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/organization/apps/xero \
    -X PUT \
    -d "client_id=91E5715...BC1648&client_secret=4e7747ce...0775166c5f&recurring=true" \
    -H "Content-type: application/x-www-form-urlencoded" \
    -H "Authorization: ${API_KEY}"
```

> The response indicates whether the update was successful or not.

```json
{
    "status": "ok",
    "details": "The Xero app credentials were updated successfully"
}
```

<span class="api api-put"></span> <code>/organization/apps/{app}</code>

This endpoint is used to enable an app integration and updating the OAuth2 client credentials.  The `client_id` and `client_secret` are required whereas the `recurring` field defaults to `false` if omitted.

| Field             | Location | Type     | Description                                                                      |
| :---------------- | -------- | -------- | -------------------------------------------------------------------------------- |
| **app**           | Path     | *string* | The app to update                                                                |
| **client_id**     | Body     | *string* | The OAuth2 client ID                                                             |
| **client_secret** | Body     | *string* | The OAuth2 client secret                                                         |
| **recurring**     | Body     | *bool*   | Whether to continuously pull data for this connection or not, defaults to `false` |

### Disable App

> Disable an app by issuing a `DELETE` request

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/organization/apps/xero \
    -X DELETE \
    -H "Authorization: ${API_KEY}"
```

> The response is always positive, even if the app is not previously enabled

```json
{
    "status": "ok",
    "details": "The Xero app was successfully removed"
}
```

<span class="api api-delete"></span> <code>/organization/apps/{app}</code>

This endpoint is used to disable an app integration.  The API call always succeeds.

| Field   | Location | Type     | Description       |
| :------ | -------- | -------- | ----------------- |
| **app** | Path     | *string* | The app to update |
