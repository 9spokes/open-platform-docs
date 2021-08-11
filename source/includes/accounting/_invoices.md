## Invoices

Following is the data specification for a invoice that is extracted from accounting/POS OSPs

> Retrieving the list of invoices for a connection is done by querying the `invoices` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/invoices \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of invoices as seen below.

```json
{
  "results": [
    {
      "data": {
        "currency_rate": 1.0,
        "transaction_gross_value": 17765.0,
        "transaction_net_value": 17000.0,
        "transaction_tax_value": 765.0,
        "transaction_date": "2021-04-05T00:00:00.000Z",
        "transaction_due_date": "2021-05-05T00:00:00.000Z",
        "transaction_reference": "070",
        "transaction_currency": "NZD",
        "transaction_status": "PAID",
        "line_items": [
          {
            "product_name": "Samsung Galaxy S6 10.5* Tab",
            "item_category": "revenue-transaction",
            "item_type": "invoice",
            "item_quantity": 10,
            "item_identifier": "Samsung Galaxy S6 10.5* Tab",
            "item_net_unit_sale_value": 1700.0,
            "item_total_net_value": 16235.0,
            "item_total_tax_value": 765.0,
            "item_total_gross_value": 17000.0,
            "system_id": "132516"
          }
        ]
      }
    },
    ...
  ]

}

```

<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/data/invoices</code>

The `invoices` endpoint for a connection returns an array of invoices. The `data` is the key for an invoice.

Individual line items can be found for each invoice under the `line_items` key.
### Invoice

| Field                              | Data Type    | Description                                                                             |
| :--------------------------------- | ------------ | --------------------------------------------------------------------------------------- |
| **transaction_outstanding_amount** | *number*     | Total outstanding invoice amount                                                        |
| **currency_rate**                  | *number*     | Currency rate between the currency of the invoice and the base currency of the business |
| **transaction_date**               | *date*       | Date on which the invoice was issued                                                    |
| **transaction_due_date**           | *date*       | Date on which the invoice is due                                                        |
| **transaction_status**             | *string*     | Status of the invoice (Paid, Unpaid)                                                    |
| **transaction_reference**          | *string*     | Unique identifier of the invoice on OSP's end                                           |
| **transaction_currency**           | *string*     | Currency in which the invoice was issued                                                |
| **transaction_gross_value**        | *number*     | Total invoice amount                                                                    |
| **transaction_net_value**          | *number*     | invoice subtotal                                                                        |
| **line_items**                     | *LineItem[]* | An array of line items as defined below                                                 |

### Line Item

| Field                            | Data Type | Description                                                               |
| :------------------------------- | --------- | ------------------------------------------------------------------------- |
| **product_name**                 | *string*  | Name of the product or service being sold
| **system_id**                    | *string*  | Unique identifier of the line item on 9Spokes' end                      |
| **item_identifier**              | *string*  | Unique identifier of the line item on the app's end                           |
| **item_category**                | *string*  | Account category under which the transaction item was originally listed |
| **item_type**                    | *string*  | 'invoice' when the osp is an accouting app and 'good-service' when the osp is a point of sale app |
| **item_net_unit_sale_value**     | *number*  | Net sale value per item |
| **item_net_unit_discount_value** | *number*  | Net discount value per item |
| **item_unit_tax_value**          | *number*  | Tax value per item |
| **item_price_list_reference**    | *string*  | Reference to any pre-set discounting based upon specific price lists (specials, happy hour, etc.) |
| **item_total_gross_value**       | *number*  | Total gross value of the item (before tax) |
| **item_total_net_value**         | *number*  | Net value of the item (after tax) |
| **item_total_tax_value**         | *number*  | Total tax value applied to the item | 
