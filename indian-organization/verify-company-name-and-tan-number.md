# Verify Company Name & TAN Number

### Introduction

TAN or <mark style="color:orange;">Tax Deduction and Collection Account Number</mark> is a 10 digit alphanumeric number required to be obtained by all persons who are responsible for deducting or collecting tax. The Search by TAN API makes use of this number to retrieve the name, address and other details of the registered user.

### API Usecase

The Company Name and TAN Number service use the TAN number and Name of the organization <mark style="color:purple;"></mark> to identify and retrieve the unique details and particulars of the Organisation

### How to call the API

You will need to login before sending a TAN number request. You are required to pass the access token received from the login call, as authorization header in the TAN request along with `companyName` , `tan`

### API Input Guidelines

Provide the following details:

* Company Name
* TAN Number

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for TAN based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization          | Required | String | Access Token               |
| ---------------------- | -------- | ------ | -------------------------- |
| Content-Type           | Required | String | Application/JSON           |
| task                   | Required | String | Registration number search |
| essentials.companyName | Required | String | Name Of the Company        |
| essentials.TAN         | Required | String | TAN number of the company  |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/tans' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "essentials": {
        "companyName": "Allahabad bank",
        "tan": "AGRA10865B"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME         | DESCRIPTION                                                                                                         |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------- |
| essentials             | This parameter contains the essential data for output.                                                              |
| essentials.companyName | The name of the company that is registered with the TAN.                                                            |
| essentials.tan         | The Tax Deduction and Collection Account Number is displayed here.                                                  |
| id                     | This contains the access token received during login request.                                                       |
| patronId               | This parameter is returned as userId parameter of login request.                                                    |
| result                 | This parameter displays the final response parameters.                                                              |
| result.verified        | This parameter displays the verification status as true/false.                                                      |
| result.message         | This parameter displays the message whether the verification has been completed with a positive or negative result. |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "companyName": "<Company Name>",
        "tan": "<TAN Number of the Company>"
    },
    "id": "<Request ID>",
    "patronId": "<Patron ID>",
    "result": {
        "verified": < true/ false>,
        "message": "<Verification completed with positive/ negative result>"
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/821db5a2d0f5c0c56361)
