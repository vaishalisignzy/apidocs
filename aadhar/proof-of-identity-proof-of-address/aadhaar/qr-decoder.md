---
description: Extracting Aadhaar data by scanning QR code.
---

# Aadhaar data Extraction by QR Code scan (404)

### Introduction

Every Aadhaar card has a QR code window which can be located on the bottom right corner of the card. _QR decoder_ is a unique product that reads the QR code and extracts the required details. The API responds with a JSON object. The image quality needs to be of good quality for Aadhaar QR code Extraction.

### API Usecase

The Aadhaar QR code decoder scans the QR code that is uploaded to the API for extracting the unique identification details of the individual. This helps in auto-generating the details for the user without having to manually provide the information.

### [Data Stored in QR code](https://uidai.gov.in/ecosystem/authentication-devices-documents/qr-code-reader.html)

* Ref ID
* Name
* Gender
* DOB
* Mobile
* Email
* Address
* Photograph
*   2048 bit digital signature



### How to call the API

Before going for aQR code scan, you first need to create an Identity object. For best results, please make sure that the image you use fits tightly in camera view and is horizontally aligned. Each image/pdf should be less than 2MB and an expired image should not be uploaded.

### API input guidelines

* The Image should be of good quality.
* Image should be less than 2MB in size.
* API accepts only image/pdf URLs.

### Input Parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

### Output Parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

### Sample cURL Request

**Step 1**: Hit Identities API

```
```

**Step 2:** Hit Snoops API and receives response

```
```

### Sample API Response

```
```

### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/snoops" method="post" summary="Aadhaar QR Decoder" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/snoops`

\




\


This method allows reading the QR code on Aadhaar for details
{% endswagger-description %}

{% swagger-parameter in="body" name="essentials.url" type="string" %}
Contains the image URL
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains the url of the image from where qr needs to be decoded
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
type of task - decodeQR
{% endswagger-parameter %}

{% swagger-parameter in="body" name="itemID" type="string" %}
Contains the Identity object id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="service" type="string" %}
type-identity
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "service": "Identity",
    "itemId": "..itemId..",
    "task": "decodeQR",
    "essentials": {
      "url": "https://persist.signzy.tech/api/files/5860c69126dfcb1472bc0660/download/h9vPIkcXnREZ4WnUaGmQgTqRzTNDTabW958pUIvStKiQEgSIfD.jpg"
    },
    "accessToken": "<Identity-access-token>",
    "id": "...patronId...",
    "response": {
      "url": "https://persist.signzy.tech/api/files/5860c69126dfcb1472bc0660/download/h9vPIkcXnREZ4WnUaGmQgTqRzTNDTabW958pUIvStKiQEgSIfD.jpg",
      "id": 2,
      "result": {
        "uid": "..uid...",
        "name": "...name...",
        "gender": "..gender..",
        "yob": "..yob..",
        "fatherName": "...fatherName...",
        "splitAddress": {
          "house": "...house...",
          "street": "...street...",
          "lm": "...landmark name...",
          "vtc": "...village/town/city...",
          "postOffice": "...post office name...",
          "district": "...district...",
          "state": "...state...",
          "pincode": "...pincode...",
          "country": [
            "IN",
            "IND",
            "INDIA"
          ],
          "addressLine": "...addressLine..."
        },
        "address": "...address..."
       }
      }
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
      "service":"Identity",
      "itemId":"<Identity-object-id>",
      "task":"decodeQR",
      "accessToken":"<Identity-access-token>",
      "essentials":{
        "url": "..url-of-image-from-where-qr-needs-to-be-decoded"
      }
    }
```
{% endtab %}

{% tab title="Response Parameter" %}
| PARAMETER  NAME          | DESCRIPTION                                                                                                                                                                                                                                                                              |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| service                  | Type of Signzy service - “identity extraction”.                                                                                                                                                                                                                                          |
| itemId                   | Contains the identity item id.                                                                                                                                                                                                                                                           |
| task                     | The type of task performed - “decodeQR”.                                                                                                                                                                                                                                                 |
| essentials               | Contains the essential output data.                                                                                                                                                                                                                                                      |
| essentials.url           | The URL of the uploaded image.                                                                                                                                                                                                                                                           |
| <p>accessToken<br></p>   | Contains the access token that was received from identity request.                                                                                                                                                                                                                       |
| Id                       | Contains the patron Id of the snoop request.                                                                                                                                                                                                                                             |
| response                 | Contains the output files.                                                                                                                                                                                                                                                               |
| response.url             | Contains the image URL of the output.                                                                                                                                                                                                                                                    |
| result                   | This parameter holds the final result parameters of the response.                                                                                                                                                                                                                        |
| <p>result.uid<br></p>    | The unique Aadhaar ID number (with masked digits).                                                                                                                                                                                                                                       |
| <p>result.vid<br></p>    | The Virtual Aadhaar ID number.                                                                                                                                                                                                                                                           |
| <p>result.name<br></p>   | This parameter contains the name on the ID card.                                                                                                                                                                                                                                         |
| result.gender            | The gender of the Aadhaar card holder.                                                                                                                                                                                                                                                   |
| <p>result.yob<br></p>    | <p>This parameter returns the Year of birth of the ID holder<br></p>                                                                                                                                                                                                                     |
| result.fatherName        | The father's name of the Aadhaar Card holder.                                                                                                                                                                                                                                            |
| result.splitAddress      | <p>This parameter distinguishes the various parts of the address of the ID holder into separate categories like house, street name, landmark name, village/town/city, district, state, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”<br></p> |
| splitAddress.addressLine | The first line of the address is displayed here.                                                                                                                                                                                                                                         |
| result.address           | The address of the Aadhaar card holder.                                                                                                                                                                                                                                                  |
{% endtab %}
{% endtabs %}



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/c08b1623d99f9139ddc1)

