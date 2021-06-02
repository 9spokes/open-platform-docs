## Email Marketing

Email Marketing data simplifies the analysis of performance of email campaigns. Following is the data specification for email marketing as extracted from Email Marketing OSPs

> Retrieving the Email Marketing data for a connection is done by querying the `emailMarketing` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/emailMarketing \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of Email Marketing data as seen below.

```json
{
  "email_marketing": [
    {
      "id": "1234",
      "web_id": "4567",
      "created": "d2021-01-22T00:00:00.000Zate",
      "status": "SENT",
      "name": "Test Campaign",
      "type": "Email",
      "list_id": "5455"
    }
  ]
}
```
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/emailMarketing</code>


### Data Schema

| Field                  | Data Type | Description                                                         |
| :--------------------- | :-------- | :-------------------------------------------------------------------|
| **id**                   | *string*  | Campaign ID (App-wide unique id)                                       |
| **web_id**               | *string*  | ID used for web links                                             |
| **created**              | *string*  | Campaign reation date                                            |
| **status**               | *string*  | Campaign stats (`Draft`, `Scheduled`, `Executing`, `Done`, `Error`, `Removed`)|
| **name**                 | *string*  | Campaign name                                                    |
| **type**                 | *string*  | One of `Newsletter`, `Ratings and Reviews`, `Announcement`, `Business Letter` |
| **list_id**              | *string*  | ID of recipient list                                             |
