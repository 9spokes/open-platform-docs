## Staff wages

Staff wages is the record of pay run categorised by employment type .

```json
{ 
    "staff_wages": [
        {
            "employment_type" : "FULL-TIME",
            "gross_pay" : 19000.0,
            "date" : "2017-10-31T00:00:00.000Z"
        }, 
        {
            "employment_type" : "CONTRACTOR",
            "gross_pay" : 2450.0,
            "date" : "2017-10-31T00:00:00.000Z"
        }, 
        {
            "employment_type" : "PART-TIME",
            "gross_pay" : 420.0,
            "date" : "2017-10-31T00:00:00.000Z"
        },       
    ]
}

```

### Data schema

| Field               | Data Type | Description                                                                                                                 |
|---------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------|
| **employment_type** | *string*  | Types of employment <ul><li>`FULL-TIME`</li><li>`PART-TIME`</li><li>`CONTRACTOR`</li><li>`INTERN`</li><li>`OTHER`</li></ul> |
| **gross_pay**       | *string*  | The amount of money paid                                                                                                    |
| **date**            | *date*    | Payment date                                                                                                                |

