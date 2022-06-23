# Search Employee State Insurance Corp. (ESIC) by PAN No.

ESIC Search by PAN





### Introduction

<mark style="color:purple;">Employee's State Insurance Corporation</mark> (abbreviated as ESIC) is a self-financing social security and health insurance scheme for Indian workers. The ESIC Search by PAN is similar to EPFO UAN search and makes use of the PAN number to retrieve the establishment details for the company/LLP that is registered under the ESIC. &#x20;

### API Usecase

Using the unique COA Reg Number as input, this Signzy API can retrieve the details and particulars of the registered architect.&#x20;

**The following information is generated:**

* PAN Number
* Registered Offices
* Establishment Name
* Registered office address
* Registered office LIN

### How to call the API

You will need to login before sending Search by PAN ESIC request. You are required to pass the access token received from the login call, as authorization header in the Search by PAN ESIC request along with PAN .



### API Input Guidelines

Provide the correct **PAN Number**&#x20;

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for Search by PAN ESIC request

{% tabs %}
{% tab title="Input Parameters" %}
| task                          | Required | String | Search by PAN                 |
| ----------------------------- | -------- | ------ | ----------------------------- |
| essentials.registrationNumber | Required | String | Architect registration number |
{% endtab %}

{% tab title="CURL Request" %}
```
 {
    "task" :"searchByPan",
    "essentials":{
      "panNumber": "..pan-number-to-search-for.."
    }
  }
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME                      | DESCRIPTION                                                                                                                                                                                                                       |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                              | The final response parameters are contained here.                                                                                                                                                                                 |
| result.panNumber                    | The PAN number of the employee for whom information is being searched.                                                                                                                                                            |
| result.registeredOffices            | The details of the registered offices at which employee works or worked.                                                                                                                                                          |
| registeredOffices.establishmentName | The name of the organisation where the employee was registered.                                                                                                                                                                   |
| registeredOffices.address           | The address of the establishment to which the employee was registered.                                                                                                                                                            |
| registeredOffices.lin               | The unique identification number for the establishment.                                                                                                                                                                           |
| registeredOffices.splitAddress      | This parameter distinguishes the various parts of the address of the establishment into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine            | This parameter displays the first line of the registered address.                                                                                                                                                                 |
{% endtab %}

{% tab title="Response" %}
```
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/ae46f4cd4621c0c0ffe3)
