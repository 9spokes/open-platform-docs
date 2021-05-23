## Stock Items

This is the specification for the Stock Items. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

### Field Description

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
  "object_creation_date": "Date",
  "data": [
    {
      "item_id": "string",
      "item_name": "string",
      "active": "boolean",
      "item_quantity": "number",
      "item_cost_price": "number",
      "item_sale_price": "number",
      "item_sale_price_includes_tax": "boolean",
      "tax_rate_id": "string",
    }
  ]
}
```

```json
{
  "user": "887cee1a-5d59-4509-ab7b-0f40a73fed69",
  "company": "7af2b057-0ac5-4818-9d50-0c48006985d5",
  "datasource": "stock_items",
  "connection_id": "f4592653-7c08-4722-8920-c280c95991d7",
  "object_class": "items",
  "object_category": "stock",
  "object_type": "stock-items",
  "object_origin_category": "point-of-sale",
  "object_origin_type": "online",
  "object_origin": "shopify",
  "object_creation_date": "2020-11-19 11:00:01.096Z",
  "data": [
    {
      "item_id": "5287889d-c45b-4a65-9ef6-68494d4fdeb0",
      "item_name": "Dining Chair",
      "active": true,
      "item_quantity": 3,
      "item_cost_price": 100,
      "item_sale_price": 280,
      "item_sale_price_includes_tax": false,
      "tax_rate_id": "GST",
    }
  ]
}
```

Below is the metadata wrapper used to classify and search stock items data. The stock items data is stored under the `data` key.

| Field                    | Data Type        | Description                                                  |
| :----------------------- | :--------------- | :----------------------------------------------------------- |
| **user**                   | *UUIDv4*         | This is the user's id of the company that this transaction belongs to. |
| **company**                | *UUIDv4*         | The company id                                               |
| **datasource**             | *string*         | The datasource name                                          |
| **connection_id**          | *UUIDv4*         | This is the connection_id which was used to retrieve the origin data. |
| **object_class**           | *string*         | This is used to retrieve a specific type of data schema:     |
| **object_category**        | *string*         | This is used to categorise the document.                     |
| **object_type**            | *string*         | This is the associated time dimension of the metric.         |
| **object_origin_category** | *string*         | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
| **object_origin_type**     | *string*         | This is the specific type of origin related to the origin category |
| **object_origin**          | *string*         | This is the name of the application which matches the app-key in the connection records. |
| **object_creation_date**   | *date*           | Creation time of document                                    |
| **data**                   | Array of stock item objects | The actual product data, see below                           |

Below is the content of the `data` object used with `stock items`.

| Field                          | Data Type | Description                                         |
| :----------------------------- | :-------- | :-------------------------------------------------- |
| **item_id**                      | *string*  | The specific stock item id related to the product   |
| **item_name**                    | *string*  | The specific stock item name related to the product |
| **active**                       | *boolean* | The item has stock values                           |
| **item_quantity**                | *number*  | The units of stock items available for sale         |
| **item_cost_price**              | *number*  | The unit cost of the stock item                     |
| **item_sale_price_includes_tax** | *boolean* | The item sale price includes tax                    |
| **tax_rate_id**                  | *string*  | The specific tax rate id related to the stock item  |