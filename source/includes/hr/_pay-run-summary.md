## Pay run summary

Summarized pay run of different periods. Following is the data specification for pay run summary as extracted from HR/Payroll OSPs

> Retrieving pay run summary for a connection is done by querying the `payRunSummary` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/payRunSummary \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of pay run summary as seen below.


```json
{ 
    "pay_run_summary": [
        {
            "pay_period": "Semi-monthly",
            "start_date": "2019-10-14T00:00:00.000Z",
            "end_date": "2019-10-29T00:00:00.000Z",
            "hours": 120.0,
            "gross_pay": 7000.0               
        },
        {
            "pay_period": "Semi-monthly",
            "start": "2019-09-30T00:00:00.000Z",
            "end": "2019-10-13T00:00:00.000Z",
            "hours": 120.0,
            "gross_pay": 9000.0                
        }      
    ]
}

```
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/payRunSummary</code>

### Data schema

| Field          | Data Type | Description                                                                                                                                                                        |
|----------------|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **pay_period** | *string*  | Recurring length of time over which employee time is recorded and paid <ul><li>`Weekly`</li><li>`Bi-weekly`</li><li>`Quarterly`</li><li>`Monthly`</li><li>`Semi-monthly`</li></ul> |
| **start_date** | *date*  | Start date of the pay period                                                                                                                                                       |
| **end_date**   | *date*  | End date of the pay period
| **hours**      | *number*    | Total number of work hours recorded for that period                                                                                               |
| **gross_pay**  | *number*    | The amount of money paid to employees for that period                                                                                                    |

