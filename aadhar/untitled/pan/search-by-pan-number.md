---
description: PAN Fetch
---

# Fetch Details by PAN Number

### Introduction

The Fetch API is used to retrieve or ‘fetch’ certain details from the PAN card like name, Father's Name, Date of Birth for Individual PAN cardholders and name, Date of Issue, and so on for Business PAN holders.

### API Usecase

This API uses just the PAN number of the user and provides the details of that particular user. It helps in auto-generating the details for the user without having to manually provide the information. The Following information is generated:&#x20;

* Name of the PAN holder
* Father's name
* D.O.B

### How to call the API

Before fetching the details via PAN number, you first need to create an Identity object. For best results, please make sure that the image you use fits tightly in camera view and is horizontally aligned. Each image/pdf should be less than 2MB.



### API Input Guidelines

* PAN number in upper/lower case.

### <mark style="color:blue;">Sample CURL Request</mark>

### **Step 1**: Hit Identities API

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters Name | Description                           | Compulsory/Optional |
| --------------- | ------------------------------------- | ------------------- |
| type            | Type of Identity                      | Compulsory          |
| callbackurl     | URL where response will be posted     | Compulsory          |
| images          | Front and Back side Image of Passport | Compulsory          |
{% endtab %}

{% tab title="Sample CURL " %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/identities' \
--header 'Authorization: exjbyOxoHTxq9YpagNDXeAMmQ2n0a8pjY41EZKi02H6BumuuCMQimfutTPIMFgzO' \
--header 'Content-Type: application/json' \
--data-raw '{
    "type": "individualPan",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": []
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| Parameters Name | Description |
| --------------- | ----------- |
| accessToken     |             |
| autoRecognition |             |
| verification    |             |
| forgeryCheck    |             |
| id              |             |
| patronId        |             |
{% endtab %}

{% tab title="Sample Response" %}
```
{
    "type": "individualPan",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [],
    "accessToken": "kue81r5v8bkhyyonpxhinxgssh3mh64k",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "6180c1297157fd10dd4ee890",
    "patronId": "6140962af6d4030eae0496e0"
}
```
{% endtab %}
{% endtabs %}

### ****

### **Step 2:** Hit Snoops API and receives a response

{% tabs %}
{% tab title="Input Parameters" %}
| **PARAMETER  NAME** | **DESCRIPTION**                                 |
| ------------------- | ----------------------------------------------- |
| service             | Type of Signzy service - “identity extraction”  |
| itemId              | Contains the identity item id                   |
| accessToken         | Identity access token                           |
| task                | <p>The type of task performed - “Fetch”<br></p> |
| essentials          | Contains the essential output data              |
{% endtab %}

{% tab title="Sample CURL" %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/snoops' \
--header 'Content-Type: application/json;charset=UTF-8' \
--data-raw '{
      "service":"Identity",
      "itemId":"<Identity-object-id>",
      "task":"fetch",
      "accessToken":"<Identity-access-token>",
      "essentials": {
        "name": "POOJA",
        "number": "DQYPP6888Q",
        "fuzzy": "true"
    }
}'
```
{% endtab %}
{% endtabs %}



### <mark style="color:green;">**Sample API Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| **PARAMETER  NAME**     | **DESCRIPTION**                                                                                            |
| ----------------------- | ---------------------------------------------------------------------------------------------------------- |
| result                  | This holds final result parameters of the response.&#xD;                                                   |
| result.name             | The name of the PAN holder (or organization name for business PAN)                                         |
| result.fatherName       | The father's name of the PAN holder (for individual PAN only)                                              |
| results.dob/dateofIssue | This parameter holds the date of birth (for individual PAN) or the date of issue (in case of business PAN) |
| results.number          | The PAN number of the individual/organization                                                              |
{% endtab %}

{% tab title="API Response" %}
```
{
    "service": "Identity",
    "itemId": "6180c10b7157fd10dd4ee888",
    "task": "fetch",
    "essentials": {
        "name": "POOJA",
        "number": "DQYPP6888Q",
        "fuzzy": "true",
        "instance": {}
    },
    "accessToken": "0me9dkaquqckpp2mssnjz1y74wuy4em",
    "id": "6180c1717157fd10dd4ee893",
    "response": {
        "number": "<PAN Number to be seached>",
        "id": 12684,
        "name": "<Name to be searched for>",
        "fuzzy": "true",
        "instance": {
            "id": "6180c10b7157fd10dd4ee888",
            "callbackUrl": "https://www.w3schools.com"
        },
        "result": {
            "number": "<PAN Number>",
            "name": "<PAN Holder's Name>",
            "fatherName": "<Father's Name>",
            "dob": ""
        }
    }
}
```
{% endtab %}
{% endtabs %}



### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |
|             |                                        |

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/b22b5cd81c706226dfb9)

