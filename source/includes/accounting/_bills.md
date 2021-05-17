## Bills

Following is the data specification for a bill that is extracted from accounting/POS OSPs

````

> Below is a sample document

```json
{
    "company": "string",
    "app": "string",
    "bill": {
        "id": "f4b7eae03391457882f4d20610b0b2df",
        "reference": "a4b7eae03391457882f4d20610b0b2dt",
        "status": "Unpaid",
        "currency": "NZD",
        "currency_rate": "1",
        "transaction_date": "2021-05-12T00:00:00.000Z",
        "issue_date": "2021-05-12T00:00:00.000Z",
        "due_date": "2021-05-15T00:00:00.000Z",
        "tax_amount": "20.0",
        "cost_amount": "100.0",
        "discount_amount": "5.0",
		"sub_total_amount": "125.0",
        "total_amount": "125.0",
        "outstanding_amount": "125.0",
        "line_items": [
            {
                "id": "b4b7eae03391457882f4d20610b0b2dg",
                "reference": "d4b7eae03391457882f4d20610b0b2dp",
                "name": "Keyboard - Standard",
                "quantity": "10",
                "tax_amount": "2.0",
                "cost_amount": "10.0",
                "discount_amount": "0.5",
                "total_amount": "11.5",
                "sub_total_amount": "11.5"
            }
        ]
    }
}

````

### Data Schema

| Field                         | Data Type | Description                                                                               |
| :---------------------------- | --------- | ----------------------------------------------------------------------------------------- |
| `company`                     | `string`  | Business/Company name                                                                     |
| `app`                         | `string`  | OSP from which the bill data is extracted                                                 |
| `bill.id`                     | `string`  | Unique identifier of the bill on 9Spokes's end                                            |
| `bill.reference`              | `string`  | Unique identifier of the bill on OSP's end                                                |
| `bill.status`                 | `string`  | Status of the bill (Paid, Unpaid)                                                         |
| `bill.currency`               | `string`  | Currency in which the bill was issued                                                     |
| `bill.currency_rate`          | `number`  | Currency rate between the currency of the bill and the base currency of the business      |
| `bill.transaction_date`       | `date`    | Date on which the transaction occured                                                     |
| `bill.issue_date`             | `date`    | Date on which the bill was issued                                                         |
| `bill.due_date`               | `date`    | Date on which the bill is due                                                             |
| `bill.tax_amount`             | `number`  | Total applied tax amount                                                                  |
| `bill.cost_amount`            | `number`  | Total cost of all items in the bill                                                       |
| `bill.discount_amount`        | `number`  | Total applied discount amount                                                             |
| `bill.sub_total_amount`       | `number`  | Bill sub-total                                                                            |
| `bill.total_amount`           | `number`  | Total bill amount                                                                         |
| `bill.outstanding_amount`     | `number`  | Total outstanding bill amount                                                             |
| `line_items.id`               | `string`  | Unique identifier of the line item on 9 Spokes's end                                      |
| `line_items.reference`        | `string`  | Unique identifier of the line item on OSP's end                                           |
| `line_items.name`             | `string`  | This is the name of the item being sold which may be a product or service                 |
| `line_items.quantity`         | `string`  | This is the number of items (products) or units of hours (time based services) transacted |
| `line_items.tax_amount`       | `string`  | Tax applied to the line item of the transaction.                                          |
| `line_items.cost_amount`      | `string`  | Cost of the line item of the transaction                                                  |
| `line_items.discount_amount`  | `string`  | Value of the item discount per unit without any taxes applied                             |
| `line_items.sub_total_amount` | `string`  | Line item sub-total                                                                       |
| `line_items.total_amount`     | `string`  | Total value of the line item of the transaction                                           |
