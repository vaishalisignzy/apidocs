# Search Company by ICSI

### Introduction

<mark style="color:orange;">The Institute of Company Secretaries of India</mark> is a statutory professional body in India with the objective of promoting, regulating and developing the profession of company secretaries in India. _There can be two types of members_ - ACS (Associate Member) or FCS(Fellow Member). Each member is issued with a unique ICSI member number.

### API Usecase

The Signzy Search companies by ICSI service uses the type of member along with member number as input to generate the details and particulars of the registered individual/member of the ICSI.

**The following information is generated:**

* City
* Organisation Name
* Address of Member

### How to call the API

You will need to login before sending a member number request. You are required to pass the access token received from the login call, as an authorization header in the ICSI request along with Member Number and Member Type.

### API Input Guidelines

Provide the correct **Member number** issued by ICSI. It is a 5 digit number.

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for ICSI based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization           | Required | String | Access Token                           |
| ----------------------- | -------- | ------ | -------------------------------------- |
| Content-Type            | Required | String | Application/JSON                       |
| task                    | Required | String | Registration number search             |
| essentials.memberNumber | Required | String | Membership number                      |
| essentials.Type         | Required | String | Membership type could be of ACS or FCS |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/icsis' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "essentials": {
        "memberNumber": "<Membership Number>",
        "memberType": "ACS"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME           | DESCRIPTION                                                                                                                                                                                                                                    |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                   | This holds the final response parameters and displays the final output.                                                                                                                                                                        |
| result.organization      | The name of the organization that is being searched.                                                                                                                                                                                           |
| result.city              | The name of the city where the organization is located.                                                                                                                                                                                        |
| result.address           | The address of the organization is displayed here.                                                                                                                                                                                             |
| result.type              | This parameter displays the membership type. There are usually two types - ACS, which stands for Associate Company Secretary and FCS, which stands for Fellow Company Secretary.                                                               |
| result.splitAddress      | <p>This parameter distinguishes the various parts of the address of the ICSI member into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA”.</p><p></p> |
| splitAddress.addressLine | The first line of the address is displayed here.                                                                                                                                                                                               |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "memberNumber": "<Membership Number>",
        "memberType": "<Type of Member ACS or FCS>"
    },
    "id": "6188252c7157fd10dd4f2a58",
    "patronId": "<Patron ID>",
    "result": {
        "city": "RAJPURA",
        "organization": "M/S AMBER ENTERPRISES INDIA PVT LTD.",
        "address": "C-1,PHASE-2,FOCAL POINT RAJPURA",
        "type": "ACS",
        "splitAddress": {
            "district": [
                "PATHANKOT"
            ],
            "state": [
                [
                    "PUNJAB",
                    "PB"
                ]
            ],
            "city": [
                "FOCAL POINT"
            ],
            "pincode": "143525",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "C-1,PHASE-2,RAJPURA"
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/5144b530bb3b326c5223)

\
