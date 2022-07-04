# Delete Verification Data

## Introduction

This API is used whenever any information provided by the entity/organisation turns out to be irrelevant and needs to be removed or in cases where due to some discrepancies, the clients’ information needs to be deleted from the system as a whole.

## How to use the API

You will need to login before sending request. You are required to pass the access token received from the login call, as authorization header in the Entity Onboarding DELETE Request request along with essentials and task

Use the following exchange parameters for Entity Onboarding Delete Request

## Input Parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
|                      |                                 |
| -------------------- | ------------------------------- |
| task                 | to delete the verification data |
| essentials           | contains the input data         |
| essentials.requestId | contains the request Id         |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/entityonboardings'
--header 'authorization: '
--header 'content-type: application/json'
'{
    "task": "deleteRequest",
    "essentials": {
        "requestId": "...requestId.."
    }
}'
```
{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameters  | Description |
| ----------- | ----------- |
|             |             |
|             |             |
|             |             |


{% endtab %}

{% tab title="Sample API Response" %}
```
// Some code
```


{% endtab %}
{% endtabs %}

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../entityonboardings" method="post" summary="Delete Verification data" %}
{% swagger-description %}
This method is used for entity onboarding delete request..
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - delete Request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.requestID" type="string" %}
Contains the unique delete request ID	
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "result": {
        "message" : "User with that RequestId is deleted",
        "statusCode" : 200
    }
}


```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
	"task": "deleteRequest",
	"essentials": {
        "requestId": "..requestId...."
    }
}

```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME    | DESCRIPTION                                            |
| ----------------- | ------------------------------------------------------ |
| result            | The final response parameters are displayed as output. |
| result.message    | User with that request ID is deleted.                  |
| result.statusCode | The status code is displayed - 200                     |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/1f2f9ccbe8bba3c21971)

