## Email Marketing

Email Marketing data is gathered from apps like MailChimp and ConstantContact. This will allow you to analyse performance of your email campaigns

> Below is a sample document for a `Email Marketing` record

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
| `id`                   | `string`  | `campaign id (OSP unique id)`                                       |
| `web_id`               | `string`  | `id used for web links`                                             |
| `created`              | `string`  | `campaign creation date`                                            |
| `status`               | `string`  | `campaign_stats (Draft, Scheduled, Executing, Done, Error, Removed)`|
| `name`                 | `string`  |  `campaign name`                                                    |
| `type`                 | `string`  |  `[Newsletter, Ratings and Reviews, Announcement, Business Letter]` |
| `list_id`              | `string`  |  `id of recipient list`                                             |