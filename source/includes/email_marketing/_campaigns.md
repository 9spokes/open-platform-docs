## Campaigns

Campaign data simplifies the analysis of email campaign performance. Following is the data specification for Campaign as extracted from Email Marketing OSPs

> Retrieving the Campaigns data for a connection is done by querying the `campaigns` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/data/campaigns \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of campaign data as seen below.

```json
{
  "results": [
    {
        "campaign_id" : "f5c755c5-2352-4ee0-8c21-9acef700b2ca",
        "created_at" : "2021-04-14T22:51:58.000Z",
        "updated_at" : "2021-04-15T08:36:09.000Z",
        "sent_time" : "2021-04-15T08:36:10.000Z",
        "status" : "Done",
        "name" : "New Test Campaign",
        "type" : "NEWSLETTER",
        "campaign_report" : {
            "sends" : 22,
            "abuse_reports":0,
            "opens" : 22,
            "bounces" : 4,
            "clicks" : 3,
            "deliveries" : 2,
            "deliveries_unopened" : 2
        }
    },
    {
        "campaign_id" : "3a9d454f-b723-415e-a302-9dcc8fded602",
        "created_at" : "2021-04-14T22:46:43.000Z",
        "updated_at" : "2021-04-14T22:47:28.000Z",
        "sent_time" : "2021-04-14T22:47:29.000Z",
        "status" : "Done",
        "name" : "Test Campaign 15/04",
        "type" : "NEWSLETTER",
        "campaign_report" : {
            "opens" : 22,
            "abuse_reports":0,
            "bounces" : 4,
            "clicks" : 3,
            "sends" : 2,
            "deliveries" : 2,
            "deliveries_unopened" : 2
        }
    }
  ]
}

```
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/data/campaigns</code>


### Data Schema

| Field                   | Data Type | Description                         |
|:------------------------|:----------|:------------------------------------|
| **campaign_id**         | *string*  | Campaign ID (App-wide unique ID)    |
| **created_at**          | *date*    | Campaign creation date              |
| **updated_at**          | *date*    | Campaign last updated date          |
| **sent_time**           | *date*    | Campaign sent time                  |
| **status**              | *string*  | Campaign status                     |
| **name**                | *string*  | Campaign name                       |
| **type**                | *string*  | Campaign type                       |
| **campaign_report**     | *object*  | Report on the campaign              |
| **opens**               | *int*     | Total number of opens               |
| **clicks**              | *int*     | Total number of clicks              |
| **sends**               | *int*     | Total number of sends               |
| **abuse_reports**       | *int*     | Total number of abuse_reports       |
| **bounces**             | *int*     | Total number of bounces             |
| **deliveries**          | *int*     | Total number of deliveries          |
| **deliveries_unopened** | *int*     | Total number of deliveries_unopened |


