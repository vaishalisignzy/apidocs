# Doc Templator(N)

## Introduction

The Doc Templator product takes a .doc/.docx file with variables and JSON key-value pair as input and returns back a .docx file and pdf file with variables with proper values present in JSON.

## How to Use the API

The input is given as a .doc/.docx file it works in the form of a valid URL too. Fields names are to be entered manually that are to be validated. You can add more fields and also remove unnecessary ones.

## API Input Guidelines

* The URL (if provided) should be a valid URL
* The uploaded docx file should have the variables and JSON key-value pairs

Use the following exchange parameters for Doc Templator:

## Input parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name      | Description                          | Required/Optional |
| ------------------- | ------------------------------------ | ----------------- |
| task                | Takes .docx and returns a pdf with w | Required          |
| essentials          | contains the essential data          | Required          |
| essentials.url      | contains the array of urls           | Required          |
| essentials.jsonData | contains the essential json data     | Required          |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/converters'
--header 'authorization: '
--header 'content-type: application/json'
{
    "task": "docTemplator",
    "essentials": {
        "url": "......pdf url........",
        "jsonData": "...jsonData..."
    }
}'
```
{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name       | Description                                        |
| -------------------- | -------------------------------------------------- |
| id                   | a unique id is to be provided                      |
| patronId             | your patron ID                                     |
| task                 | the task thata API is ought to do                  |
| result               | Retrieves the output of the given request          |
| result.converteddocx | Gives the converted doc file in the form of a link |
| result.convertedPdf  | Gives the converted Pdf file in the form of a link |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
  "essentials": {
    "url": "https://preproduction-persist.signzy.tech/api/files/27932129/download/0b2374ed991a4a2c92ede22c41909307361765d8f8f24407b55d652e6d5390c2.docx",
    "jsonData": {
      "field_name": "Release Note"
    }
  },
  "id": "615e2c3cce57d15619dc90e8",
  "patronId": "60630eb6be09ef1b279ed142",
  "task": "docTemplator",
  "result": {
    "convertedDocx": "https://persist.signzy.tech/api/files/221302725/download/5c9d236f987946889a706cea8814ef6a0bce0673b9cd4b46aa888baa8e85a3f0.docx",
    "convertedPdf": "https://persist.signzy.tech/api/files/221302723/download/462be7a1259f400c9f1d29a93ec0fad84e8a1bb87960446d8be27eb77d44cf78.pdf"
  }
}
```


{% endtab %}
{% endtabs %}

## HTTP Response codes&#x20;

| Status code | Description                     |
| ----------- | ------------------------------- |
| **200**     | All response details are valid  |
| **404**     | Not found                       |
| **400**     | bad request                     |
| **401**     | unauthorized                    |
| **422**     | processable entity              |

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../converters" method="post" summary="Doc Templator" %}
{% swagger-description %}
This method is used to produce converted Doc and Pdf templates.
{% endswagger-description %}

{% swagger-parameter in="header" name="content-type" type="string" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="jsonData" type="string" %}
The json data to be inserted in the document
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.url" type="string" %}
The url of the doc to be converted
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
The task which is to be performed - docTemplator
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
     "result": {
         "convertedDocx": "..convertedDocx...",
         "convertedPdf": "..convertedPdf...",

      }
   }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{

   "task": "docTemplator",
   "essentials": {
     "url": "...docx url......",
     "jsonData" : {
         ..jsonData...
     }
```
{% endtab %}

{% tab title="Response Parameters" %}
| Parameter Name | Description                                 |
| -------------- | ------------------------------------------- |
| result         | Retrieves the result of the given request.  |
| convertedDocx  | Returns the converted doc with JSON values  |
| convertedPdf   | Returns the converted pdf with JSON values  |


{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/e71cffcaf3722f411df7)
