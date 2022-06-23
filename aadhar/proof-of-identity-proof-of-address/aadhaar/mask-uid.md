---
description: Aadhaar UID Masker
---

# Aadhaar Masking

### Introduction

The Aadhaar masking option allows you to mask Aadhaar number in e-Aadhaar. Masked Aadhaar number implies **replacing of first 8 digits of the Aadhaar number** with a white stripe.

### **API Use-Case**

The Mask UID service generates an image of the Aadhaar card where the unique identification number or UID is hidden so that it cannot be viewed.&#x20;

{% hint style="info" %}
Masking becomes important in cases where just the Aadhaar Card details are required but the number needs to be hidden.
{% endhint %}

### How to call the API

Before going for Masking, you first need to create an Identity object. For best results, please make sure that the image you use fits tightly in camera view and is horizontally aligned. Each image/pdf/tiff should be less than 2MB and an expired image should not be uploaded.

### API Input Guidelines

* The Image should be of good quality.
* Image should be less than 2MB in size.
* API accepts Image, pdf's and URLs.



### Sample cURL Request

### **Step 1**: Hit Identities API

{% tabs %}
{% tab title="Input Parameter" %}
| Parameters Name | Description                       |
| --------------- | --------------------------------- |
| type            |                                   |
| email           |                                   |
| callbackurl     | URL where response will be posted |
{% endtab %}

{% tab title="Sample CURL" %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/patrons/<Patron Id>/identities' \
--header 'Accept: application/json, text/plain, */*' \
--header 'Authorization: <Auth key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "type": "aadhaar",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": []
}'
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Identity Parameters" %}
| Parameters Name | Description                                                                      |
| --------------- | -------------------------------------------------------------------------------- |
| accessToken     | Contains the access token that was received from identity requestautorecognition |
| id              |                                                                                  |
| patronId        | Unique user ID                                                                   |
{% endtab %}

{% tab title="Identity Response" %}
```
{
    "type": "aadhaar",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [
        "https://preproduction-persist.signzy.tech/api/files/28575821/download/e1421811d1ec4a48923f15fc4931bbc9e4cafb4a0bd14cbe9cd5d099927773f7.jpeg",
        "https://preproduction-persist.signzy.tech/api/files/28575895/download/854e140a5d1e45578edaff77c3177064c9d3b82bc2464dcab5a3e2a88348f445.jpeg"
    ],
    "accessToken": "mpis3k33fvz8dzo0wsj7rs07zvjmfpk",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "615329acf0e8db4b7318c5a6",
    "patronId": "6140962af6d4030eae0496e0"
}
```
{% endtab %}
{% endtabs %}

****

****

### **Step 2:** Hit Snoops API and receives response

{% tabs %}
{% tab title="Response Parameters" %}
| Parameters Name | Description |
| --------------- | ----------- |
| service         |             |
| itemId          |             |
| accessToken     |             |
| task            |             |
| essentials.url  |             |
{% endtab %}

{% tab title="Soops Response" %}
```
{
    "service": "Identity",
    "itemId": "61447c2af6d4030eae05416e",
    "accessToken": "<Identity-access-token>",
    "task": "aadhaarMasker",
    "essentials": {
        "url": "https://preproduction-persist.signzy.tech/api/files/28235589/download/03f2960549b44d3a94a1a3e7801fa3788e022050012944dcae92c1ec18d983e0.jpeg"
    }
}
```
{% endtab %}
{% endtabs %}

****

### Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name       | Description                                                          |
| -------------------- | -------------------------------------------------------------------- |
| service              | The type of Signzy service - “identity extraction”.                  |
| itemId               | This parameter contains the identity item id.                        |
| task                 | The type of task performed - “aadhaarMasker”.                        |
| essentials           | Contains the essential output data.                                  |
| essentials.url       | Contains the URL of the uploaded image.                              |
| accessToken          | Contains the access token that was received from identity request    |
| Id                   | Contains the patron Id of the snoop request                          |
| response.url         | This parameter contains the output files                             |
| callOcronFallback    |                                                                      |
| instance.id          |                                                                      |
| instance.callbackUrl |                                                                      |
| result               | This parameter holds the masked images of the Aadhaar card.          |
| result.isMasked      | It shows whether the masking result is a yes or no                   |
| result.maskedImages  | The masked image URL of the Aadhaar card is shown by this parameter. |
{% endtab %}

{% tab title="API Response" %}
```
{
   "service":"Identity",
   "itemId":"<Identity-Id>",
   "task":"aadhaarMasker",
   "essentials":{
      "url":"https://preproduction-persist.signzy.tech/api/files/28604967/download/f1c02c244a3a464ca181bd6b5954dfc0782678f12ea44211b05fb4168144d9e8.jpeg"
   },
   "accessToken":"hc0ffbh26wfalrd1n9co2e7x3t89sXXXX",
   "id":"6153b838f0e8db4b7318ca9a",
   "response":{
      "urls":[
         "https://preproduction-persist.signzy.tech/api/files/28604967/download/f1c02c244a3a464ca181bd6b5954dfc0782678f12ea44211b05fb4168144d9e8.jpeg"
      ],
      "id":2604,
      "callOcrOnFallback":[
         null
      ],
      "instance":{
         "id":"6153b780f0e8db4b7318ca8e",
         "callbackUrl":"https://www.w3schools.com"
      },
      "result":{
         "isMasked":"yes",
         "maskedImages":[
            "https://persist.signzy.tech/api/files/216990453/download/8127946a089c4d4eb98caeb81273760c8d1eaa77fc644ddd8196deca637bd1e8.jpeg"
         ]
      }
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

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/44e25d58debc4246f46f)

