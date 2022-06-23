# Voter ID Verification

### Verifying Voter ID details

The user needs to validate the details provided to the API and ensure that the correct image details have been provided to the API. Once retrieved, the API will verify the details against government records to determine the originality of the voter information.

Before going for Verification calls, you first need to create an Identity object. The user details must be unique and the voter ID number (epic Number).along with the name is mandatory.

### Introduction <a href="#introduction" id="introduction"></a>

Verifying Voter ID details with the data with the government for integrity. Once the Voter ID has been manually validated, the API can compare against government records to check for the originality of the details.

### API Usecase <a href="#api-usecase" id="api-usecase"></a>

This API will take input such as EPIC number, Name, State and will verify it as per the data with the Election Commission of India for integrity and respond to the verification request as true/false.

### How to call the API <a href="#how-to-call-the-api" id="how-to-call-the-api"></a>

Before going for Verification calls, you first need to create an Identity object. The user details must be unique and the voter ID number (epic Number).along with the name is mandatory.

### API Input Guidelines <a href="#api-input-guidelines" id="api-input-guidelines"></a>

* EPIC number
* Name of the VOTER
* State to which He/She belongs&#x20;

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

{% tab title="Sample CURL" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/identities' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
    "type": "voterid",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": []
}'​
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
    "type": "voterid",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [],
    "accessToken": "rgffiv2vrfxb7wtgvo3lidf2cjnwspg",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "6180a9627157fd10dd4ee6e5",
    "patronId": "6140962af6d4030eae0496e0"
}
```
{% endtab %}
{% endtabs %}

### ****

### **Step 2:** Hit Snoops API and receives a response

{% tabs %}
{% tab title="Snoops Parameters" %}


| **PARAMETER  NAME** | **DESCRIPTION**                                        |
| ------------------- | ------------------------------------------------------ |
| service             | Type of Signzy service - “identity extraction”         |
| itemId              | Contains the identity item id                          |
| accessToken         | Identity access token                                  |
| task                | <p>The type of task performed - “Verification”<br></p> |
| essentials          | Contains the essential output data                     |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/snoops' \
--header 'Content-Type: application/json;charset=UTF-8' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
    "service": "Identity",
    "itemId": "<ID property from identity obejct creation request>",
    "accessToken": "<Access token from identity object creation>",
    "task": "verification",
    "essentials": {
        "name": "<Name>",
        "epicNumber": "<EPIC number>",
        "state": "<State of Voter>"
    }
}'
​
```
{% endtab %}
{% endtabs %}



### <mark style="color:green;">Sample API Response</mark> <a href="#sample-api-response" id="sample-api-response"></a>

{% tabs %}
{% tab title="Response Parameter" %}
| PARAMETER NAME  | DESCRIPTION                                                                   |
| --------------- | ----------------------------------------------------------------------------- |
| result          | The output of the response                                                    |
| result.verified | Contains the verification status "true/false"                                 |
| result.message  | This parameter displays the verification success/failure message to the user. |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "service": "Identity",
    "itemId": "6147a83ef0e8db4b731802c4",
    "task": "verification",
    "essentials": {
        "name": "suman singh",
        "epicNumber": "SCG3050XXX",
        "state": "West Bengal",
        "instance": {
            "id": "6147a83ef0e8db4b731802c4",
            "callbackUrl": "https://www.w3schools.com"
        }
    },
    "accessToken": "mimr8hl4zt3ifhnwgwx8tfktw6cx5dj4",
    "id": "6147a8a9f0e8db4b731802c7",
    "response": {
        "name": "suman singh",
        "epicNumber": "SCG3050754",
        "state": "WEST BENGAL",
        "instance": {
            "id": "6147a83ef0e8db4b731802c4",
            "callbackUrl": "https://www.w3schools.com"
        },
        "id": 319,
        "result": {
            "verification": true,
            "message": "Verification completed with positive result"
        }
    }
}

```
{% endtab %}
{% endtabs %}

### **** <a href="#http-response-codes" id="http-response-codes"></a>

### **HTTP Response Codes** <a href="#http-response-codes" id="http-response-codes"></a>

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |

### &#x20; <a href="#undefined-1" id="undefined-1"></a>



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/38fdccbf725bd15f0db5)

**Valid State and Union Territory List**

1 ) Andaman and Nicobar Islands\
2 ) Andhra Pradesh\
3 ) Arunachal Pradesh\
4 ) Assam\
5 ) Bihar\
6 ) Chandigarh\
7 ) Chhattisgarh\
8 ) Dadra and Nagar\
9 ) Diu-Daman\
10 ) Delhi\
11 ) Goa\
12 ) Gujarat\
13 ) Haryana\
14 ) HimachalPradesh\
15 ) JammuKashmir\
16 ) Jharkhand\
17 ) Karnataka\
18 ) Kerala\
19 ) Lakshadweep\
20 ) Madhya Pradesh\
21 ) Maharashtra\
22 ) Manipur\
23 ) Meghalaya\
24 ) Mizoram\
25 ) Nagaland\
26 ) Odisha\
27 ) Puducherry\
28 ) Punjab\
29 ) Rajasthan\
30 ) Sikkim\
31 ) TamilNadu\
32 ) Telangana\
33 ) Tripura\
34 ) Uttar Pradesh\
35 ) Uttarakhand\
36 ) West Bengal

**Verification Result Scenarios**

1. Name Verification successful - When Epic Number and Name perfectly matches with the Government recorded data.
2. Verification is complete with a negative result. - when Epic Number and Name does not match with the Government recorded data.
3. Provided Epic Number not found
   * Provided Epic Number not found.
   * The provided Epic Number is not updated in the government database.
   * The Underlying government data source is having some issues at this moment.
