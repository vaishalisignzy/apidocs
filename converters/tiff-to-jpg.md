# TIFF to JPG

## Introduction

TIFF (short for Tagged Image File Format) is an industry standard designed for handling raster or bitmapped images. TIFF files can be saved in a variety of color formats and in various forms of compression. TIFFs use lossless compression to maintain image integrity and clarity. Here, we convert from TIFF to the JPG format by calling the API. Sometimes the uploaded document might be a high-resolution image in TIFF format. We can make use of a converter to extract the jpg file format as required.

## API Usecase

The TIFF to JPG converter extracts the needed information from the high resolution TIFF file in the JPG format.

## How to call the API



## API Input Guidelines

* Place the TIFF files in the Input Folder.
* Click the 'Submit' button

## Input parameters & sample cURL request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name  | Description                                  | Required/Optional |
| --------------- | -------------------------------------------- | ----------------- |
| task            | task performed to convert TIFF format to JPG | Required          |
| essentials      | contains the essential input data            | Required          |
| essentials.urls | contains the array of of urls                | Required          |
| essentails.ttl  | contains the expiry time                     | Optional          |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/converters' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: <accessToken Received After Login>' \
{
    "task": "tifftojpg",
    "essentials": {
        "urls": [
            "https://preproduction-persist.signzy.tech/api/files/28014407/download/40d6bf16521847c8bacf0ca2f1db203604978c79826448be9ee404fc55402492.tiff"
        ],
        "ttl": "10 mins"
    }
}
```


{% endtab %}
{% endtabs %}

## Output Parameters & Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name     | Description                                           |
| ------------------ | ----------------------------------------------------- |
| id                 | a unique ID is to be provided                         |
| patronId           | your patron ID                                        |
| results            | Retrieves the output of the given request             |
| results.tifftoJpgs | Retrieves the image URLs of the converted TIFF format |
{% endtab %}

{% tab title="Sample API response" %}
```
{
   "essentials":{
      "urls":[
         "https://preproduction-persist.signzy.tech/api/files/28014407/download/40d6bf16521847c8bacf0ca2f1db203604978c79826448be9ee404fc55402492.tiff"
      ],
      "ttl":"10 mins"
   },
   "id":"6143244cf6d4030eae050569",
   "patronId":"6140993ef6d4030eae0497fb",
   "task":"tifftojpg",
   "result":{
      "tifftoJpgs":[
         "https://persist.signzy.tech/api/files/211685143/download/1762a67039bb43aca18d74e0db73930f69577e19713f4bc3ad0cff5eb9dc2f32.jpeg"
      ]
   }
}
```


{% endtab %}
{% endtabs %}



{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../converters" method="post" summary="TIFF to JPG" %}
{% swagger-description %}
This method allows you to convert TIFF to JPG files.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Access token is passed here
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.ttl" type="string" %}
Expiry Time
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.urls" type="array" %}
array of TIFF URLs
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
The task to be performed - tiff to jpg
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
     "result": {
       "tifftoJpgs": ["... array of Image Urls......"]
     }
   }
```
{% endswagger-response %}
{% endswagger %}

| Name       | Description                                |
| ---------- | ------------------------------------------ |
| result     | Used to retrieve the output of the request |
| tifftojpgs | Returns an array of converted jpgs         |

{% tabs %}
{% tab title="Request Schema" %}
```
{

   "task": "tifftojpg",
   "essentials": {
     "urls": ["...array of TIFF URLs......"],
     "ttl": "expiry time"
   }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| Parameter Name | Description                                             |
| -------------- | ------------------------------------------------------- |
| result         | Used to retrieve the output of the request              |
| tifftojpgs     | Returns an array of image URLs for converted TIFF files |
{% endtab %}
{% endtabs %}

Help & support

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:

support@signzy.com

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/ee65c5b08beca84bc6f4)
