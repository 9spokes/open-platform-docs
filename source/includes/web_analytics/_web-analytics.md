## Web Analytics

This is the specification for Google Analytics. It is in JSON format and the metadata allow the resolvers to identify the type of data required and the related fields to transform.

> Below is a sample document for a Web Analytics record

```json
{
  "data": [
    {
      "ads_revenue": "string",
      "bounce_rates": "string",
      "exit_rate": "string",
      "avg_time_on_page": "string",
      "total_page_view": "string",
      "source_of_visitor": "string"
    }
  ]
}
```

### Data Schema

| Field               | Data Type | Description |
| :------------------ | :-------- | :---------- |
| `ads_revenue`       | `string`  |             |
| `bounce_rates`      | `string`  |             |
| `exit_rate`         | `string`  |             |
| `avg_time_on_page`  | `string`  |             |
| `total_page_view`   | `string`  |             |
| `source_of_visitor` | `string`  |             |
