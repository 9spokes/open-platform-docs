## Business

This is the specification for the business of a user. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/data/business</code>

### Field Description

> Below is the schema definition for a `business` record

```json
{
    "result": {
        "business": {
            "addresses": [
                {
                    "country": "New Zealand",
                    "line1": "AECOM House Level 5/8 Mahuhu Crescent",
                    "line2": "CBD Auckland",
                    "postal_code": "1010",
                    "type": "billing"
                }
            ],
            "currency": "NZD",
            "financial_year": {
                "end_day": 31,
                "end_month": 3
            },
            "id": "b1d9725d-43dd-47c9-87f9-d2f2a2bdbdd5",
            "name": "9SpokesTech",
            "registration_number": "187845566",
            "tax": {
                "id": "ceeb248e-9cc8-46b1-937a-b1fd2084e9bc",
                "name": "GST"
            },
            "view_id": "4471d27e06ac724b5dd676bee05854be"
        }
    }
}
```
### Business

Below is the content of the `business` object.

| Field                   | Data Type   | Description                             |
| :---------------------- | :---------- | :----------------------------------     |
| **id**                  | *string*    | Business identifier                     |
| **addresses**           | *[]address* | An array of addresses as defined below  |
| **currency**            | *string*    | Subscription state date                 |
| **financial_year**      | *financial_year* | financial_year object              |
| **name**                | *string*    | Business name                           |
| **registration_number** | *string*    | Business registration number            |
| **tax**                 | *tax*       | tax object                              |
| **view_id**             | *string*    | Reference of the company selected from accounting platform|

### financial_year

| Field                   | Data Type   | Description                             |
| :---------------------- | :---------- | :----------------------------------     |
| **end_day**             | *number*    | financial year end day                  |
| **end_month**           | *number*    | financial year end month                |

### tax

| Field                   | Data Type   | Description                             |
| :---------------------- | :---------- | :----------------------------------     |
| **id**                  | *string*    | tax identifier                          |
| **end_month**           | *string*    | name of the tax                         |

### address

| Field                   | Data Type   | Description                             |
| :---------------------- | :---------- | :----------------------------------     |
| **country**             | *string*    | country                                 |
| **line1**               | *string*    | address line 1                          |
| **line1**               | *string*    | address line 2                          |
| **postal_code**         | *string*    | postal code                             |
| **type**                | *string*    | type of the address                     |



