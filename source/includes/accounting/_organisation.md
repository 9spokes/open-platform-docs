## Organisation

This is the specification for the organisation of a user. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

### Field Description

> Below is the schema definition for a `organisation` record

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
  "object_creation_date": "date",
  "updated" : "date",
  "data" : {
      "sales_tax_period" : "string",
      "subscription_start" : "string",
      "accounting_method" : "string",
      "base_currency" : "string",
      "business_type" : "string",
      "trial_balance_history_available" : "boolean",
      "invoices_history_available" : "boolean",
      "payments_history_available" : "boolean",
      "trial_balance_daily_history_daily_available" : "boolean",
      "business_identifier" : "string",
      "fyear_end_month" : "number",
      "organisation_type" : "string",
      "short_code" : "string",
      "trading_name" : "string",
      "country_code" : "string",
      "fyear_end_day" : "number"
  },
}
```

```json
{
    "user": "0c529257-a362-43ef-ae3a-9c9ecf583fbd",
    "company": "56728df1-58bf-48eb-9302-406b7f4a2489",
    "datasource": "organisation",
    "connection_id": "56728df1-58bf-48eb-9302-406b7f4a2489",
    "object_class": "organisation",
    "object_category": "bookkeeping",
    "object_type": "company-details",
    "object_origin_category": "bookkeeping",
    "object_origin_type": "accounting",
    "object_origin": "xero",
    "object_creation_date": "2020-11-03T09:37:12.106Z",
    "updated" : "2020-11-03T10:21:03+13:00",
    "application_settings" : {
        "sales_tax_period" : "QUARTERLY1",
        "subscription_start" : "/Date(1603925122000)/",
        "accounting_method" : "Accrue",
        "base_currency" : "AUD",
        "business_type" : "IT",
        "business_identifier" : "B0193783",
        "organisation_type" : "COMPANY",
        "short_code" : "!7YLwG",
        "trading_name" : "9spokestest",
        "country_code" : "AU",
        "fyear_end_month" : 6.0,
        "fyear_end_day" : 30.0
    },
}
```

Below is the metadata wrapper used to classify and search organisation data. The organisation data is stored under the `data` key.

| Field                    | Data Type               | Description                                                  |
| :----------------------- | :---------------------- | :----------------------------------------------------------- |
| **user**                   | *UUIDv4*                | This is the user's id of the company that this transaction belongs to. |
| **company**                | *UUIDv4*                | The company id                                               |
| **datasource**             | *string*                |                                                              |
| **connection_id**          | *UUIDv4*                | This is the connection_id which was used to retrieve the origin data. |
| **object_class**           | `organisation`          | This is used to retrieve a specific type of data schema:     |
| **object_category**        | `bookkeeping`           | This is used to categorise the document.                     |
| **object_type**            | `company-details`       | This is the associated time dimension of the metric.         |
| **object_origin_category** | `bookkeeping`           | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
| **object_origin_type**     | `accounting`            | This is the specific type of origin related to the origin category |
| **object_origin**          | *string*                | This is the name of the application which matches the app-key in the connection records. |
| **object_creation_date**   | *date*                  | Creation time of document                                    |
| **data**                   | Organisation Object     | The actual organisation data, see below                  |

Below is the content of the `data` object used with `organisation`.

| Field                      | Data Type        | Description                                                  |
| :------------------------- | :--------------- | :----------------------------------------------------------- |
| **sales_tax_period**         | *string*         | Sales Tax Period                                             |
| **subscription_start**       | *string*         | Subscription state date                                      |
| **accounting_method**        | *string*         | Accounting method                                            |
| **base_currency**            | *string[3]*      | Currency                                                     |
| **business_type**            | *string*         | Business type                                                |
| **account_currency**         | *string[3]*      | Currency of the account                                      |
| **business_identifier**      | *string*         | Business number                                              |
| **organisation_type**        | *string*         | Organisation type                                            |
| **short_code**               | *string*         | Short code                                                   |
| **trading_name**             | *string*         | Trading name                                                 |
| **country_code**             | *string[2]*      | Country code                                                 |
| **fyear_end_month**          | *number*         | Financial year end month                                     |
| **fyear_end_day**            | *number*         | Financial year end day of the month                          |
