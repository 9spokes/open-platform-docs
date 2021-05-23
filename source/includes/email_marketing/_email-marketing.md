## Email Marketing

Email Marketing data simplifies the analysis of performance of email campaigns

```json
{
  "email_marketing": [
    {
      "id": "string",
      "web_id": "string",
      "created": "date",
      "status": "string",
      "name": "string",
      "type": "string",
      "list_id": "string"
    }
  ]
}
```

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
