## Trial Balance

A timeline/trial balance is a list of all the general ledger accounts contained in the ledger of a business.

<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/data/trial_balance</code>

```json

{
  "results": [
    {
      "balance_date": "2021-08-08T00:00:00Z",
      "data": [
        {
          "account_status": "ACTIVE",
          "account_type": "bank",
          "account_currency": "NZD",
          "account_category": "assets",
          "account_name": "Petty Cash",
          "value_type": "debit",
          "total_value": 261396.00,
          "account_identifier": "959af5f4-9925-44e8-b283-7ddf4b427238",
          "account_code": "1000"
        },
        {
          "account_status": "ACTIVE",
          "account_type": "sales",
          "account_currency": "NZD",
          "account_category": "revenue",
          "account_name": "Sales",
          "value_type": "credit",
          "total_value": 23000.0,
          "account_identifier": "859af5f4-9925-34e8-b283-7ddf4b427237",
          "account_code": "4000"
        },
        {
          "account_status": "ACTIVE",
          "account_type": "tax",
          "account_currency": "NZD",
          "account_category": "liability",
          "account_name": "gst",
          "value_type": "credit",
          "total_value": 1500.0,
          "account_identifier": "759af5f4-9925-44e8-b283-7ddf4b427236",
          "account_code": "2005"
        }
      ]
    },
    ...
  ]
}

```

### Data Schema

| Field                | Data Type              | Description                                                                                                                   |
| :------------------- | ---------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **account_identifier** | *string*               | Account ID                                                                                                                  |
| **account_name**       | *string*               | Account name                                                                                                                |
| **account_code**       | *string*               | The chart of account codes                                                                                                  |
| **account_type**       | *string*               | The account type (`bank`, `current`, `equity`, `fixed`, `overheads`, `payroll`, `sales`, `tax`, `term`, `current_accounts_receivable`.`current_account_payable`)                     |
| **account_category**   | *string*               | The account category (`assets`, `equity`, `expense`, `liability`, `revenue`)                                                |
| **account_currency**   | *string*               | Currency of the account                                                                                                     |
| **account_status**     | *string*               | Whether the account is active or not                                                                                        |
| **value_type**         | *string*               | Debit/Credit                                                                                                                |
| **total_value**        | *number*               | The value of the account                                                                                                    |
