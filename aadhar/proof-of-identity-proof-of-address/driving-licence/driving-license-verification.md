# Driving License Verification

### Introduction

Verifying Driving licence details with the data with the government for integrity. Once the driving licence has been manually validated, the API can compare against government records to check for the originality of the details.

### API Usecase

This API will take input such as DL number, D.O.B, Date of issue of DL and will verify it as per the data with the Ministry of road transport for integrity and respond to the verificatiton request as true/false.

### How to call the API

Before going for Verification calls, you first need to create an Identity object. The DL number, D.O.B along with the Issue date of DL is mandatory.

### API Input Guidelines

* Licence number
* Date of birth in (dd/mm/yy)
* Date of issue of licence (dd/mm/yy)

### Sample cURL Request

### **Step 1**: Hit Identities API

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters Name | Description                                  | Compulsory/Optional |
| --------------- | -------------------------------------------- | ------------------- |
| type            | Type of Identity                             | Compulsory          |
| email           |                                              |                     |
| callbackurl     | URL where response will be posted            | Compulsory          |
| images          | Front and Back side Image of Driving licence | Compulsory          |
{% endtab %}

{% tab title="Sample CURL" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<Patron ID>/identities' \
--header 'Authorization: <AUTH TOKEN> \
--header 'Content-Type: application/json' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
    "type": "drivingLicence",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": []
}'
```
{% endtab %}
{% endtabs %}

**Response**

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

#### \*\*\*\*
{% endtab %}

{% tab title="Second Tab" %}
```
{
    "type": "drivingLicence",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [],
    "accessToken": "u173ke8uo0nfrslspcqt2ifbv5w1kfqfq",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "617fc6797157fd10dd4ed7f7",
    "patronId": "6140962af6d4030eae0496e0"
}
```
{% endtab %}
{% endtabs %}

### \*\*\*\*

### **Step 2:** Hit Snoops API and receives response

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters Name | Response                                         |
| --------------- | ------------------------------------------------ |
| service         | Type of Signzy service - “identity extraction”   |
| itemId          | Contains the identity item id                    |
| accessToken     | URL where response will be posted                |
| task            | The type of task performed - “Auto Recognition”  |
| essentials      | Contains the essential output data               |
| number          | Driving Licence number that needs to be verified |
| d.o.b           | D.O.B of the person                              |
| issue date      | Date of issue of DL                              |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/snoops' \
--header 'Connection: keep-alive' \
--header 'Content-Type: application/json;charset=UTF-8' \
--data-raw '{
    "service": "Identity",
    "itemId": "<>",
    "accessToken": "<Identity Access token>",
    "task": "verification",
    "essentials": {
        "issueDate": "<Issue-Date>format dd/mm/yyyy",
        "dob": "<Date of Birth>format dd/mm/yyyy",
        "number": "<Driving-Licence-Number>"
    }
}'
```
{% endtab %}
{% endtabs %}

***

### Sample API Response

{% tabs %}
{% tab title="Response Parameters" %}
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
    "itemId": "617fc6367157fd10dd4ed7e5",
    "task": "verification",
    "essentials": {
        "issueDate": "01/03/2011",
        "dob": "09/02/1976",
        "number": "DL-0420110149646",
        "instance": {
            "id": "617fc6367157fd10dd4ed7e5",
            "callbackUrl": "https://www.w3schools.com"
        }
    },
    "accessToken": "rpdhrfu8joeccomzy2n4b7y7fgasx487",
    "id": "617fc99c7157fd10dd4ed8d5",
    "response": {
        "issueDate": "01/03/2011",
        "dob": "09/02/1976",
        "number": "DL-0420110149646",
        "instance": {
            "id": "617fc6367157fd10dd4ed7e5",
            "callbackUrl": "https://www.w3schools.com"
        },
        "id": 1,
        "result": {
            "verified": true,
            "message": "Driving licence verification process completed successfully with positive result.",
            "moreInfo": {
                "issueDate": "<Date of issuance of DL>",
                "expiryDate": "<Date of expiry of DL>",
                "vehicleClass": [
                    "ADPVEH"
                ]
            }
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

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/9b6a7babd012235b2a9b)

**Verification Result Scenarios**

1. Driving licence verification process completed successfully with a positive result - When DL Number and issue Date perfectly matches with the Government recorded data. \\
2. The Driving licence verification process was completed successfully with a negative result. - when DL Number and issue Date doesn't match with the Government recorded data. \\
3. The Provided DL Number is not found - This happens when:

* The provided DL Number is wrong.
* The provided DL Number is not updated in the government database.
* The Underlying government data source is having some issues at this moment.

**State List where DL Verification does not Work**

The DL verification service is not applicable for a licence issued in any one of the following states:

1 ) Bihar

2 ) Jharkhand

3 ) Madhya Pradesh

4 ) West Bengal
