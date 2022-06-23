# Digital Signature on Pdf Validator(N)

Introduction


Sometimes certain documents like Aadhar, PAN might need to be digitally signed for the authenticity of the document. This service helps users with verification without the use of any third-party API, making the process more convenient and faster.

## API Usecase

This API is used for validating the digital signatures on the PDF document.

## How to use the API

Upload the file or paste the URL of the pdf document which needs to get their digital signatures verified.



The following exchange parameters can be used for creating a Digital Signature on Pdf Validator:&#x20;

## Input Parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description                              | Required/Optional |
| -------------- | ---------------------------------------- | ----------------- |
| task           | to validate the digital signature on pdf | Required          |
| essentials     | contains the essential input data        | Required          |
| essentials.url | contains the array of urls               | Required          |
| essentials.ttl | it is the expiry time                    | Optional          |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl https://signzy.tech/api/v2/patrons/<patron-id>/converters
--header 'authorization: '
--header 'content-type: application/json'
{
    "task": "validatedsc",
    "essentials": {
        "url": "......pdf url........",
        "ttl": "...expiry times..."
    }
}
```
{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name    | Description                                                |
| ----------------- | ---------------------------------------------------------- |
| id                | a unique id is to be provided                              |
| patronId          | your patron ID                                             |
| task              | the task that this API is ought to do                      |
| result            | Retrieves the output of the given request                  |
| result.validDsc   | shows if the Dsc is valid in the form of 'True' or 'False' |
| result.dscDetails | gives the details of the dsc                               |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
  "essentials": {
    "url": "https://staging-persist.signzy.tech/api/files/3722502/download/1c00b172fafc474c80575d8fd091009106f550b183544d2baae5d576701e9fb1.pdf"
  },
  "id": "615e2c1da6d6d85a3a48ceb3",
  "patronId": "60630eb6be09ef1b279ed142",
  "task": "validatedsc",
  "result": {
    "validDsc": false,
    "dscDetails": []
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



{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../converters" method="post" summary="Digital Signature Validator" %}
{% swagger-description %}
This method is used to validate digital signature on PDF file.
{% endswagger-description %}

{% swagger-parameter in="header" name="content-type" type="string" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="url" type="string" %}
Contains the URL of the pdf which needs to be validated
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
The task that is performed - validate dsc
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
     "result": {
         "validDsc": true/false,
         "dscDetails": {
          "documentRevision": ..documentRevision...,
          "doesSignatureCoversFullDocument": ...doesSignatureCoversFullDocument...,
          "totalDocumentRevisions": ..totalDocumentRevisions...,
          "certificateInfo": [
            {
              "certificateNumber": 0,
              "subject": "...subject...",
              "certificateValidity": "...certificateValidity...",
              "certificateTimeValidity": "...certificateTimeValidity...",
              "validFrom": "2017-01-25 16:44:13.00",
              "issuer": "...issuer...",
              "validTo": "...validTo..."
            }
          ],
          "IntegrityCheck": true
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

   "task": "validatedsc",
   "essentials": {
     "url": "...pdf url......"
   }
  }
```
{% endtab %}

{% tab title="Response Parameter" %}
| Parameter Name  | Description                                                                               |
| --------------- | ----------------------------------------------------------------------------------------- |
| result          | Returns the result of the given request with details like valid details, dsc details etc. |
| certificateInfo | Used to retrieve the details of the certificate pdf                                       |
| IntegrityCheck  | Checks file integrity and returns whether true or false                                   |
{% endtab %}
{% endtabs %}



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/baea0385a350ea188e60)
