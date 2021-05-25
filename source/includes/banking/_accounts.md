## Bank Accounts

Bank accounts is a list of real-life bank accounts from a connected app platform for the associated business.

```json
{
    "balance_date": "2020-11-02T00:00:00.000Z",
    "accounts": [
        {
            "id": "59",
            "number": "154452222",
            "name": "My Savings",
            "status": "ACTIVE",
            "total_balance": 10951677.31,
            "currency": "GBP"
        },
        {
            "id": "69",
            "number": "133233",
            "name": "PayPal Funds Transfer Account",
            "status": "ACTIVE",
            "total_balance": 231232.90,
            "currency": "GBP" 
        }
    ]
}
```

### Data schema

| Field             | Data Type | Description                                                |
|-------------------|-----------|------------------------------------------------------------|
| **balance_date**  | *date*    | The date when the bank accounts were recorded              |
| ***accounts***    | *array*   | Array of accounts                                          |
| **id**            | *string*  | The unique identifier for the account in the platform      |
| **number**        | *string*  | Account number for the bank account                        |
| **name**          | *string*  | Name of the bank account in the platform                   |
| **status**        | *string*  | Status of the bank account                                 |
| **total_balance** | *number*  | The total balance of the bank account as of `balance_date` |
