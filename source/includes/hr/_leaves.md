## Leaves

A leave is a time-off requested to a specific company by a employee.

```json
{ 
    "leaves": [
        {
            "id": "314117",
            "type": "SICK",
            "status": "PENDING",
            "start_date": "2021-01-15T00:00:00.000Z",
            "end_date": "2021-01-19T00:00:00.000Z",           
            "application_url": "https://www.talenox.com/apps/leave/applications/314117",
            "employee_id":"176772",
            "employee_name":"Kia Solo",
            "dates": [  
                "2021-01-15T00:00:00.000Z", 
                "2021-01-16T00:00:00.000Z", 
                "2021-01-17T00:00:00.000Z", 
                "2021-01-18T00:00:00.000Z", 
                "2021-01-19T00:00:00.000Z" 
            ]              
        },
        {
            "id": "252826",
            "type": "PAID",
            "status": "APPROVED",
            "start_date": "2020-07-31T00:00:00.000Z",
            "end_date": "2020-08-03T00:00:00.000Z",       
            "application_url": "https://www.talenox.com/apps/leave/applications/252826",
            "employee_id":"176772",
            "employee_name":"Obigud Kenobee",
            "dates": [  
                "2020-07-31T00:00:00.000Z", 
                "2020-08-01T00:00:00.000Z", 
                "2020-08-02T00:00:00.000Z", 
                "2020-08-03T00:00:00.000Z" 
            ]              
        },       
    ]
}

```

### Data schema

| Field               | Data Type        | Description                                                                                                    |
|---------------------|------------------|----------------------------------------------------------------------------------------------------------------|
| **id**              | *string*         | The unique identifier of the leave in the platform                                                             |
| **type**            | *string*         | Type of the leave, either: <ul><li>`SICK`</li><li>`PAID`</li><li>`UNPAID`</li><li>`OTHER`</li></ul>            |
| **status**          | *string*         | status of the leave, either: <ul><li>`PENDING`</li><li>`DECLINED`</li><li>`APPROVED`</li><li>`OTHER`</li></ul> |
| **start_date**      | *date*           | Start date of the leave                                                                                        |
| **end_date**        | *date*           | End date of the leave                                                                                          |
| **application_url** | *string*         | URL to the leave application in the platform                                                                   |
| **employee_id**     | *string*         | The unique identifer of the employee applied for the leave                                                     |
| **employee_name**   | *string*         | Name of the employee applied for the leave                                                                     |
| ***dates***         | *array of dates* | Corresponding dates for the leave                                                                              |
