# ICWAI Search by Member Number

### Introduction

<mark style="color:orange;">**The Institute of Cost and Management Accountants of India**</mark> (**ICMAI**), which was also known as **The Institute of Cost & Works Accountants of India** (**ICWAI**) is the second professional accountancy body in India. It is under the ownership of Ministry of Corporate Affairs, Government of India. It has been given a prime responsibility by the Ministry of Corporate Affairs of the Government of India to contribute to the cost and management accounting profession at global level.

### API Usecase

Similar to the firm member search API, the member search API can be used to retrieve further details of the registered member using the ICWAI number.

**The following information is generated:**

* Membership Status
* Members Name
* Members Address

### How to call the API

You will need to login before sending a member number request. You are required to pass the access token received from the login call, as authorization header in the ICWAI request along with memberName.

### API Input Guidelines

Provide the correct **Firm number** issued by ICMAI. It is a 6 digit number.

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for ICWAI search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization           | Required | String | Access Token                  |
| ----------------------- | -------- | ------ | ----------------------------- |
| Content-Type            | Required | String | Application/JSON              |
| essentials.memberNumber | Required | String | Architect registration number |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/icwais' \
--header 'Authorization: <Auth>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "type": "members",
    "essentials": {
        "memberNumber": "<Membership Number>"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME               | DESCRIPTION                                                                                                                                                                                                                               |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type                         | The type of task performed - member search                                                                                                                                                                                                |
| essentials                   | This parameter contains the essential data for output.                                                                                                                                                                                    |
| essentials.memberNumber      | The member number which is being searched is displayed here.                                                                                                                                                                              |
| id                           | This parameter contains the access token that is returned during login request.                                                                                                                                                           |
| patronId                     | This parameter is returned as userId parameter of login request.                                                                                                                                                                          |
| result                       | This parameter contains the final response parameters.                                                                                                                                                                                    |
| result.entityName            | The name of the member is displayed here.                                                                                                                                                                                                 |
| result.membershipDate        | The membership date for the member is displayed here.                                                                                                                                                                                     |
| result.addressdetails1       | This parameter displays the address details of the first registered address.                                                                                                                                                              |
| addressdetails1.details      | This parameter displays the details about the type of address.                                                                                                                                                                            |
| addressdetails1.address      | The address of the member is displayed here.                                                                                                                                                                                              |
| addressdetails1.splitAddress | <p>This parameter distinguishes the various parts of the address of the member into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA”.</p><p></p> |
| splitAddress.addressLine     | The first line of the address is displayed here.                                                                                                                                                                                          |
| result.addressdetails2       | This parameter displays the address details of the second registered address.                                                                                                                                                             |
| addressdetails2.details      | This parameter displays the details about the type of address.                                                                                                                                                                            |
| addressdetails2.address      | The address of the member is displayed here.                                                                                                                                                                                              |
| addressdetails2.splitAddress | This parameter distinguishes the various parts of the address of the member into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA”.&#xD;           |
| splitAddress.addressLine     | The first line of the address is displayed here.                                                                                                                                                                                          |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "memberNumber": "<Membership Number>"
    },
    "id": "<ID returned during login request>",
    "patronId": "<Patron ID>",
    "type": "members",
    "result": {
        "entityName": "<Entity Name>",
        "memberName": "<Member's Name>",
        "membershipDate": "<Date of membership>",
        "addressDetails1": {
            "details": "D Address Details",
            "address": "<Registered Address of Member>",
            "splitAddress": {
                "district": [
                    "MUMBAI"
                ],
                "state": [
                    [
                        "MAHARASHTRA",
                        "MH"
                    ]
                ],
                "city": [
                    "MUMBAI"
                ],
                "pincode": "400010",
                "country": [
                    "IN",
                    "IND",
                    "INDIA"
                ],
                "addressLine": "FLAT NO.4,ALIABAD BUILDING AGAHALL,NESBIT ROAD MAZGOAN"
            }
        },
        "addressDetails2": {
            "details": "L Address Details",
            "address": "FLAT NO.4,ALIABAD BUILDING AGAHALL,NESBIT ROAD MAZGOAN, MUMBAI, MAHARASHTRA, 400010",
            "splitAddress": {
                "district": [
                    "MUMBAI"
                ],
                "state": [
                    [
                        "MAHARASHTRA",
                        "MH"
                    ]
                ],
                "city": [
                    "MUMBAI"
                ],
                "pincode": "400010",
                "country": [
                    "IN",
                    "IND",
                    "INDIA"
                ],
                "addressLine": "FLAT NO.4,ALIABAD BUILDING AGAHALL,NESBIT ROAD MAZGOAN"
            }
        }
    }
}
```
{% endtab %}
{% endtabs %}

### ****

### **HTTP Response Codes**

****

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/41d72985ca290482e6b4)
