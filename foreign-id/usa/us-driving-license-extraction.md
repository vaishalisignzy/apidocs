# US Driving License Extraction

### Introduction

Similar to the Driving Licence extraction system, this is applicable only for reading US passports and extracting the information from the image like Name, Issue Date, Expiry Date, address and other details as required.

### API Usecase

This API can be used for Auto-reading US Driving Licence. It can extract data from an image of a passport.

### How to call the API

US Driving Licence reading system accepts direct URL of the front image of Driving Licence.

### API Input Guidelines

Need to pass the full email id & access token for sending API requests.

### Input Parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

### Output Parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

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

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../foreignidentitiesextractions" method="post" summary="US Driving Licence" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your patron id../foreignidentitiesextractions`

\




\


This method is used to extract the details of a US Driving Licence
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorisation" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - US DrivingLicence
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the image urls of the driving licence
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.files" type="object" %}
Contains the URLs of the image files
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
        "essentials": {
            "files": [
                "...url of dl file..."
            ]
        },
        "id": "...id...",
        "patronId": "...patron id...",
        "task": "usDrivingLicence",
        "result": {
            "firstName": "...first name...",
            "lastName": "...last name...",
            "number": "...dl number...",
            "dob": "...date of birth...",
            "issueDate": "...date of issue...",
            "expiryDate": "...date of expiry...",
            "address": "...address..."
        }
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {

     "task" : "usDrivingLicence",
     "essentials": {
      "files": [
      		"...url of image file..."
      	]
     }
    }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME    | DESCRIPTION                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| result            | This displays the final response parameters.                             |
| result.firstName  | This parameter returns the first name of the driving license holder.     |
| result.lastName   | This parameter returns the last name of the driving license holder.      |
| result.number     | The driving license number is displayed here.                            |
| result.dob        | The date of birth of the driving license holder is displayed here.       |
| result.issueDate  | The date of issue of the driving license is displayed by this parameter. |
| result.expiryDate | The expiry date of the driving license is shown here.                    |
| result.address    | The address of the driving license holder is displayed here.             |
{% endtab %}
{% endtabs %}

&#x20; [![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/26e4691c2a916bcf2943)
