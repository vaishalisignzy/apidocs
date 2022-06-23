# Voter ID Data Extraction

### **Introduction**

This API can be used for extracting details of the user by uploading the image of the voter ID card. These details can be in the form of Voter ID number, Name, Address, etc.

> Though this engine supports data extraction from images as well as from pdf files, our test results indicate that there is much better accuracy and faster response time for image extraction. We would suggest you to pass only image file for better results. For pdf files extraction, you can use our [PDF to image converter ](../../../converters/pdf-to-jpg.md)API and then pass the resulting image for data extraction.



### API Usecase

The Voter ID data extraction API uses the image/image URL or pdf file that is uploaded to the API for extracting the details of the individual. This helps in auto-generating the details for the user without having to manually provide the information.

### How to call the API

Before going for Auto reading, you first need to create an Identity object. To get an overview of the ID verification process visit here. For best results, please make sure that the image you use fits tightly in camera view and is horizontally aligned. Each image/pdf should be less than 2MB and an expired image should not be uploaded.

> The Aadhaar Card reading system accepts direct URL of the front and back of the Voter ID.

### API Input Guidelines

* Image should be well lit
* Image should be less than 2MB in size
* API accepts only image/pdf or URLs of image

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
    "images": [
        <VOTER CARD FRONT IMAGE URL>",
        "<VOTER CARD BACK IMAGE URL>"
    ]
}'
```
{% endtab %}
{% endtabs %}

<mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Parameters" %}
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
    "images": [
        "https://preproduction-persist.signzy.tech/api/files/29510437/download/a4bc33097c60463d8259b9193eac092128df814259444690bcae2635366a51b2.jpeg",
        "https://preproduction-persist.signzy.tech/api/files/29510435/download/275c7c27dc4444c79e8fe9971c97e8ebb1ef2f7f453e4558bf9cb8fc88b3babf.jpeg"
    ],
    "accessToken": "xejwo7zwex587pydjn0gqhdlaak7rlzn",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "61809f257157fd10dd4ee68e",
    "patronId": "6140962af6d4030eae0496e0"
}
```
{% endtab %}
{% endtabs %}

### ****

### **Step 2:** Hit Snoops API and receives response

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

{% tab title="Sample CURL " %}
```
curl --location --request POST 'https://signzy.tech/api/v2/snoops' \
--header 'Content-Type: application/json;charset=UTF-8' \
--data-raw '{
    "service": "Identity",
    "itemId": "<Identity ID>",
    "accessToken": "<Identity access token>",
    "task": "autoRecognition",
    "essentials": {}
}'
```
{% endtab %}
{% endtabs %}

****

### <mark style="color:green;">**Sample API Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| **PARAMETER  NAME**         | **DESCRIPTION**                                                                                                                                                                                                                                         |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| service                     | Type of Signzy service - “identity extraction”                                                                                                                                                                                                          |
| itemId                      | Contains the identity item id                                                                                                                                                                                                                           |
| task                        | <p>The type of task performed - “Auto Recognition”<br></p>                                                                                                                                                                                              |
| essentials                  | Contains the essential output data                                                                                                                                                                                                                      |
| essentials.accessToken&#xD; | Contains the access token that was received from identity request&#xD;                                                                                                                                                                                  |
| essentials.Id               | Contains the unique Id received from the identity request.&#xD;                                                                                                                                                                                         |
| response                    | Contains the output files                                                                                                                                                                                                                               |
| result                      | This holds the final result parameters of the response.&#xD;                                                                                                                                                                                            |
| result.epicNumber           | The Voter Id/ Epic Number of the voter card which is uploaded.                                                                                                                                                                                          |
| result.name                 | The name of the voter card holder                                                                                                                                                                                                                       |
| result.fatherName           | The father's name of the voter card holder.                                                                                                                                                                                                             |
| result.state                | This parameter returns the state information of the voter card holder                                                                                                                                                                                   |
| result.dob                  | The date of birth of the voter card holder                                                                                                                                                                                                              |
| result.yob                  | The year of birth of the voter card holder                                                                                                                                                                                                              |
| result.ageAsOn              | This parameter returns the age in year to be compared with the dob for calculating the voter card owner's age.                                                                                                                                          |
| result.address              | The address information on the card is returned                                                                                                                                                                                                         |
| result.splitAddress         | This parameter distinguishes the various parts of the address of the ID holder into separate categories like district, state, city, pincode and country. For the country category, acceptable values (for Indian ID cards) is “IN”,”IND”and”INDIA”&#xD; |
| url                         | Contains the image URL of the uploaded image                                                                                                                                                                                                            |
| callbackUrl                 | URL where the data is to be posted once the  request is processed                                                                                                                                                                                       |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "service": "Identity",
    "itemId": "6147a721f0e8db4b731802bd",
    "task": "autoRecognition",
    "essentials": {},
    "accessToken": "ggafwvjwuray0app2wjg4fu0xk066lk6",
    "id": "6147a7c9f0e8db4b731802c0",
    "response": {
        "result": {
            "name": "KRISHNA PRASAD TENNETI",
            "fatherName": "SUBBAIAH",
            "address": "Mohana Mohana , Anchal - Jhanjharpur , Distt. ,- Madhubani , 847404",
            "state": "BIHAR",
            "ageAsOn": "",
            "dob": "",
            "gender": "",
            "yob": "",
            "epicNumber": "WKH1186254",
            "splitAddress": {
                "district": [
                    "MADHUBANI"
                ],
                "state": [
                    [
                        "BIHAR",
                        "BR"
                    ]
                ],
                "city": [
                    "JHANJHARPUR"
                ],
                "pincode": "847404",
                "country": [
                    "IN",
                    "IND",
                    "INDIA"
                ],
                "addressLine": "MOHANA MOHANA,ANCHAL DISTT"
            }
        },
        "url": [
            "https://preproduction-persist.signzy.tech/api/files/28414221/download/fefb69831d704012a17a91aed97579c4311ba549355c4d4ca64354b47a9f7df1.jpeg",
            "https://preproduction-persist.signzy.tech/api/files/28414223/download/a69a444c7ed44d41b47dfcf2c8220223e48d15316273407d9123ed21b58fa4e8.jpeg"
        ],
        "callbackUrl": "https://www.w3schools.com",
        "instaneId": "6147a721f0e8db4b731802bd"
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
