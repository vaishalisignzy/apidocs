# PAN Verification

### Introduction

The PAN details must be manually validated by the user before sending them to the SIGNZY verification service. Upon receiving the details, they are cross-checked against government records to verify the authenticity of the details provided by the user. This is the basic verification service where only the name and PAN number will be verified.

### API Usecase <a href="#api-usecase" id="api-usecase"></a>

This API will take input such Name on the PAN card and PAN number then it will verify it as per the data with the Indian Government for integrity and **respond to the verification request as true/false.**

### How to call the API <a href="#how-to-call-the-api" id="how-to-call-the-api"></a>

Before going for Verification calls, you first need to create an Identity object. The user details must be unique and the PAN Number with the name is mandatory.

### API Input Guidelines <a href="#api-input-guidelines" id="api-input-guidelines"></a>

* Name of PAN card holder
* PAN number

### <mark style="color:blue;">Sample cURL Request</mark> <a href="#sample-curl-request" id="sample-curl-request"></a>

### **Step 1**: Hit Identities API

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters Name | Description                           | Compulsory/Optional |
| --------------- | ------------------------------------- | ------------------- |
| type            | Type of Identity                      | Compulsory          |
| callbackurl     | URL where response will be posted     | Compulsory          |
| images          | Front and Back side Image of Passport | Compulsory          |
{% endtab %}

{% tab title="CURL Request" %}
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

<mark style="color:green;">**Response**</mark>

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
    "accessToken": "zo4aoi4y3xmm829k54xuj23u6irojmhs",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "6180c4867157fd10dd4ee8d9",
    "patronId": "6140962af6d4030eae0496e0"
}
```
{% endtab %}
{% endtabs %}

### **Step 2:** Hit Snoops API and receives <mark style="color:green;">****</mark>** a** response

{% tabs %}
{% tab title="Input Parameters" %}


| **PARAMETER  NAME** | **DESCRIPTION**                                             |
| ------------------- | ----------------------------------------------------------- |
| service             | Type of Signzy service - “identity extraction”              |
| itemId              | Contains the identity item id                               |
| accessToken         | Identity access token                                       |
| task                | <p>The type of task performed - “Auto Verification”<br></p> |
| essentials          | Contains the essential output data                          |
{% endtab %}

{% tab title="Sample CURL" %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/snoops' \
--header 'Content-Type: application/json;charset=UTF-8' \
--data-raw '{
      "service":"Identity",
      "itemId":"<Identity-object-id>",
      "task":"verification",
      "accessToken":"<Identity-access-token>",
      "essentials":{
        "number":"<PAN-as-mentioned-on-the-card>",
        "name":"<Name-corresponding-to-the-given-pan>",
        "fuzzy":"true/false"
    }
}'
```
{% endtab %}
{% endtabs %}



### <mark style="color:green;">Sample API Response and Response Parameters</mark> <a href="#sample-api-response" id="sample-api-response"></a>

{% tabs %}
{% tab title="Response Parameter" %}
| PARAMETER NAME      | DESCRIPTION                                                                                |
| ------------------- | ------------------------------------------------------------------------------------------ |
| result              | The output of the response                                                                 |
| result.verified     | Contains the verification status "true/false"                                              |
| result.message      | This parameter displays the verification success/failure message to the user.              |
| result.upstreamName | This parameter checks the details of the PAN against the existing records in the database. |
{% endtab %}

{% tab title="API Response" %}
```
{
    "service": "Identity",
    "itemId": "6180c7ee7157fd10dd4ee901",
    "task": "verification",
    "essentials": {
        "name": "POOJA",
        "number": "DQYPP6888Q",
        "fuzzy": "true",
        "instance": {}
    },
    "accessToken": "6cyrnwj6mgm8h3v5oesir7mp0i1enzn3t",
    "id": "6180c8117157fd10dd4ee904",
    "response": {
        "name": "POOJA",
        "number": "DQYPP6888Q",
        "fuzzy": "true",
        "id": 6892,
        "instance": {
            "id": "6180c7ee7157fd10dd4ee901",
            "callbackUrl": "https://www.w3schools.com"
        },
        "result": {
            "verified": true,
            "message": "Verification completed with positive result",
            "upstreamName": "POOJA"
        }
    }
}
```
{% endtab %}
{% endtabs %}

### **HTTP Response Codes** <a href="#http-response-codes" id="http-response-codes"></a>

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |

### &#x20;&#xD;

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/9921ba16b42ea8d7dbe7)

### Verification Result Scenarios

1. Verification completed with positive result. - When PAN Number and Name perfectly matches with the Government recorded data.
2. Verification completed with negative result. - when PAN Number and Name does not match with the Government recorded data.
3. PAN not found.
   * The PAN Number is wrong.
   * The PAN Number is not found in our database.

**Name Verification Result Scenarios**:

The below mentioned name matching scenarios are valid for fuzzy name checks for PAN.

Help & support

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:

support@signzy.com

