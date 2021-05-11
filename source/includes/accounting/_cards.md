## Cards

> Below is a sample document

```json
{
  "card_data": [
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

### Data Schema

| Field                   | Data Type | Description                                                           |
| :---------------------- | :-------- | :-------------------------------------------------------------------- |
| `account_number`        | `string`  | Account number associated with the card retrieved from the extraction |
| `account_spend_limit`   | `string`  | The spending limit on the account                                     |
| `card_holder_id`        | `string`  | The unique id for the card holder                                     |
| `cardholder_first_name` | `string`  | Card holder's first name                                              |
| `cardholder_last_name`  | `string`  | Cardholder's last name                                                |
| `company_id`            | `string`  | Company id associated to the card                                     |
| `account_open_date`     | `date`    | Date when the account associated to the card was open                 |
| `account_close_date`    | `date`    | Date when the account associated to the card was closed               |
| `card_expiry_date`      | `date`    | Card expiry date                                                      |
