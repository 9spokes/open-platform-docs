## Bank Accounts

A list of bank accounts from a connected app platform for the associated business.  Following is the data specification for a bank account that is extracted from banking OSPs

> Retrieving the list of bank accounts for a connection is done by querying the `bankAccounts` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/bankAccounts \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of bank accounts as seen below.

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
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/bankAccounts</code>

### Data Schema

| Field             | Data Type | Description                                                |
| ----------------- | --------- | ---------------------------------------------------------- |
| **balance_date**  | *date*    | The date when the bank accounts were recorded              |
| ***accounts***    | *array*   | Array of accounts                                          |
| **id**            | *string*  | The unique identifier for the account in the platform      |
| **number**        | *string*  | Account number for the bank account                        |
| **name**          | *string*  | Name of the bank account in the platform                   |
| **status**        | *string*  | Status of the bank account                                 |
| **total_balance** | *number*  | The total balance of the bank account as of `balance_date` |
