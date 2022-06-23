# Check Status by Transaction ID

## Introduction

In the API Batch mode request, once the details have been confirmed, a unique Transaction ID is generated for the user who initiates the request. Using this unique ID, users can enquire about the time and details it takes for the requested batch to be processed.

How to use the API


You will need to login before sending Court Cases Count request. You are required to pass the access token received from the login call, as authorisation header in the API Batch Mode Fetch Transaction request along with other parameters.

Use the following exchange parameters for API Batch Mode request:

## Input parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name           | Description                      | Required/Optional |
| ------------------------ | -------------------------------- | ----------------- |
| task                     | checks the status transaction ID | Required          |
| essentials               | contains the essential data      | Required          |
| essentials.transactionId | contains the transaction id data | Required          |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/batchmodes' \
  --header 'authorization: <Access-Token>' \
  --header 'content-type: application/json' \
{
    "task": "fetchTransaction",
    "essentials": {
        "transactionId": "...transactionId..."
    }
}
```
{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description |
| -------------- | ----------- |
|                |             |


{% endtab %}

{% tab title="Sample API Response" %}
```
// Some code
```


{% endtab %}
{% endtabs %}



{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../batchmodes" method="post" summary="Check Status By Transaction ID" %}
{% swagger-description %}
This method is used to check the status of the transaction request.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
 Type of task performed - fetchTransaction
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
 Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.transactionId" type="string" %}
The transaction Id which is to be searched.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
 	"result": {
        "url": "..url..",
        "apiName": "..apiName..",
        "maxRows": ...maxRows...,
        "rowProcessed": ...rowProcessed...,
        "success": ...success...,
        "error": ...error...,
        "comments": "...comments...",
        "patronId": "...patronId...",
        "clientRequestId": "...clientRequestId...",
        "createdTime": ...createdTime...,
        "expiryTime": ...createdTime...,
        "dontProcess": ...dontProcess...,
        "complete": ....complete...,
        "outputUrl": "...outputUrl...",
        "completedTime": ...completedTime...
 	}
 }
            
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
    "task" : "fetchTransaction",
    "essentials": {
        "transactionId": "...transactionId...",
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME         | DESCRIPTION                                                                                   |
| ---------------------- | --------------------------------------------------------------------------------------------- |
| result                 | This contains the final response parameters.                                                  |
| result.url             | The parameter contains the rows of image URLs for the uploaded images.                        |
| result.apiName         | The name of the API for which batch request is being performed.                               |
| result.maxRows         | The maximum number of rows to be processed in the batch request are displayed here.           |
| result.rowProcessed    | The number of rows that have been processed for the batch request at the time of the enquiry. |
| result.success         | The success message is displayed by this parameter.                                           |
| result.error           | The error messages, if any, are displayed in this parameter.                                  |
| result.comments        | This parameter displays any additional comments about the batch request.                      |
| result.patronId        | This parameter contains the userId parameter of login request.                                |
| result.clientRequestId | This contains the transaction ID that was received during input batch request.                |
| result.createdTime     | The time when the request was created is shown here.                                          |
| result.expiryTime      | The approximate expiry time of the batch process is shown here.                               |
| result.dontProcess     | This parameter contains details about why the batch process cannot be processed.              |
| result.complete        | The completion details are displayed here.                                                    |
| result.outputUrl       | This parameter contains the output URLs of the completed request.                             |
| result.completedTime   | The total time taken to complete the batch request is displayed here.                         |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/0cacee6ec0b65bf700dc)

