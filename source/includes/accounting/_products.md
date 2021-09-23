## Product

This is the specification for Product Items. It is in JSON formam. Following is the data specification for products as extracted from accounting apps

> Retrieving the products data for a connection is done by querying the `products` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/data/data/products \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of Product data as seen below.

```json
{
  "results": [
    {
      "data": {
        "inventory_product_quantity": 70,
        "product_cost": 50,
        "product_cost_value": 3500,
        "product_group": "Gaming",
        "product_id": "7683bc1e9ad34b099220bdc895bbc2c4",
        "product_name": "S70 Mouse",
        "product_variant": ["white", "black"],
        "product_net_price": 70,
        "product_sale_value": 4900
      }
    },
    ...
  ]
}

```
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/data/products</code>

### Data

Below is the content of the `data` object used with `product`.

| Field                          | Data Type           | Description                                                        |
| :----------------------------- | :------------------ | :----------------------------------------------------------------- |
| **product_name**               | *string*            | The specific product name retrieved                                |
| **product_id**                 | *string*            | Specific ID related to the product                                 |
| **product_group**              | *string*            | Specific group related to the product                              |
| **product_variant**            | *string[]*          | Specific variant related to the product                            |
| **product_cost**               | *number*            | The unit cost of the product                                       |
| **product_net_price**          | *number*            | The unit net price of the product                                  |
| **inventory_product_quantity** | *number*            | The units of product available for sale                            |
| **product_cost_value**         | *number*            | The total cost value of the product (product cost x quantity)      |
| **product_sale_value**         | *number*            | The total sale value of the product (product net price x quantity) |
