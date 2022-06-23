# Indian Passport Data Extraction

### Introduction

The Passport Extraction service is useful to users who wish to retrieve their details from the uploaded image of the Passport. This service can retrieve details like Name, Address, Case Number, Issue Date, etc.

> Though this engine support extraction of images as well as pdf files, our test results indicate that **there is much better accuracy and faster response time for image extraction**. We would **suggest you to pass only image file for better results**. For pdf files extraction, you can use our [pdf to image converter](../../../converters/pdf-to-jpg.md) API and then pass the resulted image file in this extraction.



### API Usecase

The Indian passport data extraction API uses the image/image URL or pdf file that is uploaded to the API for extracting the details of the individual. This helps in auto-generating the details for the user without having to manually provide the information.

### How to call the API

Before going for Auto reading, you first need to create an Identity object. To get an overview of the ID verification process visit here. For best results, please make sure the image you use fits tightly in camera view and is horizontally aligned. For Passport Extraction both front and back side images are mandatory.

### API Input Guidelines

* The Image should be well lit
* Image should be less than 2MB in size
* API accepts only image/pdf or URLs of image



### Sample cURL Request

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
--header 'Authorization: AUTH KEY' \
--header 'Content-Type: application/json' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
    "type": "passport",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [
        "<PASSPORT FRONT IMAGE URL>",
        "<PASSPORT BACK IMAGE URL>"
    ]
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
{% endtab %}

{% tab title="Sample Response" %}
```
{
    "type": "passport",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [
        "<PASSPORT FRONT IMAGE URL>",
        "<PASSPORT BACK IMAGE URL>"
    "accessToken": "<Access Token>",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "61808fe37157fd10dd4ee672",
    "patronId": "<Patron ID>"
}
```
{% endtab %}
{% endtabs %}

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

{% tab title="Response" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/snoops' \
--header 'Accept: application/json, text/plain, */*' \
--header 'Content-Type: application/json;charset=UTF-8' \
--data-raw '{
    "service": "Identity",
    "itemId": "61808fff7157fd10dd4ee673",
    "accessToken": "ef3r2my1nx4n5twycomaxgr8ibcb913tg",
    "task": "autoRecognition",
    "essentials": {}
}'
```
{% endtab %}
{% endtabs %}

### Sample API Response

{% tabs %}
{% tab title="Response Parameters" %}
| **PARAMETER  NAME**         | **DESCRIPTION**                                                                                                                                                                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| service                     | Type of Signzy service - “identity extraction”                                                                                                                                                                                                     |
| itemId                      | Contains the identity item id                                                                                                                                                                                                                      |
| task                        | <p>The type of task performed - “Auto Recognition”<br></p>                                                                                                                                                                                         |
| essentials                  | Contains the essential output data                                                                                                                                                                                                                 |
| essentials.accessToken&#xD; | Contains the access token that was received from identity request&#xD;                                                                                                                                                                             |
| essentials.id&#xD;          | Contains the unique Id received from the identity request.                                                                                                                                                                                         |
| response                    | Contains the output files                                                                                                                                                                                                                          |
| response.files              | Contains the image URL of the output.&#xD;                                                                                                                                                                                                         |
| result                      | This holds the final result parameters of the response.&#xD;                                                                                                                                                                                       |
| result.parentsGuardianName  | The parent/guardian name as mentioned in the  passport.                                                                                                                                                                                            |
| result.dateofIssue          | This parameter returns the Date of Issue for the passport.                                                                                                                                                                                         |
| result.expiryDate           | Contains the Expiry date of the passport                                                                                                                                                                                                           |
| result.birthDate            | Holds the Date of birth of the passport holder                                                                                                                                                                                                     |
| result.name                 | Name of the passport holder                                                                                                                                                                                                                        |
| result.country              | This parameter returns the country information of the passport holder                                                                                                                                                                              |
| result.nationality          | This parameter returns the nationality details of the passport holder.                                                                                                                                                                             |
| result.sex                  | Contains two options: F for Female, M for Male. This is used to select the gender of the passport holder.                                                                                                                                          |
| result.address              | The address information of the passport holder                                                                                                                                                                                                     |
| result.pincode              | Contains the pincode for the above mentioned address                                                                                                                                                                                               |
| result.passportNumber       | This parameter returns the passport number for the uploaded passport                                                                                                                                                                               |
| result.fileNumber           | This parameter returns the passport file number for the uploaded passport                                                                                                                                                                          |
| result.placeofBirth         | Contains the place of birth details for the passport holder.                                                                                                                                                                                       |
| result.placeofIssue         | Contains the place of issue details for the passport holder.                                                                                                                                                                                       |
| result.splitAddress         | This parameter distinguishes the various parts of the address of the ID holder into separate categories like district, state, city, pincode and country. For the country category, acceptable values (for Indian ID cards) is “IN”,”IND”and”INDIA” |


{% endtab %}

{% tab title="API  Response" %}


```
{
    "service": "Identity",
    "itemId": "61808fff7157fd10dd4ee673",
    "task": "autoRecognition",
    "essentials": {},
    "accessToken": "ef3r2my1nx4n5twycomaxgr8ibcb913tg",
    "id": "618091a67157fd10dd4ee677",
    "response": {
        "files": [
            "https://preproduction-persist.signzy.tech/api/files/29510393/download/e793435526094f548e0f457d663acf6f8cb98d8196f14b0796cab4d8e8c25505.jpeg",
            "https://preproduction-persist.signzy.tech/api/files/29510395/download/653dc972d6214f848ada8aeb2f708e306df11ff6ba654299aafac01801613f1c.jpeg"
        ],
        "id": 14783,
        "instance": {
            "id": "61808fff7157fd10dd4ee673",
            "callbackUrl": "https://www.w3schools.com"
        },
        "result": {
            "parentsGuardianName": "BHAVIKA JITEN RAMASWAMI",
            "issueDate": "22/10/2010",
            "expiryDate": "21/10/2020",
            "birthDate": "10/09/1984",
            "name": "GAURAV JOSHI",
            "country": [
                "IN",
                "IND",
                "India"
            ],
            "nationality": "INDIAN",
            "sex": "M",
            "address": "A 780,RUNWAL HEIGHTS LBS ROAD,MULUND (WEST) MUMBAI 400080",
            "pincode": "",
            "passportNumber": "J3703236",
            "fileNumber": "BOME045689734",
            "placeOfBirth": "CHANDIGARH INDIA",
            "placeOfIssue": "THANE",
            "splitAddress": {
                "district": [
                    "MUMBAI"
                ],
                "state": [
                    [
                        "MAHARASHTRA",
                        "MH"
                    ]
                ],
                "city": [
                    "MUMBAI"
                ],
                "pincode": "400080",
                "country": [
                    "IN",
                    "IND",
                    "INDIA"
                ],
                "addressLine": "A 780,RUNWAL HEIGHTS LBS ROAD,MULUND WEST"
            },
            "summary": {
                "number": "J3703236",
                "name": "GAURAV JOSHI",
                "dob": "10/09/1984",
                "address": "A 780,RUNWAL HEIGHTS LBS ROAD,MULUND (WEST) MUMBAI 400080",
                "splitAddress": {
                    "district": [
                        "MUMBAI"
                    ],
                    "state": [
                        [
                            "MAHARASHTRA",
                            "MH"
                        ]
                    ],
                    "city": [
                        "MUMBAI"
                    ],
                    "pincode": "400080",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "A 780,RUNWAL HEIGHTS LBS ROAD,MULUND WEST"
                },
                "gender": "M",
                "guardianName": "BHAVIKA JITEN RAMASWAMI",
                "issueDate": "22/10/2010",
                "expiryDate": "21/10/2020"
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

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/snoops" method="post" summary="Passport Extraction" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/snoops`

\




\


This method allows the basic details to be extracted from Passport.
{% endswagger-description %}

{% swagger-parameter in="body" name="service" type="string" %}
type - identity 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="itemID" type="object" %}
identity Item ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - Auto recognition
{% endswagger-parameter %}

{% swagger-parameter in="body" name="accessToken" type="object" %}
Identity access token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the image/image URL of the Passport from which the basic information has to be extracted
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
      "service": "Identity",
      "itemId": "...item id...",
      "task": "autoRecognition",
      "essentials": {},
      "accessToken": "...access token...",
      "id": "..id...",
      "response": {
        "files": ["..image url..."],
        "id": 3920,
        "instance": {},
        "result": {
          "parentsGuardianName": "..parentsGuardianName...",
          "issueDate": "..issueDate..",
          "expiryDate": "..expiryDate..",
          "birthDate": "..birthDate..",
          "name": "..name..",
          "country": [
            "..country.."
          ],
          "nationality": "..nationality..",
          "sex": "F/M",
          "address": "..address..",
          "pincode": "..pincode..",
          "passportNumber": "..passportNumber..",
          "fileNumber": "..fileNumber..",
          "placeOfBirth": "..placeOfBirth..",
          "placeOfIssue": "..placeOfIssue..",
          "splitAddress": {
            "district": [
              "..district.."
            ],
            "state": [
              [
                "..state.."
              ]
            ],
            "city": [
              "..city.."
            ],
            "pincode": "..pincode..",
            "country": [
              "IN",
              "IND",
              "INDIA"
            ],
            "addressLine": "..addressLine.."
          }
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
      "itemId":"<Identity-id>",
      "task":"autoRecognition","accessToken":"<Identity-access-token>",
      "essentials":{}
    }
```
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/9b6a7babd012235b2a9b)
