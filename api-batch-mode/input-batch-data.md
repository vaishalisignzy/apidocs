# Input Batch Data

## Introduction

Sometimes it may be necessary to extract details of multiple individuals at the same time. For example, an organisation requires the PAN card details of all employees for IT filing. While the APIs we have seen previously are capable of handling this, they can only process one request at a time and this can be cumbersome at times to extract the details of one individual at a time.

API Usecase


Using the API Batch Mode Save Request service by Signzy, users can extract the details of multiple ID holders at a given time.The output is usually a transaction ID and the details once retrieved are sent as a CSV file to the email ids input to the API.  Currently, the API supports the call request for 5 API services but will be supporting more in the future. The 5 APIs are:

1. PAN Verification API
2. Driving Licence Verification API
3. VoterID Verification API
4. Aadhaar UID Masker API&#x9;
5. PAN to GST API

## How to use the API

You will need to [login](https://docs-staging.signzy.tech/) before sending Court Cases Count request. You are required to pass the access token received from the login call, as authorization header in the API Batch Mode Save request along with other parameters.

Use the following exchange parameters for API Batch Mode request:

## Input Parameters and Sample cURL Request&#x20;

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name          | Description                       | Required/Optional |
| ----------------------- | --------------------------------- | ----------------- |
| task                    | to extract the user information   | Required          |
| essentials              | contains the essential input data | Required          |
| essentials.url          | contains the array of urls        | Required          |
| essentials.apiName      | contains the api name             | Optional          |
| essentials.emailId      | contains the email ids            | Required          |
| essentials.emailSubject | contains the email subject        | Optional          |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/batchmodes' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: OEb1luRXZ5KqDAtu4QKEF0OmpZ9Xtg92B0UUeroXBdWuHH6bdC9DoUQNCgtefXGr' \
{
    "task": "save",
    "essentials": {
        "url": "https://preproduction-persist.signzy.tech/api/files/29369731/download/c995eac5cc5e469c8fa7b7893fa94475e9993ee8dc484dc89280463e23c6888f.csv",
        "apiName": "panVerification",
        "emailId": [
            "sadhika@hotmail.com"
        ],
        "emailSubject": "product issue"
    }
```
{% endtab %}
{% endtabs %}

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../batchmodes" method="post" summary="Input API Batch data" %}
{% swagger-description %}
This method is used to input API Batch data
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
 Type of task performed - save
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
 Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.url" type="string" %}
CSV file URL of the data which has to be processed in batch mode	
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.apiName" type="string" %}
Name of the API to be hit in batch mode	
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.emailId" type="array" %}
List of Email IDs which where the mail to be sent once the batch request is processed
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.emailSubject" type="string" %}
Subject of the mail which is to be sent once the batch request is processed
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.callbackUrl" type="string" %}
URL where the data is to be posted once the batch request is processed
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
 	"result": {
        "transactionId": "..transactionId.."
 	}
 }

```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
    "task" : "save",
    "essentials": {
        "url": "...url...",
        "apiName": "...apiName...",
        "emailId": ["...emailId..."],
        "emailSubject" : "...emailSubject...",
        "callbackUrl": "...callbackUrl..."
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME       | DESCRIPTION                                                                                    |
| -------------------- | ---------------------------------------------------------------------------------------------- |
| result               | This holds the final response parameters.                                                      |
| result.transactionId | This parameter generates a unique transaction Id which can be used to track the batch request. |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/0cacee6ec0b65bf700dc)

\
