# Compress Video

## Introduction

High-resolution videos may often exceed the desired file size and may need to be compressed for uploading to the API service. This ensures that the video file size is reduced without affecting the quality of the video.

## API Usecase

The file size of high-resolution videos exceeds the desired file size so for it to be easily uploaded to the API service the file size of the video needs to be compressed that is where this service comes to work

## How to use the API

Upload the video in the form of a URL or from your device. Select the desired quality of the video and click submit to receive the desired result which is the compressed video that was provided.



The following exchange parameters can be used for Compressing Video Size:

## Input parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters     | Description                | Required/Optional |
| -------------- | -------------------------- | ----------------- |
| task           | to compress the video      | Required          |
| essentials     | contains essential data    | Required          |
| essentials.url | contains the array of urls | Required          |
| essentials.ttl | contains the expiry time   | Optional          |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/converters' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: <accessToken Received After Login>' \
{
    "task": "compressvideo",
    "essentials": {
        "url": "https://jsoncompare.org/LearningContainer/SampleFiles/Video/MP4/Sample-MP4-Video-File-for-Testing.mp4",
        "quality": "MEDIUM"
    }
}
```
{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| id                     | contains the id                           |
| ---------------------- | ----------------------------------------- |
| patronId               | your patron id                            |
| result                 | Retrieves the result of the given request |
| result.compressedVideo | Used to return the compressed video       |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
   "essentials":{
      "url":"https://jsoncompare.org/LearningContainer/SampleFiles/Video/MP4/Sample-MP4-Video-File-for-Testing.mp4",
      "quality":"MEDIUM"
   },
   "id":"6143201af6d4030eae050420",
   "patronId":"6140993ef6d4030eae0497fb",
   "task":"compressvideo",
   "result":{
      "compressedVideo":"https://persist.signzy.tech/api/files/211675217/download/07a29122eb6d4c37a442b81243a184c393c102d4af2b437089a6e1a5e539cf1a.mp4"
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

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../converters" method="post" summary="Compress Video" %}
{% swagger-description %}
This method is used to compress high-quality videos..Contains the 
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.ttl" type="string" %}
Expiry Time
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.quality" type="string" %}
Quality of the video to be compressed
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.url" type="string" %}
The url of the video to be compressed
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
The task that is to be carried out - compress video
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
     "result": {
       "compressedVideo": "... compressed video......"
     }
   }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{

   "task": "compressvideo",
   "essentials": {
     "url": "...video url......",
     "quality": "...quality......",
     "ttl": "expiry time"
   }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| Parameter Name   | Description                               |
| ---------------- | ----------------------------------------- |
| result           | Retrieves the result of the given request |
| compressed video | Used to return the compressed video       |
{% endtab %}
{% endtabs %}

Help & support

In case you have any queries, need clarification, or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:

support@signzy.com

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/fcbd630c2f71f506e14a)
