## Staff Wages

Staff wages is the record of pay run categorized by employment type. Following is the data specification for staff wages as extracted from HR/Payroll OSPs

> Retrieving staff wages for a connection is done by querying the `staffWages` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/staffWages \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of staff wages as seen below.

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
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/staffWages</code>

### Data Schema

| Field               | Data Type | Description                                                                                                                 |
|---------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------|
| **employment_type** | *string*  | Types of employment <ul><li>`FULL-TIME`</li><li>`PART-TIME`</li><li>`CONTRACTOR`</li><li>`INTERN`</li><li>`OTHER`</li></ul> |
| **gross_pay**       | *string*  | The amount of money paid                                                                                                    |
| **date**            | *date*    | Payment date                                                                                                                |

