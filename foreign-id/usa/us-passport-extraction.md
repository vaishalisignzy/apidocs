# US Passport Extraction

### Introduction

Similar to the Passport extraction system, this is applicable only for reading US passports and extracting the information from the image like File Number, Name, Place Of Birth, Nationality and other details as required.

### API Usecase

This API can be used for auto reading US passports. It can extract data from an image of a passport.

### How to call the API

US Passport reading system accepts direct URL of the front image of passport.



### API Input Guidelines

We need to provide the direct URL of a passport image.

### Input Parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description |
| -------------- | ----------- |
|                |             |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/....patronid.../foreignidentitiesextractions \
  --header 'accept: */*' \
  --header 'accept-language: en-US,en;q=0.8' \
  --header 'authorization: <Access-Token>' \
  --header 'content-type: application/json' \
  --data '{"task":"usPassport","essentials":{"files":["...files.."]}}'
```


{% endtab %}
{% endtabs %}

### Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description |
| -------------- | ----------- |
|                |             |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
   "essentials":{
      "files":[
         "https://preproduction-persist.signzy.tech/api/files/32370019/download/33096a8e2c16425db21578e63a4b46a6cfdefa2828404033a9f167541c6a4507.jpg"
      ]
   },
   "id":"61b87488a90d4749419c0d09",
   "patronId":"6140993ef6d4030eae0497fb",
   "task":"usPassport",
   "result":{
      "name":"MR TRAVELER",
      "issueDate":"24/01/2006",
      "expiryDate":"23/01/2011",
      "birthDate":"01/01/2000",
      "country":[
         "",
         "UNITED STATES OF AMERICA"
      ],
      "nationality":"UNITED STATES OF AMERICA",
      "sex":"M",
      "address":"",
      "personalNumber":"9020000021407",
      "passportNumber":"340000230",
      "fileNumber":"",
      "placeOfBirth":"ARMENIA"
   }
}
```


{% endtab %}
{% endtabs %}

### Sample CURL Request



### Sample API Response



### HTTP Response Codes

| Status Code | Description                    |
| ----------- | ------------------------------ |
| 200         | All response details are valid |
| 400         | bad request                    |
| 401         | unauthorised                   |
| 404         | not found                      |
| 422         | processable entity             |

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../foreignidentitiesextractions" method="post" summary="US Passport Extraction" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your patron id../foreignidentitiesextractions`

\




\


This method is used to extract the details of a US Passport
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorisation" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - US Passport
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the image urls of the passport
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.files" type="object" %}
Contains the URLs of the image files
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
        "essentials": {
            files: ["...image url..."]
        },
        "id": "..id..",
        "patronId": "...patron id...",
        "task": "usPassport",
        "result": {
            "name": "..name..",
            "issueDate": "..issueDate..",
            "expiryDate": "..expiryDate..",
            "birthDate": "..birthDate..",
            "country": [
                "",
                ""
            ],
            "nationality": "..nationality..",
            "sex": "..sex..",
            "address": "..address..",
            "personalNumber": "..personalNumber..",
            "passportNumber": "..passportNumber..",
            "fileNumber": "..fileNumber..",
            "placeOfBirth": "..placeOfBirth.."
        }
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {

     "task" : "usPassport",
     "essentials": {
      "files": [
      		"...url of image file..."
      	]
     }
    }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME        | DESCRIPTION                                                               |
| --------------------- | ------------------------------------------------------------------------- |
| result                | This contains the final response parameters.                              |
| result.name           | This parameter displays the name of the passport holder.                  |
| result.issueDate      | This parameter contains the issue date of the passport.                   |
| result.expiryDate     | This parameter contains the expiry date of the US passport.               |
| result.birthDate      | This parameter contains the birth date of the individual passport holder. |
| result.country        | The country information is displayed as output.                           |
| result.nationality    | The nationality of the passport holder is displayed as output here.       |
| result.sex            | The parameter displays the gender information of the passport holder.     |
| result.address        | The address information of the US passport holder is displayed here.      |
| result.personalNumber | The personal number of the individual to whom the US passport belongs.    |
| result.passportNumber | The passport number for the passport holder is displayed here.            |
| result.fileNumber     | The file number for the US passport is shown as output.                   |
| result.placeOfBirth   | The place of birth of the passport holder is displayed here.              |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/7ffe52a8428026182ce4)
