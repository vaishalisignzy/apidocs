# ICWAI Search by Firm Number

### &#xD;Introduction

<mark style="color:orange;">**The Institute of Cost and Management Accountants of India**</mark> (**ICMAI**), which was also known as **The Institute of Cost & Works Accountants of India** (**ICWAI**) is the second professional accountancy body in India. It is under the ownership of the Ministry of Corporate Affairs, Government of India. It has been given a prime responsibility by the Ministry of Corporate Affairs of the Government of India to contribute to the cost and management accounting profession at the global level.

### API Usecase

Using ICWAI Firm Search service, the ICWAI number can be used to retrieve the details of the particulars of the individual registered with ICWAI along with the address and organisational details.

**The following information is generated:**

* Entity Name
* Constitution Date
* Firm Address

### How to call the API

You will need to login before sending a firm number request. You are required to pass the access token received from the login call, as an authorization header in the ICWAI request along with firmName.

### API Input Guidelines

Provide the correct **Firm number** issued by ICMAI. It is a 6 digit number.

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for ICWAI search

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
        "memberNumber": "<Firm Number>"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME           | DESCRIPTION                                                                                                                                                                                                               |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                   | This contains the final response parameters.                                                                                                                                                                              |
| result.entityName        | The name of the firm that is being searched.                                                                                                                                                                              |
| result.constitutionDate  | The date of constitution of the firm that is being searched is displayed here.                                                                                                                                            |
| result.address           | The address of the firm that is being searched is shown by this parameter.                                                                                                                                                |
| result.splitAddress      | This parameter distinguishes the various parts of the address of the firm into separate categories like district, state, city, pincode and country. For the country category, acceptable values  is “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine | This parameter displays the first line of the address.                                                                                                                                                                    |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "firmNumber": "<Firm Number>"
    },
    "id": "<Unique User ID>",
    "patronId": "<Unique Patron ID>",
    "type": "firms",
    "result": {
        "entityName": "<Firm Name>",
        "constitutionDate": "02/12/1991",
        "address": "<Firm Address>",
        "splitAddress": {
            "district": [
                "PUNE"
            ],
            "state": [
                [
                    "MAHARASHTRA",
                    "MH"
                ]
            ],
            "city": [
                "PUNE CITY"
            ],
            "pincode": "411004",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "<Firm Address>"
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/6b81a0e554023372560b)
