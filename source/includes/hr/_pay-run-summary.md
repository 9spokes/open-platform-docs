## Pay run summary

Summarized pay run of different periods.

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

### Data schema

| Field          | Data Type | Description                                                                                                                                                                        |
|----------------|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **pay_period** | *string*  | Recurring length of time over which employee time is recorded and paid <ul><li>`Weekly`</li><li>`Bi-weekly`</li><li>`Quarterly`</li><li>`Monthly`</li><li>`Semi-monthly`</li></ul> |
| **start_date** | *date*  | Start date of the pay period                                                                                                                                                       |
| **end_date**   | *date*  | End date of the pay period
| **hours**      | *number*    | Total number of work hours recorded for that period                                                                                               |
| **gross_pay**  | *number*    | The amount of money paid to employees for that period                                                                                                    |

