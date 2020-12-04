### Tax Rates

This is the specification for the Tax Rates of business . It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

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
            "tax_id" : "string",
            "tax_name" : "string",
            "tax_rate" : "number"
        }
    ]
}
```

> Below is a sample document

```json
{
    "connection_id" : "f4592653-7c08-4722-8920-c280c95991d7",
    "user" : "08da4bfe-a8df-4729-82af-36726a18e746",
    "company" : "7af2b057-0ac5-4818-9d50-0c48006985d5",
    "cycle" : "day",
    "datasource" : "tax_rates",
    "object_origin_category" : "bookkeeping",
    "object_origin_type" : "accounting",
    "object_origin" : "sageone",
    "object_creation_date" : "2020-10-30T01:56:46.611Z",
    "object_class" : "rates",
    "object_type" : "tax-rates",
    "object_category" : "tax",
    "data" : [
        {
            "tax_id" : "GB_STANDARD",
            "tax_name" : "Standard 20.00%",
            "tax_rate" : 0.0
        },
        {
            "tax_id" : "GB_LOWER",
            "tax_name" : "Lower Rate 5.00%",
            "tax_rate" : 0.0
        }
    ]
}
```

| Field                    | Data Type               | Description                                                                                                  |
| :----------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------ |
| `user`                   | `UUIDv4`                | This is the user's id of the company that this transaction belongs to.                                       |
| `company`                | `UUIDv4`                | The company id                                                                                               |
| `datasource`             | `string`                |                                                                                                              |
| `connection_id`          | `UUIDv4`                | This is the connection_id which was used to retrieve the origin data.                                        |
| `object_class`           | `rates`       | This is used to retrieve a specific type of data schema:                                                               |
| `object_category`        | `general-ledger`        | This is used to categorise the document.                                                                     |
| `object_type`            | `day` or `month`        | This is the associated time dimension of the metric.                                                         |
| `object_origin_category` | `bookkeeping`           | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
| `object_origin_type`     | `accounting`            | This is the specific type of origin related to the origin category                                           |
| `object_origin`          | `string`                | This is the name of the application which matches the app-key in the connection records.                     |
| `object_origin`          | `string`                | This is the name of the application which matches the app-key in the connection records.                     |
| `object_creation_date`   | `Date`                  | Creation time of document                                                                                    |
| `data`                   | Tax Rate Array of objects | The actual timeline balance data, see below                                                                |

Below is the content of the `data` object used with `tax-rates`.

| Field                | Data Type              | Description                                                                                                               |
| :------------------- | ---------------------- | --------------------------------------------------------------------------------------------------------------------------|
| `tax_id`             | `string`               | Tax ID                                                                                                                    |
| `tax_name`           | `string`               | Tax name                                                                                                                  |
| `tax_rate`           | `number`               | The value of the tax                                                                                                      |
