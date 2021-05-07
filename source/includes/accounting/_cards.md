## Cards

This is the specification for Cards. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

### Field Description

> Below is the schema definition for a `card` record

```json
{
  "user": "string",
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
      "account_number": "string",
      "account_spend_limit": "string",
      "card_holder_id": "string",
      "cardholder_first_name": "string",
      "cardholder_last_name": "string",
      "company_id": "string",
      "account_open_date": "date",
      "account_close_date": "date",
      "card_expiry_date": "date"
    }
  ]
}
```

> Below is a sample document

```json
{
  "user": "887cee1a-5d59-4509-ab7b-0f40a73fed69",
  "connection_id": "f4592653-7c08-4722-8920-c280c95991d7",
  "object_class": "card_data",
  "object_category": "banking",
  "object_type": "card",
  "object_origin_category": "banking",
  "object_origin_type": "accounting",
  "object_origin": "visa",
  "object_creation_date": "2020-11-19 11:00:01.096Z",
  "data": [
    {
      "account_number": "string",
      "account_spend_limit": "string",
      "card_holder_id": "string",
      "cardholder_first_name": "string",
      "cardholder_last_name": "string",
      "company_id": "string",
      "account_open_date": "date",
      "account_close_date": "date",
      "card_expiry_date": "date"
    }
  ]
}
```

Below is the metadata wrapper used to classify and search card data. The card data is stored under the `data` key.

| Field                    | Data Type        | Description                                                  |
| :----------------------- | :--------------- | :----------------------------------------------------------- |
| `user`                   | `UUIDv4`         | This is the user's id of the company that this transaction belongs to. |
| `connection_id`          | `UUIDv4`         | This is the connection_id which was used to retrieve the origin data. |
| `object_class`           | `string`         | This is used to retrieve a specific type of data schema:     |
| `object_category`        | `string`         | This is used to categorise the document.                     |
| `object_type`            | `string`         | This is the associated time dimension of the metric.         |
| `object_origin_category` | `string`         | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
| `object_origin_type`     | `string`         | This is the specific type of origin related to the origin category |
| `object_origin`          | `string`         | This is the name of the application which matches the app-key in the connection records. |
| `object_creation_date`   | `Date`           | Creation time of document                                    |
| `data`                   | `Array of stock item objects` | The actual product data, see below                           |

Below is the content of the `data` object used with `card`.

| Field                          | Data Type | Description                                         |
| :----------------------------- | :-------- | :-------------------------------------------------- |
| `account_number`                      | `string`  | Account number associated with the card retrieved from the extraction   |
| `account_spend_limit`                    | `string`  | The spending limit on the account |
| `card_holder_id`                | `string`  | The unique id for the card holder         |
| `cardholder_first_name`              | `string`  | Card holder's first name                     |
| `cardholder_last_name` | `string` | Cardholder's last name                    |
| `company_id`                  | `string`  | Company id associated to the card  |
| `account_open_date`                  | `date`  | Date when the account associated to the card was open  |
| `account_close_date`                  | `date`  | Date when the account associated to the card was closed  |
| `card_expiry_date`                  | `date`  | Card expiry date  |