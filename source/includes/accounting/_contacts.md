## Contacts

A contact is a person or organization that is associated with your business. Following is the data specification for contacts extracted from accounting/POS OSPs

> Retrieving the list of contacts for a connection is done by querying the `contacts` endpoint for that connection

```sh
$ curl https://${API_ROOT}/companies/69894a02-9c03-40ac-a06a-ee6e4b38c6fb/connections/52684382-abff-45fa-a3f2-ced175adfe61/contacts \
    -H "Authorization: ${API_KEY}"
```

> The response is an array of contacts as seen below.


```json
{
    "contacts": [
        {
            "type" : "CUSTOMER",
            "id": "689336287289",          
            "email":"k.h@gmail.com",       
            "name": "Katherine Hammes",
            "phone": "0321 15151 454",
            "addresses":[
                {
                    "type":"BILLING",
                    "country":"New Zealand",
                    "postal_code":"1010",
                    "line1":"88 high Road",
                    "line2":"Auckland Central, Auckland 1010" 
                },
                {
                    "type":"DELIVERY",
                    "country":"New Zealand",
                    "postal_code":"0622",
                    "line1":"1-11 Greenwood road",
                    "line2":"Hauraki, auckland" 
                }                
            ]
        },
        {           
            "type" : "SUPPLIER",
            "id": "122372889",
            "email":"hrdsteel@gmail.com",       
            "name": "Hard steel",
            "phone": "124 546 84123",
            "addresses":[
                {
                    "type":"BILLING",
                    "country":"Australia",
                    "postal_code":"1999",
                    "line1":"29 flicker street",
                    "line2":"New South Wales" 
                },           
            ]
        }
    ]
}
```
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/contacts</code>

### Data Schema

| Field           | Data Type | Description                                                                                  |
|-----------------|-----------|----------------------------------------------------------------------------------------------|
| **contacts**    | *array*   | Array of contacts                                                                            |
| **type**        | *string*  | The contact type, either: <ul><li>`CUSTOMER`</li><li>`SUPPLIER`</li><li>`OTHER`</li></ul> |
| **id**          | *string*  | The unique identifier for the contact in the platform                                        |
| **email**       | *string*  | Email address of the contact                                                         |
| **name**        | *string*  | Name of the contact                                                     |
| **phone**       | *string*  | Phone number of the contact                                                                   |
| ***addresses*** | *array*   | Array of addresses for the contact                                                           |
| **type**        | *array*   | The address type, either: <ul><li>`BILLING`</li><li>`DELIVERY`</li><li>`OTHER`</li></ul>  |
| **country**     | *array*   | Country of the contact address                                                               |
| **postal_code** | *array*   | Postal code for the contact address                                                          |
| **line1**       | *array*   | Line 1 of the contact address                                                                |
| **line2**       | *array*   | Line 2 of the contact address                                                                |

