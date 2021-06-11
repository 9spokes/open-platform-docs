## Tax Rates

Following is the data specification of tax rates as extracted from accounting/POS OSPs

> Retrieving the list of tax types and corresponding rates for a connection is done by querying the `taxRates` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/taxRates \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of tax rates as seen below.

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

<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/taxRates</code>

The `taxRates` endpoint for a connection returns an array of tax rates.  Each record contains a *metadata* envelope and a `data` key.  The `data` key for taxRates is always an array of taxRates.

### Metadata

| Field                      | Data Type                 | Description                                                                                                  |
| :------------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **user**                   | *uuid*                    | User's ID of the company that the transaction belongs to.                                       |
| **company**                | *uuid*                    | The company ID                                                                                               |
| **datasource**             | *string*                  | `tax-rates`                                        |
| **connection_id**          | *uuid*                    | ID used to retrieve the origin data                                        |
| **object_class**           | `rates`                   | Retrieves a specific type of data schema                                                     |
| **object_category**        | `general-ledger`          | Used to categorize the document                                                                     |
| **object_type**            | `day` or `month`          | Associated time element of the metric                                                         |
| **object_origin_category** | `bookkeeping`             | The 9Spokes categorization of data origin business applications (and other data producing services) |
| **object_origin_type**     | `accounting`              | Specific type of origin related to the origin category                                           |
| **object_origin**          | *string*                  | Name of the application which matches the app-key in the connection records                     |
| **object_creation_date**   | *date*                    | Creation time of document                                                                                    |
| **data**                   | Tax Rate Array of objects | The actual timeline balance data (see below)                                                                  |

### Data

Below is the content of the `data` object used with `tax-rates`.

| Field        | Data Type | Description          |
| :----------- | --------- | -------------------- |
| **tax_id**   | *string*  | Tax ID               |
| **tax_name** | *string*  | Tax name             |
| **tax_rate** | *number*  | The value of the tax |
