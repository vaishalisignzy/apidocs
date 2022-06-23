# PAN Data Extraction

### **Introduction**

PAN Stands for <mark style="color:purple;">Permanent Account Number</mark> it serves as powerful ID proof in the Indian subcontinent. It is allotted by the Income Tax Department to an individual or business and can help keep track of all transactions carried out by the individuals, business, or anyone who has been allotted with PAN.

### API Usecase

Though this engine support extraction of images as well as pdf files, our test results indicate that there is much better accuracy and faster response time for **image** extraction than **pdf** extraction. **We would suggest you pass only the image file** for _better results_. For pdf files extraction, you can use our [pdf to image converter API ](../../../converters/pdf-to-jpg.md)and then pass the resulting image file in this extraction engine.

> PAN Card reading system also accepts the direct URL of the image of PAN, for data extraction.>>

### How to call the API

Before proceeding to Auto reading or Verification calls, you first need to create an Identity object. To get an overview of the ID verification process visit here. For best results, please make sure that the image you use fits tightly in camera view and is horizontally-aligned. Each image/pdf should be less than 2MB.

> The Aadhaar Card reading system accepts direct URL to the front and back sides.

### API Input Guidelines

* Image should be well lit
* Image should be less than 2MB in size
* API accepts only image/pdf or URLs of image

****

### <mark style="color:blue;">Sample CURL Request</mark>

#### **Step 1**: Hit Identities API

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
    "images": [
        "https://preproduction-persist.signzy.tech/api/files/29510889/download/5b3201c0425e4b358af023636dece0dd5242a330a9e3412d99c7cd1cf3abdca2.jpeg"
    ]
}'
```
{% endtab %}
{% endtabs %}

<mark style="color:green;">****</mark>

<mark style="color:orange;">**Response**</mark>

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
    "images": [
        "https://preproduction-persist.signzy.tech/api/files/29510889/download/5b3201c0425e4b358af023636dece0dd5242a330a9e3412d99c7cd1cf3abdca2.jpeg"
    ],
    "accessToken": "0551avw6syml7ni00efunotqgx6t5btrlf",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "6180b8f87157fd10dd4ee76b",
    "patronId": "6140962af6d4030eae0496e0"
}
```
{% endtab %}
{% endtabs %}

#### **Step 2:** Hit Snoops API and receives **a** response

{% tabs %}
{% tab title="Snoops Parameters" %}
| **PARAMETER  NAME** | **DESCRIPTION**                                            |
| ------------------- | ---------------------------------------------------------- |
| service             | Type of Signzy service - “identity extraction”             |
| itemId              | Contains the identity item id                              |
| accessToken         | Identity access token                                      |
| task                | <p>The type of task performed - “Auto Recognition”<br></p> |
| essentials          | Contains the essential output data                         |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/snoops' \
--header 'Content-Type: application/json;charset=UTF-8' \
--data-raw '{
          "service":"Identity",
          "itemId":"<Identity-object-id>",
          "task":"autoRecognition",
          "accessToken":"<Identity-access-token>",
          "essentials":{}
}'
```
{% endtab %}
{% endtabs %}



### <mark style="color:green;">**Sample API Output Parameters and Response**</mark>

{% tabs %}
{% tab title="Response parameters" %}
| **PARAMETER  NAME**                  | **DESCRIPTION**                                                     |
| ------------------------------------ | ------------------------------------------------------------------- |
| Service                              | Type of service - “identity”                                        |
| ItemId                               | Contains the identity item id                                       |
| Task                                 | The type of task performed - “Auto Recognition”                     |
| Essentials                           | Contains the essential output data                                  |
| <p>essentials.</p><p>accessToken</p> | Contains the access token that was received from identity request   |
| Essentials.id                        | Contains the unique Id of the snoop request                         |
| Response                             | Contains the output files                                           |
| Response.Files                       | Contains the image URL of the output.                               |
| type                                 | type of identity : "individualPAN/businessPAN"                      |
| id                                   | Unique id of the identity                                           |
| result                               | This holds final result parameters of the response.                 |
| result.name                          | Name of the PAN cardholder/Organisation name in case of businessPAN |
| result.fatherName                    | Father's name on the card (valid only for individual PAN)           |
| result.dob                           | Date Of Birth of cardholder/Date of Issue in case of businessPAN    |
| result.number                        | PAN number of the individual                                        |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "service": "Identity",
    "itemId": "6180b4ee7157fd10dd4ee74f",
    "task": "autoRecognition",
    "essentials": {},
    "accessToken": "25eb2pq8bwlyfkgnx8kpurrv0blw0k",
    "id": "6180bac37157fd10dd4ee775",
    "response": {
        "files": [
            "https://preproduction-persist.signzy.tech/api/files/29510889/download/5b3201c0425e4b358af023636dece0dd5242a330a9e3412d99c7cd1cf3abdca2.jpeg"
        ],
        "type": "individualPan",
        "instance": {
            "id": "6180b4ee7157fd10dd4ee74f",
            "callbackUrl": "https://www.w3schools.com"
        },
        "id": 93,
        "result": {
            "dob": "01/01/1996",
            "name": "POOJA",
            "fatherName": "BADAN SINGH",
            "number": "DQYPP6888Q",
            "panType": "Adult",
            "summary": {
                "number": "DQYPP6888Q",
                "name": "POOJA",
                "dob": "01/01/1996",
                "address": "",
                "splitAddress": {
                    "district": [],
                    "state": [
                        []
                    ],
                    "city": [],
                    "pincode": "",
                    "country": [],
                    "addressLine": ""
                },
                "gender": "",
                "guardianName": "BADAN SINGH",
                "issueDate": "",
                "expiryDate": ""
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

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/747959fb564bda763326)
