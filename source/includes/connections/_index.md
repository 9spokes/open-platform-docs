# Connections

A **connection** represents a link to a data provider.  Connections belong to companies and they are mutually exclusive from one another.  Only a single connection of any type can belong to any given company.

Connections transition through several preset stages as the end-user creates, consents to, and terminates a connection to a given app. The supported connection states are listed below.

## Connection Lifecycle

| State           | Description                                                                     |
| :-------------- | ------------------------------------------------------------------------------- |
| `NEW`           | The connection was created and has not yet been authorized                      |
| `ACTIVE`        | The connection has been authorized and data is flowing                             |
| `NOT_CONNECTED` | The connection to the app provider has been lost and user intervention is required |
| `REMOVED`       | The connection has been disabled and is pending removal                         |

## Create New Connection

> Create a new connection of type `sage` for company ID `9091a260-1292-4874-bbe5-3693a341d332`

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/companies/9091a260-1292-4874-bbe5-3693a341d332/connections \
    -X POST \
    -d "app=sage" \
    -H "Content-type: application/x-www-form-urlencoded" \
    -H "Authorization: ${API_KEY}"
```

> The response includes the new connection ID under the `id` key and the `authorize_url` require to activate the connection.

```json
{
    "status": "ok",
    "details": {
        "id": "087cd170-ec96-4898-bf97-2ecf82ab7cc1",
        "created": "2021-05-11T10:46:39.589Z",
        "modified": "2021-05-11T11:00:04.415Z",
        "osp": "sage",
        "status": "NEW",
        "authorize_url": "https://cb.9spokes.io/redirect?q=4QICwWaXTrrRG%2FVOABjOuQqKNbuoQv3x2n6qyfVpPuIVxAmSZwIQOw3idGUATLJ9VBgomwzm7il40fG5ElywgW5lKXOHT54FJqG5h5vGtBWWLEjxpQaM7eCPDps3aPD62OTk2mU03ZtfYCdzLj40SXrT3k5YyQqrX91ZUuZLIrIt%2BaIRB4NiNLlDYMhY%2FZHtsB5F19NqqL7TeXu5r14vz4Uh8f3%2BXrRQG1sAViQOR1PW7ZU7w2PrQzK77sm7%2BUmejFTuUqfWBZfS8dASQ3i51yWX%2Fbu0lD1IUimI4KsUfmaHXldydDhj41%2B1sFJG7dNk9GwHpHFPag4SKHbIV49nRYZUQJAxRqVfHYDihHrYOgQEwx6b2KJQhFPYDg60OnMdJLVEx7mn0ElK40IWYQ5omYbNxea9jhGifcGqRzKAZGWlUmY0ETK7GQD3DGZdMC2X4YtfgGp9gKF5mfMMIBWr8w%3D%3D"
    }
}    
```

<span class="api api-post"></span> <code>/companies/{company}/connections</code>

Creating a new connection for a given company is done using a `POST` request to the `connections` endpoint for that company.

| Field       | Location | Type     | Description                    |
| :---------- | -------- | -------- | ------------------------------ |
| **company** | Path     | *string* | The ID of the company          |
| **app**     | Form     | *string* | The name of the app to connect |

The `authorize_url` key in the response should be used to redirect the user agent.

## List Connections

> Fetch all connections for company ID `9091a260-1292-4874-bbe5-3693a341d332`

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/companies/9091a260-1292-4874-bbe5-3693a341d332/connections \
    -H "Authorization: ${API_KEY}"
```

> The `details` key is an array of connections

```json
{
    "status": "ok",
    "details": [
        {
            "id": "087cd170-ec96-4898-bf97-2ecf82ab7cc1",
            "created": "2021-05-11T10:46:39.589Z",
            "modified": "2021-05-11T11:00:04.415Z",
            "osp": "sage",
            "status": "ACTIVE",
            "authorize_url": "https://cb.9spokes.io/redirect?q=4QICwWaXTrrRG%2FVOABjOuQqKNbuoQv3x2n6qyfVpPuIVxAmSZwIQOw3idGUATLJ9VBgomwzm7il40fG5ElywgW5lKXOHT54FJqG5h5vGtBWWLEjxpQaM7eCPDps3aPD62OTk2mU03ZtfYCdzLj40SXrT3k5YyQqrX91ZUuZLIrIt%2BaIRB4NiNLlDYMhY%2FZHtsB5F19NqqL7TeXu5r14vz4Uh8f3%2BXrRQG1sAViQOR1PW7ZU7w2PrQzK77sm7%2BUmejFTuUqfWBZfS8dASQ3i51yWX%2Fbu0lD1IUimI4KsUfmaHXldydDhj41%2B1sFJG7dNk9GwHpHFPag4SKHbIV49nRYZUQJAxRqVfHYDihHrYOgQEwx6b2KJQhFPYDg60OnMdJLVEx7mn0ElK40IWYQ5omYbNxea9jhGifcGqRzKAZGWlUmY0ETK7GQD3DGZdMC2X4YtfgGp9gKF5mfMMIBWr8w%3D%3D"
        }
    ]
}
```

<span class="api api-get"></span> <code>/companies/{company}/connections</code>

Retrieving all the connections for a given company is done using a `GET` request to the `connections` endpoint for that company.

| Field       | Location | Type     | Description           |
| :---------- | -------- | -------- | --------------------- |
| **company** | Path     | *string* | The ID of the company |

## Get a Connection

> Retrieves a single connection with ID `087cd170-ec96-4898-bf97-2ecf82ab7cc1`

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/companies/9091a260-1292-4874-bbe5-3693a341d332/connections/087cd170-ec96-4898-bf97-2ecf82ab7cc1 \
    -H "Authorization: ${API_KEY}"
```

> The `details` key is the connection object

```json
{
    "status": "ok",
    "details": {
        "id": "087cd170-ec96-4898-bf97-2ecf82ab7cc1",
        "created": "2021-05-11T10:46:39.589Z",
        "modified": "2021-05-11T11:00:04.415Z",
        "osp": "sage",
        "status": "ACTIVE",
        "authorize_url": "https://cb.9spokes.io/redirect?q=4QICwWaXTrrRG%2FVOABjOuQqKNbuoQv3x2n6qyfVpPuIVxAmSZwIQOw3idGUATLJ9VBgomwzm7il40fG5ElywgW5lKXOHT54FJqG5h5vGtBWWLEjxpQaM7eCPDps3aPD62OTk2mU03ZtfYCdzLj40SXrT3k5YyQqrX91ZUuZLIrIt%2BaIRB4NiNLlDYMhY%2FZHtsB5F19NqqL7TeXu5r14vz4Uh8f3%2BXrRQG1sAViQOR1PW7ZU7w2PrQzK77sm7%2BUmejFTuUqfWBZfS8dASQ3i51yWX%2Fbu0lD1IUimI4KsUfmaHXldydDhj41%2B1sFJG7dNk9GwHpHFPag4SKHbIV49nRYZUQJAxRqVfHYDihHrYOgQEwx6b2KJQhFPYDg60OnMdJLVEx7mn0ElK40IWYQ5omYbNxea9jhGifcGqRzKAZGWlUmY0ETK7GQD3DGZdMC2X4YtfgGp9gKF5mfMMIBWr8w%3D%3D"
    }
}
```

<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}</code>

Retrieving the connection record for a given company is done using a `GET` request specifying both the `connection` and the `company` as path parameters.

The result contains the state of the connection (see [connection lifecycle](#connection-lifecycle)) as well as the data extraction status for each underlying data source.

| Field          | Location | Type     | Description                          |
| :------------- | -------- | -------- | ------------------------------------ |
| **company**    | Path     | *string* | The ID of the company                |
| **connection** | Path     | *string* | The ID of the connection to retrieve |

## Remove a Connection

> Delete a connection for company ID `9091a260-1292-4874-bbe5-3693a341d332` with ID `087cd170-ec96-4898-bf97-2ecf82ab7cc1`

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/companies/9091a260-1292-4874-bbe5-3693a341d332/connections/087cd170-ec96-4898-bf97-2ecf82ab7cc1 \
    -X DELETE \
    -H "Authorization: ${API_KEY}"
```

> The operation `status` is either `ok` or `err`

```json
{
    "status": "ok",
    "details": "Connection deleted successfully"
}    
```

<span class="api api-delete"></span> <code>/companies/{company}/connections/{connection}</code>

Removing a connection for a given company is done by issuing a `DELETE` request and specifying both the `connection` and `company` in the path.

| Field          | Location | Type     | Description                        |
| :------------- | -------- | -------- | ---------------------------------- |
| **company**    | Path     | *string* | The ID of the company              |
| **connection** | Path     | *string* | The ID of the connection to remove |

<aside class="warning">
Deleting a connection removes all the data associated with that company, it's irreversible!
</aside>

## Get Connection Data Status

> Get a connection data status for company ID: `9091a260-1292-4874-bbe5-3693a341d332` with connection ID: `087cd170-ec96-4898-bf97-2ecf82ab7cc1`

```sh
# The example below assumes you have the API_ROOT and API_KEY environment variables set
$ curl https://${API_ROOT}/companies/9091a260-1292-4874-bbe5-3693a341d332/connections/087cd170-ec96-4898-bf97-2ecf82ab7cc1/status \
    -X GET \
    -H "Authorization: ${API_KEY}"
```

> The operation `status` is either `ok` or `err`

```json
{
    "status": "ok",
    "correlationId": "e9138503-c8a3-412e-8f68-403adc547b1e",
    "details": [
        {
            "datasource": "products",
            "total": 1,
            "completed": 1,
            "last_updated": "2021-09-16T23:41:36.814Z"
        },
        {
            "datasource": "bank_accounts",
            "total": 1,
            "completed": 1,
            "last_updated": "2021-09-22T12:00:45.327Z"
        },
        {
            "datasource": "invoices",
            "total": 395,
            "completed": 395,
            "last_updated": "2021-09-23T04:00:41.429Z"
        },
        {
            "datasource": "bills",
            "total": 395,
            "completed": 395,
            "last_updated": "2021-09-23T04:00:41.403Z"
        },
        {
            "datasource": "trial_balance",
            "total": 96,
            "completed": 96,
            "last_updated": "2021-09-22T13:45:45.575Z"
        },
        {
            "datasource": "business",
            "total": 1,
            "completed": 1,
            "last_updated": "2021-09-16T23:41:35.973Z"
        }
    ]
} 
```

<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/status</code>

Getting data status of a connection for a given company is done by issuing a `GET` request and specifying both the `connection` and `company` in the path.

| Field          | Location | Type     | Description                        |
| :------------- | -------- | -------- | ---------------------------------- |
| **company**    | Path     | *string* | The ID of the company              |
| **connection** | Path     | *string* | The ID of the connection to remove |
