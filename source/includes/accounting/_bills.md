## Bills

This is the specification for the bills of a user. 

```

> Below is a sample document

```json
{
    "bills_data" : {
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

### Below is the content of the `data` object used with `purchase-transaction`.

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

### Below is the content of the `line_items` object used with `purchase-transaction`.

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
