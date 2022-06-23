# Driving Licence Data Extraction

### Introduction

Driving Licence Extraction by SIGNZY enables users to upload the details from the image of the uploaded driving licence. Similar in function to Aadhaar and PAN, the API can extract user details like name, DL number, Issue Date, Expiry Date and so on for further use.

{% hint style="info" %}
Though this engine support extraction of **images** as well as **pdf files**, **** our test results indicate that there is much better accuracy and faster response time for image extraction. We would suggest you pass only the image file for better results. For pdf files extraction, you can use our [pdf to image converter](../../../converters/pdf-to-jpg.md) API and then pass the resulted image file in this extraction.
{% endhint %}

### API Usecase

The Driving licence data extraction API uses the image/image URL or pdf file that is uploaded to the API for extracting the details of the individual. This helps in auto-generating the details for the user without having to manually provide the information.



### How to call the API

Before going for Auto reading or Verification calls, you first need to create an Identity object. To get an overview of the ID verification process visit here. For best results, please make sure the image you use fits tightly in camera view and is horizontally aligned. Each image/pdf should be less than 2MB.



### API Input Guidelines

* The Image should be well lit
* Image shout be less than 2MB in size
* API accepts only image/pdf URLs



### Sample cURL Request

### **Step 1**: Hit Identities API

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters Name | Description                                  | Compulsory/Optional |
| --------------- | -------------------------------------------- | ------------------- |
| type            | Type of Identity                             | Compulsory          |
| callbackurl     | URL where response will be posted            | Compulsory          |
| images          | Front and Back side Image of Driving licence | Compulsory          |
{% endtab %}

{% tab title="Sample CURL" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/identities' \
--header 'Authorization: AUTH' \
--header 'Content-Type: application/json' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
             "type": "drivingLicence",
             "email": "ankur.rand@signzy.com",
             "callbackUrl": "https://www.w3schools.com",
             "images": [
        "<DL Front Side Image URL>",
        "<DL Back Side Image URL"
    ]
}'
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Response Parameters " %}
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
    "type": "drivingLicence",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [
        "https://preproduction-persist.signzy.tech/api/files/29506935/download/b1de27d13b6f4deeb3a44b3946f60129169db305808644199c7eb6154342d90a.jpeg",
        "https://preproduction-persist.signzy.tech/api/files/29506937/download/1e515b44180e40f2bee62140071c4c153fe2c47919894a8aa050c8857def6cbb.webp"
    ],
    "accessToken": "5momkpfqaz454oyhdbn9w9yv542llo4u",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "617f801a7157fd10dd4eced8",
    "patronId": "6140962af6d4030eae0496e0"
}
```
{% endtab %}
{% endtabs %}

### ****

### **Step 2:** Hit Snoops API and receives **a** response

{% tabs %}
{% tab title="Snoops Parameters" %}
| Parameters Name | Response                                        |
| --------------- | ----------------------------------------------- |
| service         | Type of Signzy service - “identity extraction”  |
| itemId          | Contains the identity item id                   |
| accessToken     | URL where response will be posted               |
| task            | The type of task performed - “Auto Recognition” |
| essentials      | Contains the essential output data              |
{% endtab %}

{% tab title="Response" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/snoops' \
--header 'Accept: application/json, text/plain, */*' \
--header 'Content-Type: application/json;charset=UTF-8' \
--data-raw '{
    "service": "Identity",
    "itemId": "<Identity-id>",
    "accessToken": "<Identity-access-token>",
    "task": "autoRecognition",
    "essentials": {}
}'
```
{% endtab %}
{% endtabs %}

****

**API Response**

{% tabs %}
{% tab title="Output Parameters" %}
| **PARAMETER  NAME**    | **DESCRIPTION**                                                                                                                                                                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| service                | Type of Signzy service - “identity extraction”                                                                                                                                                                                                     |
| ItemId                 | Contains the identity item id                                                                                                                                                                                                                      |
| task                   | <p>The type of task performed - “Auto Recognition”<br></p>                                                                                                                                                                                         |
| essentials             | Contains the essential output data                                                                                                                                                                                                                 |
| essentials.accessToken | Contains the access token that was received from identity request&#xD;                                                                                                                                                                             |
| essentials.id&#xD;     | Contains the unique Id received from the identity request.&#xD;                                                                                                                                                                                    |
| response&#xD;          | Contains the output files&#xD;                                                                                                                                                                                                                     |
| response.files         | Contains the image URL of the output.&#xD;                                                                                                                                                                                                         |
| instance.callbackURL   | URL where the data is to be posted once the request is processed                                                                                                                                                                                   |
| result&#xD;            | This holds final result parameters of the response.&#xD;                                                                                                                                                                                           |
| result.issueDate       | This parameter contains the Date of Issue for the Driving Licence                                                                                                                                                                                  |
| result.dob&#xD;        | Date of birth of the DL holder                                                                                                                                                                                                                     |
| result.expiryDate      | expiry date of the driving licence                                                                                                                                                                                                                 |
| result.name            | The name on the driving licence.                                                                                                                                                                                                                   |
| result.number          | The driving licence number on the card                                                                                                                                                                                                             |
| result.guardianName    | The name of the individual's guardian as mentioned on the DL.                                                                                                                                                                                      |
| result.address         | Contains the address details under the parameter splitAddress.                                                                                                                                                                                     |
| address.splitAddress   | This parameter distinguishes the various parts of the address of the ID holder into separate categories like district, state, city, pincode and country. For the country category, acceptable values (for Indian ID cards) is “IN”,”IND”and”INDIA” |
| result.dlType          | The type of vehicle class for which DL has been assigned.                                                                                                                                                                                          |


{% endtab %}

{% tab title="API  Sample Response" %}
```
{
            "dlType": [],
            "issueDate": "01/03/2011",
            "expiryDate": "08/02/2026",
            "dob": "09/02/1976",
            "guardianName": "BODH RAJ BREJA",
            "name": "ANURAG BREJA",
            "number": "DL-0420110149646",
            "state": "Delhi",
            "address": "HNO-178 A2/B MIG FLATS PASCHIM VIHAR,DELHI 110063",
            "gaurdianName": "BODH RAJ BREJA",
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
                "pincode": "110063",
                "country": [
                    "IN",
                    "IND",
                    "INDIA"
                ],
                "addressLine": "HNO-178 A2/B MIG FLATS PASCHIM VIHAR"
            },
            "summary": {
                "number": "DL-0420110149646",
                "name": "ANURAG BREJA",
                "dob": "09/02/1976",
                "address": "HNO-178 A2/B MIG FLATS PASCHIM VIHAR,DELHI 110063",
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
                    "pincode": "110063",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "HNO-178 A2/B MIG FLATS PASCHIM VIHAR"
                },
                "gender": "",
                "guardianName": "BODH RAJ BREJA",
                "issueDate": "01/03/2011",
                "expiryDate": "08/02/2026"
            }
        }
    }
}
```


{% endtab %}
{% endtabs %}

###

### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/9b6a7babd012235b2a9b)
