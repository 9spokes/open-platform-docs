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
  "data": [
    {
      "account_identifier": "string",
      "account_name": "string",
      "account_code": "string",
      "account_type": "string",
      "account_category": "string",
      "account_type_bank": "string",
      "account_currency": "string",
      "account_status": "string",
      "value_type": "string",
      "total_value": "number"
    }
  ]
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
  "data": [
    {
      "account_category": "revenue",
      "account_code": "200",
      "account_currency": "AUD",
      "account_identifier": "e2bacdc6-2006-43c2-a5da-3c0e5f43b452",
      "account_status": "ACTIVE",
      "value_type": "credit",
      "account_name": "Sales",
      "account_type": "sales",
      "account_type_bank": "",
      "system_account": "",
      "total_value": 32431.0
    },
    {
      "account_code": "400",
      "account_currency": "AUD",
      "account_identifier": "d392fe47-c99d-499e-a200-46709dd6b6e7",
      "account_name": "Advertising",
      "account_status": "ACTIVE",
      "system_account": "",
      "value_type": "debit",
      "account_category": "expense",
      "account_type_bank": "",
      "total_value": 1830.18,
      "account_type": "overheads"
    },
    {
      "account_currency": "AUD",
      "account_identifier": "959af5f4-9925-44e8-b283-7ddf4b427238",
      "account_status": "ACTIVE",
      "value_type": "debit",
      "system_account": "",
      "total_value": 31.5,
      "account_category": "expense",
      "account_code": "404",
      "account_name": "Bank Fees",
      "account_type": "overheads",
      "account_type_bank": ""
    }
  ]
}
```

Below is the metadata wrapper used to classify and search timeline balance data. The timeline balance data is stored under the `data` key.

| Field                    | Data Type               | Description                                                                                                  |
| :----------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------ |
| `user`                   | `UUIDv4`                | This is the user's id of the company that this transaction belongs to.                                       |
| `company`                | `UUIDv4`                | The company id                                                                                               |
| `datasource`             | `string`                |                                                                                                              |
| `connection_id`          | `UUIDv4`                | This is the connection_id which was used to retrieve the origin data.                                        |
| `object_class`           | `timeline-balance`      | This is used to retrieve a specific type of data schema:                                                     |
| `object_category`        | `general-ledger`        | This is used to categorise the document.                                                                     |
| `object_type`            | `day` or `month`        | This is the associated time dimension of the metric.                                                         |
| `object_origin_category` | `bookkeeping`           | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
| `object_origin_type`     | `accounting`            | This is the specific type of origin related to the origin category                                           |
| `object_origin`          | `string`                | This is the name of the application which matches the app-key in the connection records.                     |
| `balance_date`           | `Date`                  | The trial balance's date                                                                                     |
| `currency`               | `string`                | Currency of data                                                                                             |
| `object_creation_date`   | `Date`                  | Creation time of document                                                                                    |
| `data`                   | Timeline Balance Object | The actual timeline balance data, see below                                                                  |

Below is the content of the `data` object used with `timeline-balance`.

| Field                | Data Type              | Description                                                                                                                   |
| :------------------- | ---------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `account_identifier` | `string`               | Account ID                                                                                                                    |
| `account_name`       | `string`               | Account name                                                                                                                  |
| `account_code`       | `string`               | The chart of accounts code                                                                                                    |
| `account_type`       | `string`               | Type of the account, possible values are `bank`, `current`, `equity`, `fixed`, `overheads`, `payroll`, `sales`, `tax`, `term` |
| `account_category`   | `string`               | The category of account this is. Must be one of `assets`, `equity`, `expense`, `liability`, `revenue`                         |
| `account_currency`   | `string[3]`            | Currency of the account                                                                                                       |
| `account_status`     | `ACTIVE` or `INACTIVE` | Whether the account is active or not                                                                                          |
| `value_type`         | `debit` or `credit`    | Debit/Credit                                                                                                                  |
| `total_value`        | `number`               | The value of the account                                                                                                      |
