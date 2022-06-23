---
description: Search a company by Udhyog Aadhaar Number and Aadhaar Number
---

# Search MSME by UAN & UID (404)

### &#xD;Introduction

Udyog Aadhar Number (UAN) is a 12 digit Unique Identification Number provided by the Ministry of Micro, Small and Medium Enterprises, Government of India for small and medium enterprises in India. It is also known as Aadhar for Business.

### API Usecase

This is an advanced Search method as compared to the UAN Search API. The UAN and UID Search API takes the UAN of the business as well as the Aadhar Number of the owner to uniquely identify and retrieve the organisational details like name of business, date of commencement, address etc.

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
| Authorization            | Required | String | Access Token              |
| ------------------------ | -------- | ------ | ------------------------- |
| Content-Type             | Required | String | Application/JSON          |
| essentials.uanNumber     | Required | String | UAN number issued by MSME |
| essentials.aadhaarNumber | Required | String | Aadhaar Number            |
{% endtab %}

{% tab title="CURL Request" %}
```
  {
   "type":"acknowledgement",
      "essentials":{
     "uamNumber": "..uam number...",
      "aadhaarNumber": "...aadhaar number...."
     }
  }
```
{% endtab %}
{% endtabs %}

<mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters " %}
| PARAMETER NAME            | DESCRIPTION                                                                                                                                                                                                                     |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                    | This contains the final response parameters.                                                                                                                                                                                    |
| result.nameofEnterprise   | The name of the enterprise to which UAN is assigned.                                                                                                                                                                            |
| result.dateofCommencement | The date of commencement of the enterprise to which the UAN is assigned.                                                                                                                                                        |
| result.address            | The address of the enterprise as registered with the UAN.                                                                                                                                                                       |
| result.status             | The current status of the enterprise to which UAN belongs to.                                                                                                                                                                   |
| result.splitAddress       | This parameter distinguishes the various parts of the address of the enterprise into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine  | The first line of the address is displayed here.                                                                                                                                                                                |
{% endtab %}

{% tab title="Response" %}
```
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
