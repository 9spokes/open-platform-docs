## Leaves

A leave is time-off requested to a company by an employee. Following is the data specification for a leave record that is extracted from HR/Payroll OSPs

> Retrieving the list of leaves for a connection is done by querying the `leaves` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/data/leaves \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of leaves as seen below.

```json
{
  "results": [
    {
      "leave": {
        "id": "314117",
        "type": "SICK",
        "status": "PENDING",
        "start_date": "2021-01-15T00:00:00.000Z",
        "end_date": "2021-01-19T00:00:00.000Z",
        "application_url": "https://www.talenox.com/apps/leave/applications/314117",
        "employee_id": "176772",
        "employee_name": "Kia Solo",
        "dates": [
          "2021-01-15T00:00:00.000Z",
          "2021-01-16T00:00:00.000Z",
          "2021-01-17T00:00:00.000Z",
          "2021-01-18T00:00:00.000Z",
          "2021-01-19T00:00:00.000Z"
        ]
      }
    },
    {
      "leave": {
        "id": "252826",
        "type": "PAID",
        "status": "APPROVED",
        "start_date": "2020-07-31T00:00:00.000Z",
        "end_date": "2020-08-03T00:00:00.000Z",
        "application_url": "https://www.talenox.com/apps/leave/applications/252826",
        "employee_id": "176772",
        "employee_name": "Obigud Kenobee",
        "dates": [
          "2020-07-31T00:00:00.000Z",
          "2020-08-01T00:00:00.000Z",
          "2020-08-02T00:00:00.000Z",
          "2020-08-03T00:00:00.000Z"
        ]
      }
    }
  ]
}


```
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/leaves</code>

### Data Schema

| Field               | Data Type        | Description                                                                                                    |
|---------------------|------------------|----------------------------------------------------------------------------------------------------------------|
| **id**              | *string*         | Unique identifier of the leave request in the platform                                                             |
| **type**            | *string*         | The leave type, either: <ul><li>`SICK`</li><li>`PAID`</li><li>`UNPAID`</li><li>`OTHER`</li></ul>            |
| **status**          | *string*         | The leave status, either: <ul><li>`PENDING`</li><li>`DECLINED`</li><li>`APPROVED`</li><li>`OTHER`</li></ul> |
| **start_date**      | *date*           | Start date of the leave request                                                                                        |
| **end_date**        | *date*           | End date of the leave request                                                                                         |
| **application_url** | *string*         | URL to the leave application in the platform                                                                   |
| **employee_id**     | *string*         | Unique identifer of the employee who applied for the leave                                                     |
| **employee_name**   | *string*         | Name of the employee who applied for the leave                                                                     |
| ***dates***         | *array of dates* | Dates of the leave request                                                                              |
