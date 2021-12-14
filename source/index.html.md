---
title: API Reference

language_tabs:
  - shell
  - javascript

toc_footers:
  - <a href='https://www.9spokes.com/app-partners'>9Spokes</a>
  - <a href='https://www.9spokes.com/terms-and-conditions'>Terms of Use</a>
  - <a href='https://sandbox.api.9spokes.com/portal/signup'>Try 9Spokes Open</a>

includes:
  - organisation/index
  - organisation/redirect
  - organisation/apps
  - companies/index
  - connections/index
  - accounting/index
  - accounting/bills
  - accounting/invoices
  - accounting/products
  #- accounting/cards
  - accounting/contacts
  - accounting/trial-balance
  - accounting/business
  # - accounting/goods-services-transaction
  # - accounting/tax-rates
  # accounting/organisation
  - banking/index
  - banking/accounts
  - hr/index
  - hr/leaves
  - hr/pay-run-summary
  - hr/staff-wages
  - pos/index
  - pos/products
  - pos/sales
  # - pos/stockItems
  - social_marketing/index
  - social_marketing/social-marketing
  - email_marketing/index
  - email_marketing/campaigns
  - email_marketing/growth_history
  - web_analytics/index
  - web_analytics/web-analytics

search: true
  
code_clipboard: true
---

# 9Spokes Open

## Overview

Welcome! 9Spokes Open APIs are categorized by a growing list of data sources like Accounting, Banking, POS and others.

Under each data category, the following pieces are listed:

* Summary of the data category
* API endpoint path with query parameters
* Data Schema definition with field descriptions
* A sample JSON structure containing dummy data

## Authentication

> To authorize, use this code:

```shell
# The example below assumes you have the API_ROOT and API_KEY environment variables set
curl https://${API_ROOT}/ -H "Authorization: ${API_KEY}"
```

```javascript
import 9spokes from 'nsp';

const api = 9spokes.authorize(process.env.API_KEY);
```

> The example above assumes the `API_KEY` is defined as an environment variable.

All requests to any 9Spokes API require a valid API key.  API keys are 64-byte strings and should be attached to each request using the HTTP `Authorization` header.

Do not specify a scheme (such as `basic` or `bearer`) and do not base64-encode your key.  Instead, use your API key directly in the `Authorization` header.

`Authorization: 63TX2kPSahV...xk7MKge9ut`

<aside class="success">
You must replace <code>63TX2kPSahV...xk7MKge9ut</code> with your own API key.
</aside>

## Environments

### Sandbox

All app developers must begin their journey by first integrating with our sandbox environment.  The sandbox environment allows you to safely test your application without worrying about scopes, rate limits, or other production features.

<aside class="notice">
The API root for the Sandbox environment is <code>https://sandbox.api.9spokes.com</code>
</aside>

You may generate up to 2 Sandbox API keys, the first of which is automatically generated and sent to you by email.

### Production

Once your app development is complete, you may request Production API keys to interact with the live environment. Production APIs are identical to their Sandbox counterparts with the exception of the root URL.

<aside class="notice">
The API root for the live environment is <code>https://api.9spokes.com</code>
</aside>

<aside class="warning">Sandbox API keys cannot be used in the live environment and vice-versa.</aside>

## API Structure

### Requests

The 9Spokes API organizes data in a RESTful manner.  This means data resources are organized hierarchically, with the `company` object being the topmost resource in most cases.

### Responses

All API responses adhere to a strict JSON data format making it easy for app developers to parse success & error responses.  The `content-type` is always `application/json` and the response body is always an object containing, at the very least, a `status` key.  The value of `status` is either `ok` for successes or `err` for errors.

HTTP status codes are used to further categorize the response.  The table below denotes all the supported HTTP response codes.

| HTTP Code | Meaning                 | Corrective Action                                                      |
| --------- | ----------------------- | ---------------------------------------------------------------------- |
| **200**   | *OK*                    | The request was processed successfully.                                |
| **400**   | *Bad Request*           | The request is invalid. Check the format of your request and try again. |
| **401**   | *Unauthorized*          | The API key is not accepted.                                           |
| **403**   | *Forbidden*             | The request is denied, however the API key may be valid.                 |
| **404**   | *Not Found*             | The specified resource does not exist.                                  |
| **405**   | *Method Not Allowed*    | Only the documented HTTP verbs are supported.                           |
| **429**   | *Too Many Requests*     | You have hit a rate limit. Reduce your request rate.                   |
| **500**   | *Internal Server Error* | An internal error has occurred processing your request.                  |
| **503**   | *Service Unavailable*   | The API is temporarily unavailable.                                     |

### Success Response

Successful responses yield a HTTP status code of `200` and a JSON body similar to the structure below:

> A typical success response

```json
{
  "status": "ok",
  "correlationId": "daf07c66-c954-4853-ab5d-01c7b29b80a9",  
  "details": {
    // data
  }
}
```

The `status` key is set to `ok` and the `details` key is present.

<aside class="warning">Depending on the context of the request, the value of <code>details</code> could either be an <i>object</i> or an <i>array</i>.</aside>

<!-- <span class="api api-get" /> -->

### Error Response

API requests that could not be processed will carry a HTTP code that is greater than `399` and a body similar to the structure shown here.

> An error response.  `message` contains the error string

```json
{
  "status": "err",
  "correlationId": "daf07c66-c954-4853-ab5d-01c7b29b80a9",
  "message": "This connection does not exist"
}
```

### Correlation ID

A `correlationId` is included in both successful and error response. Please provide this ID if you are contacting 9Spokes support regarding an issue.

## Querying

The 9Spokes API uses OData (Open Data Protocol) format to filter response data. 

<aside class="warning">The below queries will only work when requesting connected app data.</aside>

### Filter ($filter)  

The `$filter` query option allows you to filter data sets based on the properties available. 

| Operator  | Description             |
| --------- | ----------------------- |
| **eq**    | *Equal*                 |
| **ne**    | *Not equal*             |
| **gt**    | *Greater than*          |
| **ge**    | *Greater than or equal* |
| **lt**    | *Less than*             |
| **le**    | *Less than or equal*    |
| **and**   | *Logical and*           |
| **or**    | *Logical or*            |


- Single quotes for string type values.

<span class="api api-example"></span> <code>/companies/{companyId}/connections/{connectionId}/data/invoices?$filter=data.transaction_status eq 'UNPAID'</code>

- The current supported format for dates is **(yyyy-mm-dd)** 

<span class="api api-example"></span> <code>/companies/{companyId}/connections/{connectionId}/data/invoices?$filter=data.transaction_date eq 2021-08-11</code>

### Orderby ($orderby)  

The `$orderBy` query option allows you to order data sets based on the property name provided. 

<span class="api api-example"></span> <code>/companies/{companyId}/connections/{connectionId}/data/invoices?$orderBy=data.transaction_date</code>


### Select ($select)  

The `$select` query option allows you to request a specific set of properties. 

At least 2 property names must be provided.

<span class="api api-example"></span> <code>/companies/{companyId}/connections/{connectionId}/data/invoices?$select=data.transaction_date,data.transaction_status</code>

## Pagination

The 9Spokes API default page is set to size 10, however this can be modified. A response will have `total` property showing a specified number of results. 

> A typical success response of data

```json
{
  "results": [...],
  "total": 50,
}
```
- To set the page size and get specific number of results, use `$top`. 

<span class="api api-example"></span> <code>/companies/{companyId}/connections/{connectionId}/data/invoices?$top=5</code>

- To paginate through the list of results, use `$skip`.

<span class="api api-example"></span> <code>/companies/{companyId}/connections/{connectionId}/data/invoices?$top=5&$skip=5</code>


## Using Postman

For convenience, you may download a copy of a pre-defined [Postman collection](https://cms.9spokes.com/assets/uploads/documents/9Spokes-Open-Postman-Collection.json) to help you get started quickly.

You will need to input your own API key by choosing the folder-level _Authorization_ (9Spokes Open > Authorization) and inputing a key in the `Value` field.

![Configuring Authorization](/images/postman/postman-api-key.png "Postman API Key")

The collection is grouped logically by object type.  Each object type (e.g. Organization, Companies, Connections, ...etc) is kept in its own folder.

![Object Types](/images/postman/postman-folders.png "Postman Folders")

<aside class="notice"><b>Note:</b> only <i>Invoices</i> and <i>Trial Balances</i> are included as example, though you can extend the same approach for other data sources.</aside>
