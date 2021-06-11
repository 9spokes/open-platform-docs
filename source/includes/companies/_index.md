# Companies

A **Company** object represents a real business or organization.  Companies are the most fundamental data container whereby all connections and all their associated data must belong to a company object.

## Create New Company

> Create a new company by providing a company `name`

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/companies \
    -X POST \
    -d "name=9Socks" \
    -H "Content-type: application/x-www-form-urlencoded" \
    -H "Authorization: ${API_KEY}"
```

> The response includes the new connection ID under the `id` key and the `authorize_url` require to activate the connection.

```json
{
    "status": "ok",
    "details": {
        "id": "97436a79-0293-485e-8aad-eb629f5c9dfd",
        "name": "9Socks",
        "created": "2020-12-09T22:26:59.999Z",
        "updated": "2020-12-09T22:27:00Z",
    }
}
```

<span class="api api-post"></span> <code>/companies</code>

Creating a new company is done using a `POST` request to the `companies` endpoint.

| Field    | Location | Type     | Description                       |
| :------- | -------- | -------- | --------------------------------- |
| **name** | Form     | *string* | The name of the Company to create |

## List Companies

> Fetch all companies

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/companies \
    -H "Authorization: ${API_KEY}"
```

> The `details` key is an array of companies

```json
{
    "status": "ok",
    "details": [
        {
            "id": "97436a79-0293-485e-8aad-eb629f5c9dfd",
            "name": "9Socks",
            "created": "2020-12-09T22:26:59.999Z",
            "updated": "2020-12-09T22:27:00Z",
        }
    ]
}
```

<span class="api api-get"></span> <code>/companies/{company}</code>

Retrieving all the companies is done using a `GET` request to the `companies` endpoint.

## Get a Company

> Retrieves a single company with ID `97436a79-0293-485e-8aad-eb629f5c9dfd`

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/companies/97436a79-0293-485e-8aad-eb629f5c9dfd \
    -H "Authorization: ${API_KEY}"
```

> The `details` key is the connection object

```json
{
    "status": "ok",
    "details": {
        "id": "97436a79-0293-485e-8aad-eb629f5c9dfd",
        "name": "9Socks",
        "created": "2020-12-09T22:26:59.999Z",
        "updated": "2020-12-09T22:27:00Z",
    }
}
```

<span class="api api-get"></span> <code>/companies/{company}</code>

Retrieving a specific company record is done using a `GET` request specifying the `company` as path parameters.

| Field       | Location | Type     | Description                       |
| :---------- | -------- | -------- | --------------------------------- |
| **company** | Path     | *string* | The ID of the company to retrieve |

## Remove a Company

> Delete a company with ID `97436a79-0293-485e-8aad-eb629f5c9dfd`

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/companies/97436a79-0293-485e-8aad-eb629f5c9dfd \
    -X DELETE \
    -H "Authorization: ${API_KEY}"
```

> The operation `status` is either `ok` or `err`

```json
{
    "status": "ok",
    "details": "Company deleted successfully"
}    
```

<span class="api api-delete"></span> <code>/companies/{company}</code>

Removing a company is done by issuing a `DELETE` request and specifying the `company` ID in the path.

| Field       | Location | Type     | Description                     |
| :---------- | -------- | -------- | ------------------------------- |
| **company** | Path     | *string* | The ID of the company to remove |

<aside class="warning">
Deleting a company also removes all the connections and their associated data. It is irreversible!
</aside>
