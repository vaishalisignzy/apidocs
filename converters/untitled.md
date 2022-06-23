# Compress PDF

## Introduction

Similar to the requirement for image compression, PDF file sizes may also need to be compressed depending on the necessity of the API service. The API can reduce a PDF file size without sacrificing the quality. Maintaining the balance between smaller file sizes and good quality is our highest priority. The PDF output of our PDF Compressor API works well with our other APIs. The PDF Compressor API can optimize PDF files of any size. It works perfectly well with documents that contain images and text.

## API Usecase

The PDF Compressor API optimizes a PDF document to reduce its size. This PDF optimization is ideal when you are constrained by file size limitations without losing much on file quality.

## API Input Guidelines

* The file type should be in PDF
* You can upload the PDF from the device or paste the URL to convert



## Input parameters & Sample cURL request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description                          | Required/Optional |
| -------------- | ------------------------------------ | ----------------- |
| task           | The task here is to compress the PDF | Required          |
| essentials     | contains the essential input data    | Required          |
| essentials.url | url of the pdf to be compressed      | Required          |
| essentials.ttl | Expiry time                          | Optional          |
{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/converters' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: <accessToken Received After Login>' \
{
    "task": "compresspdf",
    "essentials": {
        "url": "https://preproduction-persist.signzy.tech/api/files/28011329/download/49b3726a18484ed6a7b8f101668171ae7d863263924f474d85a391009c229ca0.pdf"
    }
}
```
{% endtab %}
{% endtabs %}

## Output Parameters & Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name       | Description                                           |
| -------------------- | ----------------------------------------------------- |
| id                   | a unique ID is to be provided                         |
| patronId             | your patron ID                                        |
| result               | Retrieves the output of the given request             |
| result.compressedPdf | Retrieves the image URLs of the converted TIFF format |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
   "essentials":{
      "url":"https://preproduction-persist.signzy.tech/api/files/28011329/download/49b3726a18484ed6a7b8f101668171ae7d863263924f474d85a391009c229ca0.pdf"
   },
   "id":"61432130f6d4030eae050480",
   "patronId":"6140993ef6d4030eae0497fb",
   "task":"compresspdf",
   "result":{
      "compressedPdf":"https://persist.signzy.tech/api/files/211678119/download/1ea1529609644adf9ff7a2bc113c6ee4120b55bd8e3540dcaca1fd0ee77c2332.pdf"
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

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../converters" method="post" summary="Compress PDF" %}
{% swagger-description %}
This method allows you to compress PDFs.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Contains the authorization token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.ttl" type="string" %}
Expiry time
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.url" type="string" %}
url of the pdf to be compressed
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains the essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
The task that is carried out here - compress pdf
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
     "result": {
       "compressedPdf": "... compressed pdf url......"
     }
   }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{

   "task": "compresspdf",
   "essentials": {
     "url": "...pdf url......",
     "ttl": "expiry time"
   }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| Parameter Name | Description                               |
| -------------- | ----------------------------------------- |
| result         | Retrieves the result of the given request |
| compressedPdf  | Returns the compressed pdf                |
{% endtab %}
{% endtabs %}

Help & support

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:

support@signzy.com

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/d720a0535b80d9c00445)
