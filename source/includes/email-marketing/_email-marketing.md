## Email Marketing

This is the specification for Email Marketing. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

### Field Description

> Below is the schema definition for a `Email Marketing` record

```json
{
  "user": "string",
  "connection_id": "string",
  "object_class": "string",
  "object_category": "string",
  "object_type": "string",
  "object_origin_category": "string",
  "object_origin_type": "string",
  "object_origin": "string",
  "object_creation_date": "Date",
  "data": [
    {
      "ads_revenue": "string",
      "page_fans": "string",
      "page_followers": "string",
      "cardholder_last_name": "string",
      "overall_impressions": "string",
      "engagement_overviews": "date"
    }
  ]
}
```

> Below is a sample document for a `Email Marketing` record

```json
{
  "user": "887cee1a-5d59-4509-ab7b-0f40a73fed69",
  "connection_id": "f4592653-7c08-4722-8920-c280c95991d7",
  "object_class": "",
  "object_category": "",
  "object_type": "",
  "object_origin_category": "",
  "object_origin_type": "",
  "object_origin": "",
  "object_creation_date": "2020-11-19 11:00:01.096Z",
  "data": [
    {
      "views_to_actions": "string",
      "page_fans": "string",
      "page_followers": "string",
      "overall_impressions": "string",
      "engagement_overviews": "date"
    }
  ]
}
```

Below is the metadata wrapper used to classify and search Email marketing data. The Email marketing data is stored under the `data` key.

| Field                    | Data Type        | Description                                                  |
| :----------------------- | :--------------- | :----------------------------------------------------------- |
| `user`                   | `UUIDv4`         | This is the user's id of the company that this transaction belongs to. |
| `connection_id`          | `UUIDv4`         | This is the connection_id which was used to retrieve the origin data. |
| `object_class`           | `string`         | This is used to retrieve a specific type of data schema:     |
| `object_category`        | `string`         | This is used to categorise the document.                     |
| `object_type`            | `string`         | This is the associated time dimension of the metric.         |
| `object_origin_category` | `string`         | This is the 9 Spokes categorisation of data origin business applications (and other data producing services) |
| `object_origin_type`     | `string`         | This is the specific type of origin related to the origin category |
| `object_origin`          | `string`         | This is the name of the application which matches the app-key in the connection records. |
| `object_creation_date`   | `Date`           | Creation time of document                                    |
| `data`                   | `Array of stock item objects` | The actual product data, see below                           |

Below is the content of the `data` object used with `Email marketing`.

| Field                          | Data Type | Description                                         |
| :----------------------------- | :-------- | :-------------------------------------------------- |
| `views_to_actions`                      | `string`  |    |
| `page_fans`                    | `string`  |  |
| `page_followers`                | `string`  |          |
| `overall_impressions`              | `string`  |                 |
| `engagement_overviews` | `string` |                |
