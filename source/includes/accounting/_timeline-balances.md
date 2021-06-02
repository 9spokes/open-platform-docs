## Timeline Balance

A timeline/trial balance is a list of all the general ledger accounts contained in the ledger of a business.

```json

"trial_balance": {
  "balance_date": "2020-06-30",
  "accounts": [
    {
      "status" : "ACTIVE",
      "account_type" : "bank",
      "account_currency" : "NZD",
      "account_category" : "assets",
      "account_name" : "Petty Cash",
      "value_type" : "debit",
      "total_value" : "261,396.0",
      "account_identifier" : "959af5f4-9925-44e8-b283-7ddf4b427238",
      "account_code" : "1000"
    },
    {
      "status" : "ACTIVE",
      "account_type" : "sales",
      "account_currency" : "NZD",
      "account_category" : "revenue",
      "account_name" : "Sales",
      "value_type" : "credit",
      "total_value" : "23,000.0",
      "account_identifier" : "859af5f4-9925-34e8-b283-7ddf4b427237",
      "account_code" : "4000"
    },
    {
      "status" : "ACTIVE",
      "account_type" : "tax",
      "account_currency" : "NZD",
      "account_category" : "liability",
      "account_name" : "gst",
      "value_type" : "credit",
      "total_value" : "1,500.0",
      "account_identifier" : "759af5f4-9925-44e8-b283-7ddf4b427236",
      "account_code" : "2005"
    }          
  ]
}
```

### Data Schema

| Field                | Data Type              | Description                                                                                                                   |
| :------------------- | ---------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **account_identifier** | *string*               | Account ID                                                                                                                    |
| **account_name**       | *string*               | Account name                                                                                                                  |
| **account_code**       | *string*               | The chart of accounts code                                                                                                    |
| **account_type**       | *string*               | Type of the account, possible values are `bank`, `current`, `equity`, `fixed`, `overheads`, `payroll`, `sales`, `tax`, `term` |
| **account_category**   | *string*               | The category of account this is. Must be one of `assets`, `equity`, `expense`, `liability`, `revenue`                         |
| **account_currency**   | *string[3]*            | Currency of the account                                                                                                       |
| **status**             | *string                | Whether the account is active or not                                                                                          |
| **value_type**         | *string*               | Debit/Credit                                                                                                                  |
| **total_value**        | *number*               | The value of the account                                                                                                      |
