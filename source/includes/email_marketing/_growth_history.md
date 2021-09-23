## Growth history

Growth history data is the analysis of month-by-month growth activity for list/audience. Following is the data specification for growth history as extracted from Email Marketing OSPs

> Retrieving the growth history data for a connection is done by querying the `growth_history` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/data/growth_history \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of Email Marketing data as seen below.

```json
{
  "results": [
    {
      "list_id": "69b1d36343",
      "list_name": "List 1",
      "list_date_created": "2017-05-17T04:47:45.000Z",
      "growth_history": [
        {
          "reconfirm": 0.0,
          "deleted": 0.0,
          "existing": 0.0,
          "imports": 0.0,
          "subscribed": 10.0,
          "cleaned": 1.0,
          "pending": 0.0,
          "transactional": 0.0,
          "month": "2021-08-10T00:00:00.000Z",
          "optins": 0.0,
          "unsubscribed": 0.0
        },
        {
          "reconfirm": 0.0,
          "deleted": 0.0,
          "existing": 0.0,
          "imports": 0.0,
          "subscribed": 10.0,
          "cleaned": 1.0,
          "pending": 0.0,
          "transactional": 0.0,
          "month": "2021-07-10T00:00:00.000Z",
          "optins": 0.0,
          "unsubscribed": 0.0
        }
        ...
      ]
    },
    ...
  ]
}

```
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/data/growth_history</code>


### Data Schema

| Field                 | Data Type | Description                    |
|:----------------------|:----------|:-------------------------------|
| **list_id**           | *string*  | List ID (App-wide unique ID)   |
| **list_name**         | *string*  | List name                      |
| **list_date_created** | *string*  | List creation date             |
| **growth_history**    | *array*   | Array of growth_history object |
| **reconfirm**         | *float*   | Number of reconfirm            |
| **deleted**           | *float*   | Number of deleted              |
| **existing**          | *float*   | Number of existing             |
| **imports**           | *float*   | Number of imports              |
| **subscribed**        | *float*   | Number of subscribed           |
| **cleaned**           | *float*   | Number of cleaned              |
| **pending**           | *float*   | Number of pending              |
| **transactional**     | *float*   | Number of transactional        |
| **month**             | *date*    | record's month                 |
| **optins**            | *float*   | Number of optins               |
| **unsubscribed**      | *float*   | Number of unsubscribed         |


