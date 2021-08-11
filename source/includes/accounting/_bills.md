## Bills

Following is the data specification for a bill that is extracted from accounting/POS OSPs

> Retrieving the list of bills for a connection is done by querying the `bills` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/bills \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of bills as seen below.

```json
{
  "results": [
    {
      "data": {
        "transaction_outstanding_amount": 1026.13,
        "currency_rate": 0.589596,
        "transaction_date": "2021-01-22T00:00:00.000Z",
        "transaction_due_date": "2021-02-20T12:00:00.000Z",
        "transaction_status": "UNPAID",
        "transaction_reference": "00001482",
        "related_reference": "6df6db72-77d6-4505-8fb6-b4594e057855",
        "party_identifier": "806ecb77-eece-47ac-9dd5-6a1f208681c7",
        "transaction_currency": "NZD",
        "transaction_gross_value": 1026.13,
        "transaction_net_value": 1026.13,
        "line_items": [
          {
            "product_name": "Plate",
            "system_id": "e54a0375-a275-4224-b71b-71afacae7213",
            "item_identifier": "N/A",
            "item_category": "N/A",
            "item_type": "N/A",
            "item_net_unit_sale_value": 1017.645981,
            "item_net_unit_discount_value": 1017.645981,
            "item_unit_tax_value": 1017.645981,
            "item_price_list_reference": "N/A",
            "item_total_gross_value": 1017.65,
            "item_total_net_value": 1017.65,
            "item_total_tax_value": 1017.65
          },
          {
            "product_name": "Packaging",
            "system_id": "e1924f89-55db-475c-bd50-ed0873b6d047",
            "item_identifier": "N/A",
            "item_category": "N/A",
            "item_type": "N/A",
            "item_net_unit_sale_value": 8.480383,
            "item_net_unit_discount_value": 8.480383,
            "item_unit_tax_value": 8.480383,
            "item_price_list_reference": "N/A",
            "item_total_gross_value": 8.48,
            "item_total_net_value": 8.48,
            "item_total_tax_value": 8.48
          }
        ]
      },
      ...
    }
  ]
}


```

<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/data/bills</code>

The `bills` endpoint for a connection returns an array of bills. The `data` is the key for a bill.

Individual line items can be found for each bill under the `line_items` key.
### Bill

| Field                              | Data Type    | Description                                                                          |
| :--------------------------------- | ------------ | ------------------------------------------------------------------------------------ |
| **transaction_outstanding_amount** | *number*     | Total outstanding bill amount                                                        |
| **currency_rate**                  | *number*     | Currency rate between the currency of the bill and the base currency of the business |
| **transaction_date**               | *date*       | Date on which the bill was issued                                                    |
| **transaction_due_date**           | *date*       | Date on which the bill is due                                                        |
| **transaction_status**             | *string*     | Status of the bill (Paid, Unpaid)                                                    |
| **transaction_reference**          | *string*     | Unique identifier of the bill on OSP's end                                           |
| **related_reference**              | *string*     | Unique reference related to the transaction                                          |
| **party_identifier**               | *string*     | Unique identifier for the third party                                                |
| **transaction_currency**           | *string*     | Currency in which the bill was issued                                                |
| **transaction_gross_value**        | *number*     | Total bill amount                                                                    |
| **transaction_net_value**          | *number*     | Bill subtotal                                                                       |
| **tax_amount**                     | *number*     | Total applied tax amount                                                             |
| **line_items**                     | *LineItem[]* | An array of line items as defined below                                              |

### Line Item

| Field                            | Data Type | Description                                                                                       |
| :------------------------------- | --------- | ------------------------------------------------------------------------------------------------- |
| **product_name**                 | *string*  | Name of the product or service being sold                         |
| **system_id**                    | *string*  | Unique identifier of the line item on 9Spokes' end                                              |
| **item_identifier**              | *string*  | Unique identifier of the line item on the app's end                                                   |
| **item_category**                | *string*  | Account category under which the transaction item was originally listed                           |
| **item_type**                    | *string*  | 'bill' when the osp is an accouting app and 'good-service' when the osp is a point of sale app    |
| **item_net_unit_sale_value**     | *number*  | Net sale value per item                                                                           |
| **item_net_unit_discount_value** | *number*  | Net discount value per item                                                                       |
| **item_unit_tax_value**          | *number*  | Tax value per item                                                                                |
| **item_price_list_reference**    | *string*  | Reference to any pre-set discounting based upon specific price lists (specials, happy hour, etc.) |
| **item_total_gross_value**       | *number*  | Total gross value of the item (before tax)                                                        |
| **item_total_net_value**         | *number*  | Net value of the item (after tax)                                                                 |
| **item_total_tax_value**         | *number*  | Total tax value applied to the item                                                               |
