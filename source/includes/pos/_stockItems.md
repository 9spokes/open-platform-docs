## Stock Items

This is the specification for Stock Items. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform. Following is the data specification for stock items as extracted from POS OSPs

> Retrieving the stock items data for a connection is done by querying the `stockItems` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/stockItems \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of stock items data as seen below.

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
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/stockItems</code>

### Metadata

Below is the metadata wrapper used to classify and search stock items data. The stock items data is stored under the `data` key.

| Field                      | Data Type                   | Description                                                                                                  |
| :------------------------- | :-------------------------- | :----------------------------------------------------------------------------------------------------------- |
| **user**                   | *uuid*                      | User's ID of the company that this transaction belongs to                                      |
| **company**                | *uuid*                      | The company ID                                                                                              |
| **datasource**             | *string*                    | The datasource name                                                                                          |
| **connection_id**          | *uuid*                      | ID used to retrieve the origin data                                        |
| **object_class**           | *string*                    | Retrieves a specific type of data schema                                                     |
| **object_category**        | *string*                    | Used to categorise the document                                                                     |
| **object_type**            | *string*                    | Associated time element of the metric                                                         |
| **object_origin_category** | *string*                    | The 9Spokes categorization of data origin business applications (and other data producing services) |
| **object_origin_type**     | *string*                    | Specific origin type related to the origin category                                           |
| **object_origin**          | *string*                    | Name of the application which matches the app-key in the connection records                     |
| **object_creation_date**   | *date*                      | Creation time of document                                                                                    |
| **data**                   | Array of stock item objects | The actual product data (see below)                                                                           |

### Data

Below is the content of the `data` object used with `stock items`.

| Field                            | Data Type | Description                                         |
| :------------------------------- | :-------- | :-------------------------------------------------- |
| **item_id**                      | *string*  | Specific item ID of the product   |
| **item_name**                    | *string*  | The specific stock item name related to the product |
| **active**                       | *boolean* | The item has stock values                           |
| **item_quantity**                | *number*  | The units of stock items available for sale         |
| **item_cost_price**              | *number*  | The unit cost of the stock item                     |
| **item_sale_price_includes_tax** | *boolean* | The item sale price includes tax                    |
| **tax_rate_id**                  | *string*  | The tax rate ID of the stock item  |