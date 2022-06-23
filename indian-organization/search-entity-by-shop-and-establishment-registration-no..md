# Search Entity by Shop & Establishment Registration No.

### &#xD;Introduction

Every shop/establishment that conducts business within the country of India has to be registered under the Government of India as a business establishment. For this purpose, the Shops and Organisational certificate is issued to the owner/s along with a unique registration number.

### API Usecase

Using this registration number and the state where the business is located as input, the Search Orgs for Shops and Establishment Certificate API retrieves the details like the name of the business, address etc.&#x20;

**The following information is generated:**

* Registration Details
* Date of Commnecement
* Address

### How to call the API

You will need to login before sending SnEC request. You are required to pass the access token received from the login call, as an authorization header in the SnEC request along with registrationNumber. The State is also a mandatory field here.

### API Input Guidelines

Provide the following details:

* Registration Number
* State of registration

### <mark style="color:blue;">Sample CURL Request</mark>

Search by SnE Registration Number

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization                 | Required | String | Access Token        |
| ----------------------------- | -------- | ------ | ------------------- |
| Content-Type                  | Required | String | Application/JSON    |
| essentials.registrationNumber | Required | String | Registration Number |
| essentials.state              | Required | String | Registered State    |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<Patron ID>/snecs' \
--header 'Authorization: <Auth>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "essentials": {
        "registrationNumber": "<Registration Number>",
        "state": "West Bengal"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME                     | DESCRIPTION                                                                                                                                                                                                                                                   |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                                 | The access token that was received during login request.                                                                                                                                                                                                      |
| patronId                           | The userId that was received during login request.                                                                                                                                                                                                            |
| result                             | The final response parameters to be displayed for output.                                                                                                                                                                                                     |
| result.summary                     | This parameter contains the details of the name and address of the shop/establishment which is being searched.                                                                                                                                                |
| summary.name                       | The name of the owner of the shop/establishment.                                                                                                                                                                                                              |
| summary.dateOfCommencement         | The date of commencement of registration for the given shop/establishment.                                                                                                                                                                                    |
| summary.address                    | The registered address of the owner of the shop/establishment.                                                                                                                                                                                                |
| summary.splitAddress               | This parameter distinguishes the various parts of the registered address of the shop/establishment owner into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.&#xD; |
| splitAddress.addressLine           | The first line of the registered address of the shop/establishment.                                                                                                                                                                                           |
| result.detailed                    | This parameter contains details about the registration of the shop/establishment.                                                                                                                                                                             |
| detailed.registrationDetails       | The registration details of the shop/establishment like name, registration number and detailed address are contained here.                                                                                                                                    |
| registrationDetails.registrationNo | The registration number of the shop/establishment.                                                                                                                                                                                                            |
| registrationDetails.date           | The date of the registration of the shop/establishment.                                                                                                                                                                                                       |
| registrationDetails.validUpto      | The validity date of the registration is displayed here.                                                                                                                                                                                                      |
| detailed.name                      | The name of the shop/establishment.                                                                                                                                                                                                                           |
| detailed.dateOfCommencement        | The date of commencement of the registration.                                                                                                                                                                                                                 |
| detailed.address                   | The address of the shop/establishment.                                                                                                                                                                                                                        |
| detailed.district                  | The district name of the shop/establishment.                                                                                                                                                                                                                  |
| detailed.pincode                   | The pincode of the registered address of the shop/establishment.                                                                                                                                                                                              |
| detailed.splitAddress              | This parameter distinguishes the various parts of the address of the shop/establishment into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.&#xD;                  |
| splitAddress.addressLine           | The first line of the address is displayed here.                                                                                                                                                                                                              |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "registrationNumber": "<Registration Number>",
        "state": "West Bengal"
    },
    "id": "<Access Token received during Login>",
    "patronId": "<Patron ID>",
    "result": {
        "registrationDetails": {
            "registrationNo": "KL04212N2016000001",
            "date": "09/11/2016",
            "validUpto": "08/11/2019"
        },
        "dateOfCommencement": "09/11/2016",
        "address": "44/A M.B. ROAD KOL-60, Ward No - 129, BOROUGH - XIV, KOLKATA MUNICIPAL CORPORATION, P. S. - TARATOLA, P. O. - PARNASREE PALLY S.O KOLKATA 700060",
        "splitAddress": {
            "district": [
                "KOLKATA"
            ],
            "state": [
                [
                    "WEST BENGAL",
                    "WB"
                ]
            ],
            "city": [
                "KOLKATA"
            ],
            "pincode": "700060",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "44/A M.B.ROAD KOL-60,WARD NO 129,BOROUGH XIV,MUNICIPAL CORPORATION,P.S.TARATOLA,P.O.PARNASREE PALLY S.O"
        },
        "district": "KOLKATA",
        "name": "A M SECURITY SERVICES PVT LTD",
        "pincode": "700060",
        "dateOfCommencment": "09/11/2016",
        "summary": {
            "registrationNumber": "KL04212N2016000001",
            "name": "A M SECURITY SERVICES PVT LTD",
            "status": "",
            "dateOfCommencement": "09/11/2016",
            "address": "44/A M.B. ROAD KOL-60, WARD NO - 129, BOROUGH - XIV, KOLKATA MUNICIPAL CORPORATION, P. S. - TARATOLA, P. O. - PARNASREE PALLY S.O KOLKATA 700060",
            "splitAddress": {
                "district": [
                    "KOLKATA"
                ],
                "state": [
                    [
                        "WEST BENGAL",
                        "WB"
                    ]
                ],
                "city": [
                    "KOLKATA"
                ],
                "pincode": "700060",
                "country": [
                    "IN",
                    "IND",
                    "INDIA"
                ],
                "addressLine": "44/A M.B.ROAD KOL-60,WARD NO 129,BOROUGH XIV,MUNICIPAL CORPORATION,P.S.TARATOLA,P.O.PARNASREE PALLY S.O"
            }
        },
        "detailed": {
            "registrationDetails": {
                "registrationNo": "KL04212N2016000001",
                "date": "09/11/2016",
                "validUpto": "08/11/2019"
            },
            "dateOfCommencement": "09/11/2016",
            "address": "44/A M.B. ROAD KOL-60, Ward No - 129, BOROUGH - XIV, KOLKATA MUNICIPAL CORPORATION, P. S. - TARATOLA, P. O. - PARNASREE PALLY S.O KOLKATA 700060",
            "splitAddress": {
                "district": [
                    "KOLKATA"
                ],
                "state": [
                    [
                        "WEST BENGAL",
                        "WB"
                    ]
                ],
                "city": [
                    "KOLKATA"
                ],
                "pincode": "700060",
                "country": [
                    "IN",
                    "IND",
                    "INDIA"
                ],
                "addressLine": "44/A M.B.ROAD KOL-60,WARD NO 129,BOROUGH XIV,MUNICIPAL CORPORATION,P.S.TARATOLA,P.O.PARNASREE PALLY S.O"
            },
            "district": "KOLKATA",
            "name": "A M SECURITY SERVICES PVT LTD",
            "pincode": "700060"
        }
    }
}
```
{% endtab %}
{% endtabs %}

### ****

### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/c613c319ce8ce6f00aaa)

**Valid State List**

1\) West Bengal\
2\) Telangana\
3\) Delhi\
4\) Haryana\
5\) Rajasthan\
6\) Uttar Pradesh\
7\) Maharashtra ( For production access contact : sales@signzy.com )\
