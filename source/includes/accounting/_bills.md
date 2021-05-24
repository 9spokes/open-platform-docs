## Bills

Following is the data specification for a bill that is extracted from accounting/POS OSPs

```json
{
    "connection_id" : "52684382-abff-45fa-a3f2-ced175adfe61",
    "company" : "69894a02-9c03-40ac-a06a-ee6e4b38c6fb",
    "datasource" : "bills",
    "osp" : "myob-accountright",
    "type" : "bill",
    "updated" : "2021-01-25T03:14:36Z",
    "cycle" : "day",
    "currency" : "NZD",
    "data" : [ 
        {
            "transaction_outstanding_amount" : 1026.13,
            "currency_rate" : 0.589596,
            "transaction_date" : "2021-01-22T00:00:00.000Z",
            "transaction_due_date" : "2021-02-20T12:00:00.000Z",
            "transaction_status" : "UNPAID",
            "transaction_reference" : "00001482",
            "related_reference" : "6df6db72-77d6-4505-8fb6-b4594e057855",
            "party_identifier" : "806ecb77-eece-47ac-9dd5-6a1f208681c7",
            "transaction_currency" : "NZD",
            "transaction_gross_value" : 1026.13,
            "transaction_net_value" : 1026.13,
            "line_items" : [ 
                {
                    "product_name" : "Plate",
                    "system_id" : "e54a0375-a275-4224-b71b-71afacae7213",
                    "item_identifier" : "N/A",
                    "item_category" : "N/A",
                    "item_type" : "N/A",
                    "item_net_unit_sale_value" : 1017.645981,
                    "item_net_unit_discount_value" : 1017.645981,
                    "item_unit_tax_value" : 1017.645981,
                    "item_price_list_reference" : "N/A",
                    "item_total_gross_value" : 1017.65,
                    "item_total_net_value" : 1017.65,
                    "item_total_tax_value" : 1017.65
                }, 
                {
                    "product_name" : "Packaging",
                    "system_id" : "e1924f89-55db-475c-bd50-ed0873b6d047",
                    "item_identifier" : "N/A",
                    "item_category" : "N/A",
                    "item_type" : "N/A",
                    "item_net_unit_sale_value" : 8.480383,
                    "item_net_unit_discount_value" : 8.480383,
                    "item_unit_tax_value" : 8.480383,
                    "item_price_list_reference" : "N/A",
                    "item_total_gross_value" : 8.48,
                    "item_total_net_value" : 8.48,
                    "item_total_tax_value" : 8.48
                }
            ]
        }
    ]
}
```

### Metadata

| Field             | Data Type        | Description                                         |
| :---------------- | ---------------- | --------------------------------------------------- |
| **company**       | *UUIDv4*         | The ID of the company owning the connection         |
| **connection_id** | *UUIDv4*         | The ID of the connection                            |
| **datasource**    | `bills`          | Always `bills` for bills                            |
| **osp**           | *string*         | The name of the app provider                        |
| **updated**       | *date*           | The time and date when this record was last updated |
| **cycle**         | `day` or `month` | Whether this data is pulled daily or monthly        |
| **currency**      | *string*         | The ISO4217 code for the currency for this bill     |
| **data**          | *Bill[]*         | An array of bills as defined below                  |

### Bill

| Field                              | Data Type    | Description                                                                          |
| :--------------------------------- | ------------ | ------------------------------------------------------------------------------------ |
| **transaction_outstanding_amount** | *number*     | Total outstanding bill amount                                                        |
| **currency_rate**                  | *number*     | Currency rate between the currency of the bill and the base currency of the business |
| **transaction_date**               | *date*       | Date on which the bill was issued                                                    |
| **transaction_due_date**           | *date*       | Date on which the bill is due                                                        |
| **transaction_status**             | *string*     | Status of the bill (Paid, Unpaid)                                                    |
| **transaction_reference**          | *string*     | Unique identifier of the bill on OSP's end                                           |
| **related_reference**              |              |                                                                                      |
| **party_identifier**               |              |                                                                                      |
| **transaction_currency**           | *string*     | Currency in which the bill was issued                                                |
| **transaction_gross_value**        | *number*     | Total bill amount                                                                    |
| **transaction_net_value**          | *number*     | Bill sub-total                                                                       |
| **tax_amount**                     | *number*     | Total applied tax amount                                                             |
| **line_items**                     | *LineItem[]* | The line items for this bill                                                         |

### Line Item

| Field                            | Data Type | Description                                                               |
| :------------------------------- | --------- | ------------------------------------------------------------------------- |
| **product_name**                 | *string*  | This is the name of the item being sold which may be a product or service |
| **system_id**                    | *string*  | Unique identifier of the line item on 9 Spokes's end                      |
| **item_identifier**              |
| **item_category**                |
| **item_type**                    |
| **item_net_unit_sale_value**     |
| **item_net_unit_discount_value** |
| **item_unit_tax_value**          |
| **item_price_list_reference**    |
| **item_total_gross_value**       |
| **item_total_net_value**         |
| **item_total_tax_value**         |
