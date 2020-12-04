## Account Balance

This is the specification for the account balances of a user. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

### Field Description

> Below is the schema definition for a `account-balance` record

```json
{
    "object_creation_date": "string",
    "object_type": "string",
    "object_class": "string",
    "object_category": "string",
    "object_origin": "string",
    "object_origin_category": "string",
    "object_origin_type": "string",
    "balance_date": "string",
    "user": "string",
    "connection_id": "string",
    "data": [
        {
            "account_active": "boolean",
            "account_balance": "number",
            "account_currency": "string",
            "account_id": "string",
            "account_name": "string"
        },
        {
            "account_id": "string",
            "account_name": "string",
            "account_active": "boolean",
            "account_balance": "number",
            "account_currency": "string"
        }
    ]
}
```

> Below is a sample document

```json
{
    "object_creation_date": "2020-11-02T11:00:02.617Z",
    "object_type": "day",
    "object_class": "bank",
    "object_category": "account-balance",
    "object_origin": "intuit",
    "object_origin_category": "bookkeeping",
    "object_origin_type": "accounting",
    "balance_date": "2020-11-02T00:00:00.000Z",
    "user": "ebd35d68-33d7-4655-9eba-9f5b09a9a29c",
    "connection_id": "a5977ea6-146d-426f-9879-47516a747566",
    "data": [
        {
            "account_active": true,
            "account_balance": 10951677.31,
            "account_currency": "GBP",
            "account_id": "59",
            "account_name": "My Savings (XXXXXX 2222)"
        },
        {
            "account_id": "69",
            "account_name": "PayPal Funds Transfer Account",
            "account_active": true,
            "account_balance": 0.0,
            "account_currency": "GBP"
        }
    ]
}
```

Below is the metadata wrapper used to classify and search account balance data. The account balance data is stored under the `data` key.

| Field                    | Data Type               | Description                                                                                                  |
| :----------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------ |
| `user`                   | `UUIDv4`                | This is the user's id of the company that this transaction belongs to.                                       |
| `company`                | `UUIDv4`                | The company id                                                                                               |
| `datasource`             | `string`                |                                                                                                              |
| `connection_id`          | `UUIDv4`                | This is the connection_id which was used to retrieve the origin data.                                        |
| `object_class`           | `account-balance`       | This is used to retrieve a specific type of data schema:                                                     |
| `object_category`        | `general-ledger`        | This is used to categorise the document.                                                                     |
| `object_type`            | `day` or `month`        | This is the associated time dimension of the metric.                                                         |
| `object_origin_category` | `bookkeeping`           | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
| `object_origin_type`     | `accounting`            | This is the specific type of origin related to the origin category                                           |
| `object_origin`          | `string`                | This is the name of the application which matches the app-key in the connection records.                     |
| `balance_date`           | `Date`                  | The account balance's date                                                                                     |
| `currency`               | `string`                | Currency of data                                                                                             |
| `object_creation_date`   | `Date`                  | Creation time of document                                                                                    |
| `data`                   | Account Balance Object | The actual timeline balance data, see below                                                                  |

Below is the content of the `data` object used with `timeline-balance`.

| Field                | Data Type              | Description                                                                                                                   |
| :------------------- | ---------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `account_id`         | `string`               | Account ID                                                                                                                    |
| `account_name`       | `string`               | Account name                                                                                                                  |
| `account_currency`   | `string[3]`            | Currency of the account                                                                                                       |
| `account_active`     | `boolean`              | Whether the account is active or not                                                                                          |
| `account_balance`    | `number`               | The value of the account                                                                                                      |
