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
    "results": [
        {
            "contact": {
                "id": "295c0eb6-7844-4ee7-a2ed-6c1a69fa9424",
                "company_name": "Lifestyle Design",
                "contact_name": "James",
                "email": "j.dg@example.com",
                "first_name": "James",
                "last_name": "De Grasse",
                "phone": "(021) 120 00000",
                "type": "customer and supplier",
                "addresses": [
                    {
                        "city": "Auckland",
                        "country": "NZ",
                        "line1": "12 Scott Road",
                        "line2": "Onehunga"
                    },
                    {
                        "city": "Auckland",
                        "country": "NZ",
                        "line1": "28 Esplanade Street",
                        "line2": "Papakura"
                    }
                ],
            }
        }
    ]
}
```
<span class="api api-get"></span> <code>/companies/{company}/connections/{connection}/contacts</code>

### Contact

Below is the content of the `contact` object.

| Field            | Data Type | Description                                                                                    |
| :----------------| :---------| :--------------------------------------------------------------------------------------------- |
| **type**         | *string*  | The contact type, either: <ul><li>`customer`</li><li>`customer and supplier`</li></ul>         |
| **id**           | *string*  | The unique identifier for the contact in the platform                                          |
| **first_name**   | *string*  | Name of the contact                                                                            |
| **last_name**    | *string*  | Name of the contact                                                                            |
| **company_name** | *string*  | Website of the contact                                                                         |
| **phone**        | *string*  | Phone number of the contact                                                                    |
| **email**        | *string*  | Email address of the contact                                                                   |
| **website**      | *string*  | Website of the contact                                                                         |
| **vatin**        | *string*  | VAT number of the contact                                                                      |

### address

| Field                   | Data Type   | Description                         |
| :---------------------- | :---------- | :---------------------------------- |
| **country**             | *string*    | Country                             |
| **city**                | *string*    | City                                |
| **line1**               | *string*    | Address, line 1                     |
| **line2**               | *string*    | Address, line 2                     |
| **postal_code**         | *string*    | Postal code                         |
| **type**                | *string*    | Type of the address                 |
