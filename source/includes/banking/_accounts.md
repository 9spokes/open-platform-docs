## Bank Accounts

A list of bank accounts from a connected app platform for the associated business.  Following is the data specification for a bank account that is extracted from banking or accounting apps

> Retrieving the list of bank accounts for a connection is done by querying the `bank_accounts` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/data/bank_accounts \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of bank accounts as seen below.

```json
{
    "results": [
        {
            "balance_date": "2020-11-02T00:00:00.000Z",
            "data": [
                {
                    "account_id": "59",                  
                    "account_name": "My Savings",
                    "account_active": true,
                    "account_balance": 10951677.31,
                    "account_currency": "GBP"
                },
                {
                    "account_id": "69",                
                    "account_name": "PayPal Funds Transfer Account",
                    "account_active": true,
                    "account_balance": 231232.90,
                    "account_currency": "GBP" 
                }
            ]
        },
        ...
    ]
}
```
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/data/bank_accounts</code>

### Data Schema

| Field               | Data Type | Description                                                |
| -----------------   | --------- | ---------------------------------------------------------- |
| **balance_date**    | *date*    | The date when the bank accounts were recorded              |
| ***data***          | *array*   | Array of accounts                                          |
| **account_id**      | *string*  | The unique identifier for the account in the platform      |
| **account_name**    | *string*  | Name of the bank account in the platform                   |
| **account_active**  | *bool*    | true or false if the account is active or not              |
| **account_balance** | *number*  | The total balance of the bank account as of `balance_date` |
