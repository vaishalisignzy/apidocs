# PDF to JPG

## Introduction

As API software can support multiple file formats, sometimes it may be necessary to convert from one file format to the other. This can be done with the help of converters in API. SIGNZY supports inter-conversion of multiple file formats as we will see in the following documents.

## API Use case

For example, if you have an Aadhar Card electronic copy that you have downloaded from the UIDAI website, chances are likely that it will be in PDF format, but the system only requires a jpg image. In such cases, converters are effective and do not require you to manually convert to jpg.

## API Input Guidelines

* Only single-page PDFs can be converted
* The PDF should be of good quality
* API only accepts PDFs as the input

## Input parameters & Sample cURL request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description                          | Required/Optional |
| -------------- | ------------------------------------ | ----------------- |
| task           | task performed to convert pdf to jpg | Required          |
| essentials     | contains the essential input data    | Required          |
| essentials.ttl | It is the expiry time                | Optional          |
| essentials.url | contains the array of urls           | Required          |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/converters' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: <accessToken Received After Login>' \
{
    "task": "pdftojpg",
    "essentials": {
        "urls": [
            "https://preproduction-persist.signzy.tech/api/files/28188715/download/3afacea0ee27437c869e7c66dbabdebdeeb5d6b58b2445ebb7c3adf5d3f7aad1.pdf"
        ],
        "ttl": "10 mins"
    }
}
```
{% endtab %}
{% endtabs %}

## Output Parameters & Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name   | Description                                    |
| ---------------- | ---------------------------------------------- |
| id               | a unique ID is to be provided                  |
| patronId         | your patron ID                                 |
| result           | Retrieves the output of the given request      |
| result.pdftoJpgs | Retrieves the image URLs of the converted pdfs |
{% endtab %}

{% tab title="Sample API response " %}
```
{
   "essentials":{
      "urls":[
         "https://preproduction-persist.signzy.tech/api/files/28188715/download/3afacea0ee27437c869e7c66dbabdebdeeb5d6b58b2445ebb7c3adf5d3f7aad1.pdf"
      ],
      "ttl":"10 mins"
   },
   "id":"61443bf3f6d4030eae053282",
   "patronId":"6140993ef6d4030eae0497fb",
   "task":"pdftojpg",
   "result":{
      "pdftoJpgs":[
         "https://persist.signzy.tech/api/files/211972391/download/3002576db12641c5a73cd6919b924139ee72a15a3b9c44238bf655c561630325.jpg"
      ]
   }
}
```


{% endtab %}
{% endtabs %}



{% swagger baseUrl="https://signzy.tech/" path="/api/v2/patrons/...patronID.../converters" method="post" summary="PDF to JPG" %}
{% swagger-description %}
This method allows you to convert PDF to JPG
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
This contains the access token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.ttl" type="string" %}
Expiry Time
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.urls" type="string" %}
Array of urls
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains the essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
The type of task performed - pdf to jpg
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
     "result": {
       "pdftoJpgs": ["... array of Image Urls......"]
     }
   }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{

   "task": "pdftojpg",
   "essentials": {
     "urls": ["...array of PDF URLs......"],
     "ttl": "expiry time"
   }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| Parameter Name | Description                                    |
| -------------- | ---------------------------------------------- |
| result         | Retrieves the output of the given request      |
| pdftojpgs      | Retrieves the image URLs of the converted pdfs |
{% endtab %}
{% endtabs %}

Help & support

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:

&#x20;[![](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/d01f7d2b581c9eb92ab6)



