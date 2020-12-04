## Bills

This is the specification for thebillss of a user. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

### Field Description

> Below is the schema definition for a `account-balance` record


```json
{
    "connection_id" : "string",
    "user" : "string",
    "company" : "string",
    "datasource" : "string",
    "osp" : "string",
    "type" : "string",
    "updated" : "string",
    "index" : "string",
    "cycle" : "string",
    "object_origin_category" : "string",
    "object_origin_type" : "string",
    "object_origin" : "string",
    "object_creation_date" : "string",
    "object_class" : "string",
    "object_type" : "string",
    "object_category" : "string",
    "currency" : "string",
    "data" : {
        "currency_rate" : "number",
        "transaction_paid_date" : "string",
        "transaction_outstanding_amount" : "number",
        "transaction_gross_value" : "number",
        "transaction_net_value" : "number",
        "transaction_tax_value" : "number",
        "transaction_date" : "string",
        "transaction_due_date" : "string",
        "transaction_reference" : "string",
        "transaction_currency" : "string[3]",
        "transaction_status" : "string",
        "line_items" : [
            {
                "product_name" : "string",
                "item_category" : "string",
                "item_type" : "string",
                "item_quantity" : "number",
                "item_identifier" : "string",
                "item_net_unit_sale_value" : "number",
                "item_price_list_reference" : "string",
                "item_total_net_value" : "number",
                "item_total_tax_value" : "number",
                "item_total_gross_value" : "number",
                "item_unit_tax_value" : "number",
                "system_id" : "string"
            }
        ]
    }
}
```

> Below is a sample document

```json
{
    "connection_id" : "f4592653-7c08-4722-8920-c280c95991d7",
    "user" : "08da4bfe-a8df-4729-82af-36726a18e746",
    "company" : "7af2b057-0ac5-4818-9d50-0c48006985d5",
    "datasource" : "purchases",
    "osp" : "sageone",
    "type" : "bill",
    "updated" : "2020-10-30T01:56:48Z",
    "index" : "47e112b2fa49e8219d2118ee3ef8bb2b",
    "cycle" : "day",
    "object_origin_category" : "bookkeeping",
    "object_origin_type" : "accounting",
    "object_origin" : "sageone",
    "object_creation_date" : "2020-10-30T01:56:48.195Z",
    "object_class" : "goods-service-transaction",
    "object_type" : "bill",
    "object_category" : "purchase-transaction",
    "currency" : "GBP",
    "data" : {
        "currency_rate" : 1.0,
        "transaction_paid_date" : "2020-10-12T00:00:00.000Z",
        "transaction_outstanding_amount" : 1806.0,
        "transaction_gross_value" : 1806.0,
        "transaction_net_value" : 1505.0,
        "transaction_tax_value" : 301.0,
        "transaction_date" : "2020-10-12T00:00:00.000Z",
        "transaction_due_date" : "2020-11-26T00:00:00.000Z",
        "transaction_reference" : "3244ce8f4ef348169f1934edbbddf754",
        "transaction_currency" : "GBP",
        "transaction_status" : "UNPAID",
        "line_items" : [
            {
                "product_name" : "Product 07 ",
                "item_category" : "8433007b7f7b11e691e20a5d7cf84c3e",
                "item_type" : "8433007b7f7b11e691e20a5d7cf84c3e",
                "item_quantity" : 200,
                "item_identifier" : "ebb80c3fd6854872a4a6811657a4ec73",
                "item_net_unit_sale_value" : 2.5,
                "item_total_net_value" : 500.0,
                "item_total_tax_value" : 100.0,
                "item_total_gross_value" : 600.0,
                "item_unit_tax_value" : 0.5,
                "system_id" : "f4b7eae03391457882f4d20610b0b2df"
            },
            {
                "product_name" : "Keyboard - Standard",
                "item_category" : "843326bf7f7b11e691e20a5d7cf84c3e",
                "item_type" : "843326bf7f7b11e691e20a5d7cf84c3e",
                "item_quantity" : 500,
                "item_identifier" : "73f21a60d8f14f09aa9b4a47a3903181",
                "item_net_unit_sale_value" : 2.01,
                "item_total_net_value" : 1005.0,
                "item_total_tax_value" : 201.0,
                "item_total_gross_value" : 1206.0,
                "item_unit_tax_value" : 0.402,
                "system_id" : "d7f7b46ad7de4871912b68bd8a337601"
            }
        ]
    }
}
```

Below is the metadata wrapper used to classify and search account balance data. The account balance data is stored under the `data` key.

| Field                    | Data Type               | Description                                                                                                  |
| :----------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------ |
| `user`                   | `UUIDv4`                | This is the user's id of the company that this transaction belongs to.                                       |
| `company`                | `UUIDv4`                | The company id                                                                                               |
| `datasource`             | `string`                |                                                                                                              |
| `connection_id`          | `UUIDv4`                | This is the connection_id which was used to retrieve the origin data.                                        |
| `object_class`           | `goods-service-transaction`       | This is used to retrieve a specific type of data schema:                                           |
| `object_category`        | `purchase-transaction`  | This is used to categorise the document.                                                                     |
| `object_type`            | `bill`                  | This is the associated time dimension of the metric.                                                         |
| `object_origin_category` | `bookkeeping`           | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
| `object_origin_type`     | `accounting`            | This is the specific type of origin related to the origin category                                           |
| `object_origin`          | `string`                | This is the name of the application which matches the app-key in the connection records.                     |
| `balance_date`           | `Date`                  | The account balance's date                                                                                   |
| `currency`               | `string[3]`             | Currency of data                                                                                             |
| `object_creation_date`   | `Date`                  | Creation time of document                                                                                    |
| `data`                   | Purchase Transaction Object | The actual timeline balance data, see below                                                              |

Below is the content of the `data` object used with `purchase-transaction`.

| Field                | Data Type              | Description                                                                                                 |
| :------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------|
| `currency_rate`      | `number`               | Currency rate |
| `transaction_paid_date`       | `date`               | Transation paid date  |
| `transaction_outstanding_amount`   | `number`            | Transaction outstanding amount |
| `transaction_gross_value`     | `number`              | Transaction gross value |
| `transaction_net_value`    | `number`               | Transaction net value |
| `transaction_date` | `date` | Transaction Date |
| `transaction_due_date` | `date` | Transaction due date |
| `transaction_reference` | `date` | Transaction reference |
| `transaction_currency` | `number` | Transaction currency |
| `transaction_status` | `string` | Transaction status e.g. PAID/UNPAID |
| `line_items` | `string` | Line items of the bills. See below |

Below is the content of the `line_items` object used with `purchase-transaction`.

| Field                | Data Type              | Description                                                                                                 |
| :------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------|
| `product_name`      | `string`               | Product Name |
| `item_category`       | `string`               | Product category reference  |
| `item_type`   | `string`            | Product type reference |
| `item_quantity`     | `number`              | Quantity |
| `item_identifier`    | `string`               | Item reference |
| `item_net_unit_sale_value` | `number` | Item net unit sale value |
| `item_total_net_value` | `number` | Item total net value |
| `item_total_tax_value` | `number` | Item total tax value |
| `item_total_gross_value` | `number` | Item total gross value |
| `item_unit_tax_value` | `number` | Item unit tax value |
| `system_id` | `string` | Item reference |
