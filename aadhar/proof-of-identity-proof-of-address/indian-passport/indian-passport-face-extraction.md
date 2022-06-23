# Indian Passport Face Extraction(404)

### Introduction

The Face Extraction API can be used to extract only the image of the passport holder from the image/image URL of the Indian Passport



### API Usecase

This Face extraction API uses the image, mage URL,  or pdf file that is uploaded to the API for extracting the image of the passport holder. This helps in auto-generating the image of a user without having to manually provide the image. API responds with a URL with just the face, found from the passport.

### How to call the API

Before going for Auto reading, you first need to create an Identity object. For best results, please make sure that the image you use fits tightly in camera view and is horizontally aligned.&#x20;

### API Input Guidelines

* The Image should be well lit
* Image should be less than 2MB in size
* API accepts only image, pdf, or URLs of the image

### Input Parameters

| Parameter Name | Description                                                                                |
| -------------- | ------------------------------------------------------------------------------------------ |
| accessToken    | (required, string) this is provided by the identities API                                  |
| task           | this value always remains fixed for Aadhaar extraction API, it is always `AutoRecognition` |
|                | ``                                                                                         |

### Output Parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

****

### Sample CURL Request

**Step 1**: Hit Identities API

```
```

**Step 2:** Hit Snoops API and receives a response

```
```

###

### Sample API Response

```
```



### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorized                           |
| **422**     | processable entity                     |
|             |                                        |

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/snoops" method="post" summary="Passport Face Extraction" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/snoops`

\




\


This method allows the face of the individual to be extracted from Passport
{% endswagger-description %}

{% swagger-parameter in="body" name="service" type="string" %}
type - identity 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="itemID" type="object" %}
identity Item ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - Face extraction
{% endswagger-parameter %}

{% swagger-parameter in="body" name="accessToken" type="object" %}
Identity access token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the image/image URL of the Passport from which the face has to be extracted
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
        "service": "Identity",
        "itemId": "..item id..",
        "task": "faceExtraction",
        "essentials": {
          "url": "...image url ..."
        },
        "accessToken": "...access token...",
        "id": "...id...",
        "response": {
          "url": "...image url...",
          "id": 6069,
          "result": {
            "cropped": "...extracted face image url...."
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
      "itemId":"<Identity-object-id>",
      "task":"faceExtraction",
      "accessToken":"<Identity-access-token>",
      "essentials":{
        "url": "..url-of-image-from-where-face-needs-to-be-extracted"
      }
```
{% endtab %}

{% tab title="Response Parameters" %}
| **PARAMETER NAME**     | **DESCRIPTION**                                                   |
| ---------------------- | ----------------------------------------------------------------- |
| service                | Type of Signzy service - “identity extraction”                    |
| itemId                 | Contains the identity item id                                     |
| task                   | The type of task performed - “face Extraction”                    |
| essentials             | Contains the essential output data                                |
| essentials.url         | The URL of the image that was uploaded for face extraction.       |
| essentials.accessToken | Contains the access token that was received from identity request |
| essentials.Id          | Contains the unique Id received from the identity request.        |
| response               | Contains the output files                                         |
| response.result        | Contains the extracted face URL                                   |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/18304106c18bf8ebe77a)
