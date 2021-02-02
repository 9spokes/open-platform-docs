## Contacts

A contact is a person or organisation that associated with your business. 

> Below is a sample document

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

### Data schema

| Field           | Data Type | Description                                                                                  |
|-----------------|-----------|----------------------------------------------------------------------------------------------|
| **contacts**    | *array*   | Array of contacts                                                                            |
| **type**        | *string*  | Type of the contact, either: <ul><li>`CUSTOMER`</li><li>`SUPPLIER`</li><li>`OTHER`</li></ul> |
| **id**          | *string*  | The unique identifier for the contact in the platform                                        |
| **email**       | *string*  | Account number for the bank account                                                          |
| **name**        | *string*  | Name of the bank account in the platform                                                     |
| **phone**       | *string*  | Status of the bank account                                                                   |
| ***addresses*** | *array*   | Array of addresses for the contact                                                           |
| **type**        | *array*   | Type of the address, either: <ul><li>`BILLING`</li><li>`DELIVERY`</li><li>`OTHER`</li></ul>  |
| **country**     | *array*   | Country of the contact address                                                               |
| **postal_code** | *array*   | Postal code for the contact address                                                          |
| **line1**       | *array*   | Line 1 of the contact address                                                                |
| **line1**       | *array*   | Line 2 of the contact address                                                                |



