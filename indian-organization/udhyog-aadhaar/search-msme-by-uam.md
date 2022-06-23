# Search MSME by UAN

### &#x20;&#xD;Introduction

Udyog Aadhar Number (UAN) is a 12 digit Unique Identification Number provided by the Ministry of Micro, Small and Medium Enterprises, Government of India for small and medium enterprises in India. It is also known as Aadhar for Business.

### API Usecase

The UAN Search API by Signzy uses this unique identification number to retrieve the organisational details of the business and owner/s to which the UAN has been assigned.

**The following information is generated about the Business dealer:**

* UAN Number
* Name of Enterprise
* Major Activity
* Social Activity
* Enterprise Type
* Date of Commencement
* DIC Name
* State
* Applied Date
* Modified Date
* Status

### How to call the API

You will need to login before sending <mark style="color:orange;">UAN search request.</mark> You are required to pass the access token received from the login call, as an authorization header in the UAN search request along with Udhyog Aadhaar Number.



### API Input Guidelines

Provide correct **12-digit unique Alphanumeric number**, that's allotted by  **Ministry of Micro, Small and Medium Enterprises**, Government of India



### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for UAN search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization        | Required | String | Access Token              |
| -------------------- | -------- | ------ | ------------------------- |
| Content-Type         | Required | String | Application/JSON          |
| essentials.uanNumber | Required | String | UAN number issued by MSME |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/udyogaadhaars' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "type": "uam",
    "essentials": {
        "uamNumber": "<UAN Number>"
    }
}'
```
{% endtab %}
{% endtabs %}

<mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters " %}
| PARAMETER NAME            | DESCRIPTION                                                              |
| ------------------------- | ------------------------------------------------------------------------ |
| result                    | This contains the final response parameters.                             |
| result.nameofEnterprise   | The name of the enterprise to which UAN is assigned.                     |
| result.dateofCommencement | The date of commencement of the enterprise to which the UAN is assigned. |
| result.state              | The state to which the enterprise belongs.                               |
| result.dicName            | The district name to which the enterprise belongs to.                    |
| result.status             | The current status of the enterprise to which UAN belongs to.            |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "uamNumber": "<UAN Number>"
    },
    "id": "<Access Token from Login request>",
    "patronId": "<Patron ID>",
    "type": "uam",
    "result": {
        "uamNumber": "MH26E0014851",
        "nameofEnterprise": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
        "majorActivity": "SERVICES",
        "socialCategory": "GENERAL",
        "enterpriseType": "SMALL",
        "dateofCommencement": "03/11/2015",
        "dicName": "PUNE",
        "state": "MAHARASHTRA",
        "appliedDate": "15/11/2016",
        "modifiedDate": "N/A",
        "validTillDate": "31/12/2021.",
        "nic2Digit": "63-INFORMATION SERVICE ACTIVITIES",
        "nic4Digit": "6399-OTHER INFORMATION SERVICE ACTIVITIES N.E.C.",
        "nic5DigitCode": "63999-OTHER INFORMATION SERVICE ACTIVITIES N.E.C.",
        "status": "ACTIVE"
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
|             |                                        |



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/947f2da641b6531b9546)
