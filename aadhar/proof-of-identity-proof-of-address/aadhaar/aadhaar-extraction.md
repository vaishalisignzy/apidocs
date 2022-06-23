---
description: Extraction of Aadhaar data from an image, pdf or image URL.
---

# Aadhaar Data Extraction

### **Introduction**

Aadhaar is a 12-digit unique identity number that can be obtained voluntarily by residents or passport holders of India, based on their biometric and demographic data. The data is collected by the Unique Identification Authority of India (UIDAI), a statutory authority established in January 2009 by the government of India.

### API Usecase

The Aadhar extraction API uses the image/image URL or pdf file that is uploaded to the API for extracting the unique identification details of the individual. This helps in auto-generating the details for the user without having to manually provide the information.

### How to call the API

Before going for Auto reading or Verification calls, you first need to create an Identity object.  For best results, please make sure that the image you use fits tightly in camera view and is horizontally aligned. Each image/pdf should be less than 2MB and an expired image should not be uploaded.

> The Aadhaar Card reading system accepts direct URL to the front and back sides.

### API Input Guidelines

* The Image should be of good quality
* The Image should be less than 2MB in size
* This API accepts only image, pdf, or URLs of image(png/jpg/jpeg/tiff)

{% hint style="info" %}
> If the image quality is not as per the guidelines this API won't be able to extract data and respond with an error code 404 with a message of invalid data.
{% endhint %}



### Sample CURL Request

### **Step 1**: Hit Identities API

{% tabs %}
{% tab title="Input Parameters" %}


| Parameter Name | Required/Optional | Description                       |
| -------------- | ----------------- | --------------------------------- |
| type           | Required          | Type of identity                  |
| email          | Required          | e-mail ID                         |
| callbackurl    | Required          | URL where response will be posted |
| images         | Required          | Front and back image of aadhaar   |
{% endtab %}

{% tab title="Sample Curl" %}
```
curl --location --request POST 
 'https://signzy.tech/api/v2/patrons/<Patron ID>/identities' \
--header 'Connection: keep-alive' \
--header 'Authorization: <Auth Key>' \
--header 'Content-Type: application/json' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
    "type": "aadhaar",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [
        "<Front Image URL>",
        "<Back Image URL>"
    ]
}'
```
{% endtab %}
{% endtabs %}



Response

{% tabs %}
{% tab title="Response Parameter" %}
| Parameter Name  | Description                           |
| --------------- | ------------------------------------- |
| accessToken     | This is provided by identities API    |
| autoRecognition | Auto Recogises text from upload image |
| verification    | verification is done                  |
| forgeryCheck    | Frogery check is done                 |
| id              | Unique user id                        |
| patronId        | Unique patron id                      |
{% endtab %}

{% tab title="Sample Response" %}
```
{
    "type": "aadhaar",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [
        "https://<Front side image URL>",
        "https://<Back side image URL>"
    ],
    "accessToken": "76l99svplzn0l4ndpeleygonv68nwahgm",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "6153fbe1f0e8db4b7318cf80",
    "patronId": "6140962af6d4030eae0496e0"
}

```


{% endtab %}
{% endtabs %}

### ****

### **Step 2:** Hit Snoops API and receives a response

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/Optional | Description                                                                                |
| -------------- | ----------------- | ------------------------------------------------------------------------------------------ |
| service        | Required          | Type of Signzy service - “identity extraction”                                             |
| itemId         | Required          | Contains the identity item id                                                              |
| accessToken    | Required          | This is provided by the identities API                                                     |
| task           | Required          | This value always remains fixed for Aadhaar extraction API, it is always `AutoRecognition` |
| essentials     | Required          | Contains the essential output data                                                         |


{% endtab %}

{% tab title="Sample Curl" %}
```
curl --request POST \
  --url https://signzy.tech/api/v2/snoops \
  --header 'accept: */*' \
  --header 'accept-language: en-US,en;q=0.8' \
  --header 'content-type: application/json' \
  --data '
    {
      "service":"Identity",
      "itemId":"<Identity-ID>",
      "accessToken":"<Identity-token>",
      "task":"autoRecognition",
      "essentials":{}
    }'
```


{% endtab %}
{% endtabs %}

****

**Response**

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name         | Description                                                                                                                                                                                                                                           |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| service                | Type of Signzy service - “identity extraction”                                                                                                                                                                                                        |
| itemId                 | Contains the identity item id                                                                                                                                                                                                                         |
| task                   | The type of task performed - “Auto Recognition”                                                                                                                                                                                                       |
| essentials             | Contains the essential output data                                                                                                                                                                                                                    |
| essentials.accessToken | Contains the access token that was received from identity request                                                                                                                                                                                     |
| essentials.Id          | Contains the unique Id of the snoop request                                                                                                                                                                                                           |
| response               | Contains the output files                                                                                                                                                                                                                             |
| files                  | Contains the image URL of the output                                                                                                                                                                                                                  |
| result                 | This parameter holds the final result parameters of the response.                                                                                                                                                                                     |
| result.uid             | The unique Aadhaar ID number                                                                                                                                                                                                                          |
| result.vid             | The Virtual Aadhaar ID number                                                                                                                                                                                                                         |
| result.name            | This parameter contains the name on the ID card                                                                                                                                                                                                       |
| result.yob             | This parameter returns the Year of birth of the ID holder                                                                                                                                                                                             |
| result.dob             | Date of birth of the ID holder                                                                                                                                                                                                                        |
| result.pincode         | The pincode of the ID card holder’s address                                                                                                                                                                                                           |
| result.address         | The address of the ID card holder                                                                                                                                                                                                                     |
| result.gender          | The gender of the ID card holder                                                                                                                                                                                                                      |
| result.splitAddress    | This parameter distinguishes the various parts of the address of the ID holder into separate categories like district, state, city, Pincode, and country. For the country category, acceptable values (for Indian ID cards) is “IN”,” IND”and” INDIA” |
| uidHash                | Contains the encrypted hash value of the UID                                                                                                                                                                                                          |


{% endtab %}

{% tab title="API Response" %}
```
{
    "service": "Identity",
    "itemId": "615190a5f0e8db4b73189b4b",
    "task": "autoRecognition",
    "essentials": {},
    "accessToken": "<Identity access token>",
    "id": "<ID of the snoop request>",
    "response": {
        "files": [
            "<Front aadhaar image URL>",
            "<Back aadhaar image URL>"
        ],
        "id": 47179,
        "instance": {
            "id": "615190a5f0e8db4b73189b4b",
            "callbackUrl": "https://www.w3schools.com"
        },
{
  "uid": "000000001308",
  "vid": "",
  "name": "Ajay Singh",
  "dob": "01/01/1982",
  "yob": "1982",
  "pincode": "121003",
  "address": "<Address of Aadhaar Holder>,
  "gender": "female",
  "splitAddress": {
    "district": [
      "FARIDABAD"
    ],
    "state": [
      [
        "HARYANA",
        "HR"
      ]
    ],
    "city": [
      "ANANGPUR"
    ],
    "pincode": "<Pin code>",
    "country": [
      "IN",
      "IND",
      "INDIA"
    ],
    "addressLine": "<Address of Aadhaar Holder>"
  },
  "uidHash": "<Encrypted hash value>",
  "summary": {
    "number": "000000001308",
    "name": "Ajay Singh",
    "dob": "01/01/1982",
    "address": "<Address of Aadhaar Holder>",
    "splitAddress": {
      "district": [
        "FARIDABAD"
      ],
      "state": [
        [
          "HARYANA",
          "HR"
        ]
      ],
      "city": [
        "ANANGPUR"
      ],
      "pincode": "121003",
      "country": [
        "IN",
        "IND",
        "INDIA"
      ],
      "addressLine": "Address of Aadhaar Holder"
    },
    "gender": "Male",
    "guardianName": "",
    "issueDate": "",
    "expiryDate": ""
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

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/abcdfe7711a05b35b889)



