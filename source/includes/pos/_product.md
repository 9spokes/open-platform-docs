## Product

This is the specification for the Product Items. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

### Field Description

```json
{
  "user": "887cee1a-5d59-4509-ab7b-0f40a73fed69",
  "company": "7af2b057-0ac5-4818-9d50-0c48006985d5",
  "datasource": "products",
  "connection_id": "f4592653-7c08-4722-8920-c280c95991d7",
  "object_class": "items",
  "object_category": "product",
  "object_type": "product-details",
  "object_origin_category": "point-of-sale",
  "object_origin_type": "online",
  "object_origin": "shopify",
  "object_creation_date": "2020-11-19 11:00:01.096Z",
  "data": {
      "product_name": "Dining Chair",
      "product_id": "5287889d-c45b-4a65-9ef6-68494d4fdeb0",
      "product_group": "Furniture",
      "product_variant":[ 
            "white","black"
        ],
      "product_handle":"dining-chair", 
      "product_sku": "142350",
      "created_at": "2018-11-04T21:24:23.873Z",
      "updated_at": "2020-11-03T21:24:23.906Z",
      "deleted_at": null,
      "product_cost": 100,
      "product_net_price": 280,
      "product_gross_price":300,
      "inventory_product":true,
      "inventory_product_quantity":3,
      "product_cost_value": 300,
      "product_sale_value": 840     
    }  
}
```

Below is the metadata wrapper used to classify and search product data. The product data is stored under the `data` key.

| Field                      | Data Type      | Description                                                                                                  |
| :------------------------- | :------------- | :----------------------------------------------------------------------------------------------------------- |
| **user**                   | *uuid*         | This is the user's id of the company that this transaction belongs to.                                       |
| **company**                | *uuid*         | The company id                                                                                               |
| **datasource**             | *string*       | The datasource name                                                                                          |
| **connection_id**          | *uuid*         | This is the connection_id which was used to retrieve the origin data.                                        |
| **object_class**           | *string*       | This is used to retrieve a specific type of data schema:                                                     |
| **object_category**        | *string*       | This is used to categorise the document.                                                                     |
| **object_type**            | *string*       | This is the associated time dimension of the metric.                                                         |
| **object_origin_category** | *string*       | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
| **object_origin_type**     | *string*       | This is the specific type of origin related to the origin category                                           |
| **object_origin**          | *string*       | This is the name of the application which matches the app-key in the connection records.                     |
| **object_creation_date**   | *date*         | Creation time of document                                                                                    |
| **data**                   | Product Object | The actual product data, see below                                                                           |

Below is the content of the `data` object used with `product`.

| Field                          | Data Type           | Description                                                        |
| :----------------------------- | :------------------ | :----------------------------------------------------------------- |
| **product_name**               | *string*            | The specific product name retrieved                                |
| **product_id**                 | *string*            | The specific product id related to the product                     |
| **product_group**              | *string*            | The specific product group related to the product                  |
| **product_variant**            | *string[]*          | The specific product variant related to the product                |
| **product_handle**             | *string*            | The specific product handle related to the product                 |
| **product_sku**                | *string*            | The specific product sku related to the product                    |
| **created_at**                 | `debit` or `credit` | Debit/Credit                                                       |
| **updated_at**                 | *number*            | The value of the account                                           |
| **deleted_at**                 | *number*            | The value of the account                                           |
| **product_cost**               | *number*            | The unit cost of the product                                       |
| **product_net_price**          | *number*            | The unit net price of the product                                  |
| **product_gross_price**        | *number*            | The unit gross price of the product                                |
| **inventory_product**          | *boolean*           | The Product has stock values and inventory is tracked              |
| **inventory_product_quantity** | *number*            | The units of product available for sale                            |
| **product_cost_value**         | *number*            | The total cost value of the product (product cost x quantity)      |
| **product_sale_value**         | *number*            | The total sale value of the product (product net price x quantity) |
