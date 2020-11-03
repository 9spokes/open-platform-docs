## Goods and Services Transaction

This is the specification for the goods & service transaction. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

### Field Description

> Below is the schema definition for a `goods-services-transaction` record

```json
{
    "user": ,
    "connection_id": ,
    "object_class": ,
    "object_category": ,
    "object_type": ,
    "object_origin_category": ,
    "object_origin_type": ,
    "object_origin": ,
    "object_creation_date": ,
    "data": {
        "transaction_date": ,
        "transaction_due_date": ,
        "transaction_status": ,
        "transaction_reference": ,
        "transaction_currency": ,
        "transaction_gross_value": ,
        "related_reference": ,
        "party_identifier": ,
        "business_identifier": ,
        "transaction_net_value": ,
        "transaction_tax_value": ,
        "transaction_cost_value": ,
        "line_items": [
            {
                "item_name": ,
                "system_id": ,
                "item_identifier": ,
                "item_category": ,
                "item_type": ,
                "item_quantity": ,
                "item_net_unit_sale_value": ,
                "item_net_unit_discount_value": ,
                "item_unit_tax_value": ,
                "item_price_list_reference": ,
                "item_total_gross_value": ,
                "item_total_net_value": ,
                "item_net_unit_cost_value": ,
                "line_items_total_tax_value": ,
            }
        ],
        // NOTE: "shipping_line_items" is Shopify only. Other OSPs will display every nested field as NULL
        "shipping_line_items": [
            {
                "system_id": ,
                "item_identifier": ,
                "item_category": ,
                "item_type": ,
                "item_quantity": ,
                "item_net_unit_sale_value": ,
                "item_net_unit_discount_value": ,
                "item_unit_tax_value": ,
                "item_price_list_reference": ,
                "item_total_gross_value": ,
                "item_total_net_value": ,
                "item_total_tax_value": ,
                "item_shipping_price": ,
                "item_shipping_tax_price": ,
            }
        ]
    }
}
```

> This is the example format of the JSON object in the 9Spokes format for goods and services transaction.

| 9Spokes Format  | Type | Values                      | Explanation                                                             |
| --------------- | ---- | --------------------------- | ----------------------------------------------------------------------- |
| user            |      | as per connection           | This is the party_uuid of the company that this transaction belongs to. |
| connection_id   |      | as per connection           | This is the connection_uuid which was used to retrieve the origin data. |
| object_class    |      | "goods-service-transaction" | This is used to retrieve a specific type of data schema:                |
| object_category |      | "revenue-transaction"       | This is used to categorise the document.                                |
| object_type     |      | For accounts:               |

- "account-identifier"
  For revenue-transactions:
- "invoice"
- "receipt"
- "refund"
  For order-transactions:
- "customer"
- "supplier"
  For expense-transactions:
- "bill"
- "receipt"
- "refund"
  For payment-transactions:
- "credit"
- "debit" | This is used to add further clarity to the type of document it is. |
  | object_origin_category | | - "bookkeeping"
- "point-of-sale"
- "inventory"
- "staff-management"
- "bookings"
- "customer-management" | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
  | object_origin_type | | bookkeeping
- "accounting"
- "payroll"
  point-of-sale
- "online"
- "offline"
  inventory
- "stock-item"
- "time-service"
  staff-management
- "time-assignment"
- "time-record"
  bookings
- "appointment"
- "booking" | This is the specific type of origin related to the origin category |
  | object_origin | | as per connection | This is the name of the application which matches the app-key in the connection records. |
  | object_creation_date | UTC-date-time | | This is the timestamp of when this document is created on our system by us. This is used to identify any documents which are not yet processed into metrics since the last time the data aggregation services ran. |
  | data | as object | | |
  | currency_rate | | | This is the currency rate to convert the transaction values from the transaction currency to the base currency.
  Note: This field only applies to invoices, bills, and payments. |
  | transaction_paid_date | | | This is the date when the invoice was fully paid.
  Note: This field only applies to invoices, and bills. |
  | transaction_outstanding_amount | | | This is the amount outstanding of the invoice to be paid after partial payments.
  Note: This field only applies to invoices. |
  | transaction_date | | | This is the local date and time of when the transaction occurred (not UTC) and formatted as YYYYMMDDHHMMSS. |
  | transaction_due_date | | | This is the due date of the invoice |
  | transaction_status | | revenue-transaction
- "UNPAID"
- "PAID"
- "VOIDED"
  expense-transaction
- "UNPAID"
- "PAID"
- "VOIDED"
  order-transaction
- "CREATED"
- "PROCESSED"
- "COMPLETED"
- "CANCELLED"
  fulfillment-transaction
- "PENDING"
- "FULFILLED"
- "RETURNED"
  payment-transaction
- "PROCESSED"
- "CONFIRMED" | This is the standardised status of a transaction which is different by type. |
  | transaction_reference | | | This is the internally generated reference like order number or invoice number. |
  | related_reference | | | This is where a transaction is related to another one using an internally generated reference. Example: a order-transaction.transaction_reference may be used as a revenue-transaction.related_reference if the invoice/bill is against an order. |
  | party_identifier | | | This is the origin system identifier for the party that this transaction is to or from. This relates to the party table for identifiable information. |
  | transaction_currency | | | This is the transaction currency like GBP, USD, NZD, AUD, etc. |
  | transaction_gross_value | | | This is the total value of the transaction including any taxes (gross value) in the transaction_currency. |
  | transaction_net_value | | | This is the total value of the transaction excluding any taxes (net value) in the transaction_currency. |
  | transaction_tax_value | | | This is the total value of tax applied to the entire transaction. |
  | transaction_cost_value | | | Where this transaction is a sale and has come from a system which includes cost values, these are attributed here as a total net value. |
  | line_items | as Array | | This is a list of items/products related to this document. Each element of the array is an object with the following fields |
  | line_items.item_name | | | This is the name of the item being sold which may be a product or service. |
  | line_items.system_id | | | This is the origin system identifier relating to the item which may be a product or service in another data set (inventory or services). |
  | line_items.item_identifier | | | This is the publicly available SKU or barcode reference which can be looked up on external systems or has been created by the business where the product is made in-house. |
  | line_items.item_category | | - "sales-revenue"
- "other-revenue"
- "sales-expense"
- "other-expense" | This category is which account the transacted item attributed to. For Bookkeeping, it could be any one of the accounts used in the general ledger and has the 9 Spokes standardised categories of a business' accounts to apply.
  Where the transaction has come from a POS (point-of-sale) system and is a revenue-transaction (sale or refund), this is set to sales-revenue. |
  | line_items.item_type | | - "goods-service"
- "fulfilment" | This is the type of item being listed as a part of the transaction. It is either one of the options below:
  The item_type is used to identify what a business does and can isolate/omit services which were used to facilitate the fulfilment. Example: If you are an online business selling physical products and every order required local or international delivery, you would not appreciate having "Delivery" as one of your top selling products when it was simply a mechanism required to get the goods to the customer irrespective of whether that service was chargeable or not to the customer. For more info on this, refer to the TmForums OPSR model definitions (Offer, Product, Services and Resources). |
  | line_items.item_quantity | | | This is the number of items (products) or units of hours (time based services) transacted. |
  | line_items.item_net_unit_sale_value | | | |
  | line_items.item_net_unit_discount_value | | | This is the value of the item discount per unit without any taxes applied. |
  | line_items.item_unit_tax_value | | | This is the value of the tax per unit of the item. |
  | line_items.item_price_list_reference | | | This is the reference to any pre-set discounting based upon specific price lists (specials, happy hour, etc.) |
  | line_items.item_total_gross_value | | | |
  | line_items.item_total_net_value | | | This is the total tax applied to the line_item of this transaction. |
  | line_items.item_net_unit_cost_value | | | This is the net value of any cost value which is supplied from the transaction if available. |
  | line_items_total_tax_value | | | This is the total tax applied to the line_item of this transaction. |
  | shipping_line_items | as array | NOTE: This is Shopify only. Other OSPs will display as NULL or "NOT DISPLAYED" | This is a list of items/products related to this document. Each element of the array is an object with the following fields |
  | shipping_line_items.system_id | | | |
  | shipping_line_items.item_identifier | | | |
  | shipping_line_items.item_category | | | |
  | shipping_line_items.item_type | | | |
  | shipping_line_items.item_quantity | | | |
  | shipping_line_items.item_net_unit_sale_value | | | |
  | shipping_line_items.item_net_unit_discount_value | | | |
  | shipping_line_items.item_unit_tax_value | | | |
  | shipping_line_items.item_price_list_reference | | | |
  | shipping_line_items.item_total_gross_value | | | |
  | shipping_line_items.item_total_net_value | | | |
  | shipping_line_items.item_total_tax_value | | | |
  | shipping_line_items.item_shipping_price | | | |
  | shipping_line_items.item_shipping_tax_price | | | |
