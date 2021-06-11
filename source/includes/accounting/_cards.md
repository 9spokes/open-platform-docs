## Cards

Following is the data specification for a card that is extracted from accounting/POS OSPs

> Retrieving the list of cards for a connection is done by querying the `cards` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/cards \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of cards as seen below.

```json
{
  "card_data": [
    {
      "account_number": "3217863218",
      "account_spend_limit": "30000.00",
      "card_holder_id": "31521",
      "cardholder_first_name": "Test",
      "cardholder_last_name": "Customer",
      "company_id": "133414",
      "account_open_date": "2021-01-22T00:00:00.000Z",
      "account_close_date": "2021-04-22T00:00:00.000Z",
      "card_expiry_date": "2021-04-22T00:00:00.000Z"
    }
  ]
}
```
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/cards</code>

### Data Schema

| Field                   | Data Type | Description                                                           |
| :---------------------- | :-------- | :-------------------------------------------------------------------- |
| **account_number**        | *string*  | Account number associated with the card retrieved from the extraction |
| **account_spend_limit**   | *string*  | The spending limit on the account                                     |
| **card_holder_id**        | *string*  | Unique ID for the cardholder                                     |
| **cardholder_first_name** | *string*  | Cardholder's first name                                              |
| **cardholder_last_name**  | *string*  | Cardholder's last name                                                |
| **company_id**            | *string*  | Company ID associated to the card                                     |
| **account_open_date**     | *date*    | Date when the account associated to the card was open                 |
| **account_close_date**    | *date*    | Date when the account associated to the card was closed               |
| **card_expiry_date**      | *date*    | Card expiry date                                                      |
