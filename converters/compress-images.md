# Compress Images

Introduction


Image compression is mostly done to reduce the file size of the image if it goes beyond the acceptable range. This is mostly done in cases where the image to be uploaded is greater than the acceptable limit of the API service. So if the acceptable limit for the image is 2 MB and the original image size is 11 MB, this technique is used.

## API Usecase&#x20;

When image compression capabilities are integrated directly into an application, there are no third-party dependencies. Image files can be automatically shrunk to manageable sizes using image compression API, which facilitates automation significantly.

## How to call the API

## API input guidelines

You can upload any JPEG or PNG image to our API to compress it. We will automatically detect the type of image and optimize it accordingly. Compression will start as soon as you upload a file or provide the URL to the image.

Use the following exchange parameters for Compressing Image File Size:



## Input parameters & Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description                       | Required/Optional |
| -------------- | --------------------------------- | ----------------- |
| task           | to compress the image             | Required          |
| essentials     | contains the essential input data | Required          |
| essentials.url | contains the array of urls        | Required          |
{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/converters' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: <accessToken Received After Login>' \
{
    "task": "compressimage",
    "essentials": {
        "url": "https://preproduction-persist.signzy.tech/api/files/28013029/download/241e9065d59d4593ad105d48caa767eacc0fd63ced55439aba5f983ebba5ebec.png"
    }
}
```


{% endtab %}
{% endtabs %}

## Output Parameters & Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name         | Description                                        |
| ---------------------- | -------------------------------------------------- |
| id                     | a unique ID is to be provided                      |
| patronId               | your patron ID                                     |
| result                 | Retrieves the output of the given request          |
| result.compressedimage | Retrieves the image URLs of the compressed version |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
   "essentials":{
      "url":"https://preproduction-persist.signzy.tech/api/files/28013029/download/241e9065d59d4593ad105d48caa767eacc0fd63ced55439aba5f983ebba5ebec.png"
   },
   "id":"6143228bf6d4030eae0504ef",
   "patronId":"6140993ef6d4030eae0497fb",
   "task":"compressimage",
   "result":{
      "compressedImage":"https://persist.signzy.tech/api/files/211681441/download/5b4edf8a240a4a70b05d10f741df76509be8e19a52e84586af9451cc44f15ffb.png"
   }
}
```


{% endtab %}
{% endtabs %}



{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../converters" method="post" summary="Compress Images" %}
{% swagger-description %}
This method is useful for image compression.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Contains the access token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.ttl" type="number" %}
Expiry Time
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.urls" type="string" %}
image URL of user input image
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Conttains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - compress image
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
     "result": {
       "compressedImage": "... compressed image url......"
     }
   }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{

   "task": "compressimage",
   "essentials": {
     "url": "...image url......",
     "ttl": "expiry time"
   }
  }
```

Using image compression is a great way to ensure freedom from hassle-free manual conversions and convenient management of data.

Help & support

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:

support@signzy.com
{% endtab %}

{% tab title="Response Parameter" %}
| Parameter Name  | Description                               |
| --------------- | ----------------------------------------- |
| result          | Generates the result of the given request |
| compressedImage | Returns the URL of the compressed image   |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/3b1dae9101e4ea59d595)
