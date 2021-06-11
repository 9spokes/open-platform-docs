## Product

This is the specification for Product Items. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform. Following is the data specification for products as extracted from POS OSPs

> Retrieving the products data for a connection is done by querying the `products` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/products \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of Product data as seen below.

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
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/products</code>

### Metadata

Below is the metadata wrapper used to classify and search product data. The product data is stored under the `data` key.

| Field                      | Data Type      | Description                                                                                                  |
| :------------------------- | :------------- | :----------------------------------------------------------------------------------------------------------- |
| **user**                   | *uuid*         | User's ID of the company that the transaction belongs to                                       |
| **company**                | *uuid*         | The company ID                                                                                               |
| **datasource**             | *string*       | The datasource name                                                                                          |
| **connection_id**          | *uuid*         | ID used to retrieve the origin data                                        |
| **object_class**           | *string*       | Retrieves a specific type of data schema                                                    |
| **object_category**        | *string*       | Used to categorize the document                                                                     |
| **object_type**            | *string*       | Associated time element of the metric                                                         |
| **object_origin_category** | *string*       | The 9Spokes categorization of data origin business applications (and other data producing services) |
| **object_origin_type**     | *string*       | Specific origin type related to the origin category                                           |
| **object_origin**          | *string*       | Name of the application which matches the app-key in the connection records                     |
| **object_creation_date**   | *date*         | Creation time of the document                                                                                    |
| **data**                   | Product Object | The actual product data (see below)                                                                           |

### Data

Below is the content of the `data` object used with `product`.

| Field                          | Data Type           | Description                                                        |
| :----------------------------- | :------------------ | :----------------------------------------------------------------- |
| **product_name**               | *string*            | The specific product name retrieved                                |
| **product_id**                 | *string*            | Specific ID related to the product                     |
| **product_group**              | *string*            | Specific group related to the product                  |
| **product_variant**            | *string[]*          | Specific variant related to the product                |
| **product_handle**             | *string*            | Specific handle related to the product                 |
| **product_sku**                | *string*            | SKU of the product                    |
| **created_at**                 | *date*              | Original creation time of the product in the app                                                      |
| **updated_at**                 | *date*              | Last modified time of the product in the app                                           |
| **deleted_at**                 | *date*              | Time of deletion of the product, if removed from the app                                           |
| **product_cost**               | *number*            | The unit cost of the product                                       |
| **product_net_price**          | *number*            | The unit net price of the product                                  |
| **product_gross_price**        | *number*            | The unit gross price of the product                                |
| **inventory_product**          | *boolean*           | If the product has stock values, the inventory is tracked              |
| **inventory_product_quantity** | *number*            | The units of product available for sale                            |
| **product_cost_value**         | *number*            | The total cost value of the product (product cost x quantity)      |
| **product_sale_value**         | *number*            | The total sale value of the product (product net price x quantity) |
