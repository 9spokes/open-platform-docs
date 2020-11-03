## Timeline Balance

This is the specification for the trial balances of a user. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

### Field Description

> Below is the schema definition for a `timeline-balance` record

```json
{
  "user": "string",
  "company": "string",
  "datasource": "string",
  "connection_id": "string",
  "object_class": "string",
  "object_category": "string",
  "object_type": "string",
  "object_origin_category": "string",
  "object_origin_type": "string",
  "object_origin": "string",
  "balance_date": "string",
  "currency": "string",
  "object_creation_date": "string",
  "data": {
    "account_identifier": "string",
    "account_name": "string",
    "account_code": "string",
    "account_type": "string",
    "account_category": "string",
    "account_type_bank": "string",
    "account_currency": "string",
    "account_status": "string",
    "value_type": "string",
    "total_value": "number",
    "value_currency": "string"
  }
}
```

> Below is a sample document

```json
{
  "user": "0c529257-a362-43ef-ae3a-9c9ecf583fbd",
  "company": "56728df1-58bf-48eb-9302-406b7f4a2489",
  "datasource": "trial_balance",
  "connection_id": "56728df1-58bf-48eb-9302-406b7f4a2489",
  "object_class": "timeline-balance",
  "object_category": "general-ledger",
  "object_type": "day",
  "object_origin_category": "bookkeeping",
  "object_origin_type": "accounting",
  "object_origin": "xero",
  "balance_date": "2020-11-03T09:37:12.106Z",
  "currency": "NZD",
  "object_creation_date": "2020-11-03T09:37:12.106Z",
  "data": {
    "account_identifier": "83e944867f7b11e691e20a5d7cf84c3e",
    "account_name": "Business Savings Account",
    "account_code": "1000",
    "account_type": "bank",
    "account_category": "assets",
    "account_currency": "NZD",
    "account_status": "ACTIVE",
    "value_type": "Debit",
    "total_value": 99999999
  }
}
```

This is the example format of the JSON object in the 9Spokes format for trial balance.

| Field                    | Data Type              | Description                                                                                                  |
| :----------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------ |
| `user`                   | `string`               | This is the user's id of the company that this transaction belongs to.                                       |
| `company`                | `string`               | The company id                                                                                               |
| `datasource`             | `string`               |                                                                                                              |
| `connection_id`          | `string`               | This is the connection_id which was used to retrieve the origin data.                                        |
| `object_class`           | `string`               | This is used to retrieve a specific type of data schema:                                                     |
| `object_category`        | `string`               | This is used to categorise the document.                                                                     |
| `object_type`            | `string`               | This is the associated time dimension of the metric.                                                         |
| `object_origin_category` | `string`               | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
| `object_origin_type`     | `string`               | This is the specific type of origin related to the origin category                                           |
| `object_origin`          | `string`               | This is the name of the application which matches the app-key in the connection records.                     |
| `balance_date`           | `string`               | The trial balance's date                                                                                     |
| `currency`               | `string`               | Currency of data                                                                                             |
| `object_creation_date`   | `string`               | Creation time of document                                                                                    |
| `account_identifier`     | `string`               | Account ID                                                                                                   |
| `account_name`           | `string`               | Account name                                                                                                 |
| `account_code`           | `string`               | The chart of accounts code                                                                                   |
| `account_type`           | `string`               | Type of the account                                                                                          |
| `account_category`       | `string`               | Asset, liability, equity, expense                                                                            |
| `account_type_bank`      | `string`               | Xero specific                                                                                                |
| `account_currency`       | `string`               | Currency of the account                                                                                      |
| `account_status`         | `ACTIVE` or `INACTIVE` | Whether the account is active or not                                                                         |
| `value_type`             | `string`               | Debit/Credit                                                                                                 |
| `total_value`            | `number`               | The value of the account                                                                                     |
| `value_currency`         | `string`               |                                                                                                              |
