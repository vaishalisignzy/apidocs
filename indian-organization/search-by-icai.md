# Search by ICAI

### &#xD;Introduction

The <mark style="color:orange;">Institute of Chartered Accountants of India</mark> (ICAI) is the national professional accounting body of India.Similar to the COA as we have previously seen, the ICAI is the only licensing cum regulating body of the financial audit and accountancy profession in India. &#x20;

### API Usecase

Using the ICAI members number as input, this Signzy API retrieves the details and particulars of the accountant/individual who is registered under the ICAI.

**The following information is generated:**

* Membership Status
* Members Name
* Status
* Members Address

### How to call the API

You will need to login before sending member number request. You are required to pass the access token received from the login call, as authorization header in the ICAI request along with Member Number.



### API Input Guidelines

Provide the correct **Membership Number of Chartered Accountants**&#x20;



### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for ICAI based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization                 | Required | String | Access Token                  |
| ----------------------------- | -------- | ------ | ----------------------------- |
| Content-Type                  | Required | String | Application/JSON              |
| task                          | Required | String | Registration number search    |
| essentials.registrationNumber | Required | String | Architect registration number |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<Patron ID>/icais' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
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
| PARAMETER NAME          | DESCRIPTION                                                                                                                                                                                                                     |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| essentials              | This parameter contains the essential output parameters.                                                                                                                                                                        |
| essentials.memberNumber | The member number of the ICAI being searched is shown here.                                                                                                                                                                     |
| Id                      | The access token that is received during login request.                                                                                                                                                                         |
| patronId                | This parameter is returned as userId parameter of login request.                                                                                                                                                                |
| result                  | This contains the final response parameters.                                                                                                                                                                                    |
| result.status           | The status of the request is shown here.                                                                                                                                                                                        |
| result.name             | The name of the member of ICAI is shown here.                                                                                                                                                                                   |
| result.address          | The address of the member of ICAI is shown here.                                                                                                                                                                                |
| result.splitAddress     | This parameter distinguishes the various parts of the address of the ICAI member into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA”. |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "memberNumber": "504036"
    },
    "id": "61821adf7157fd10dd4f018a",
    "patronId": "6140962af6d4030eae0496e0",
    "result": {
        "status": "ACTIVE",
        "name": "AMOD  KUMAR",
        "address": "C-34 NAWADA HOUSING COMPLEX KAKROLA MORE/ DWARKA MORE NEW DELHI - 110059, DELHI, INDIA",
        "splitAddress": {
            "district": [
                "WEST DELHI"
            ],
            "state": [
                [
                    "DELHI",
                    "DL"
                ]
            ],
            "city": [
                "DELHI"
            ],
            "pincode": "110059",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "C-34 NAWADA HOUSING COMPLEX KAKROLA MORE/DWARKA MORE NEW"
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



