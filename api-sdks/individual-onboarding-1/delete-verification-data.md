# Delete Verification Data

## Introduction

This API is used whenever any information provided by the user turns out to be irrelevant and needs to be removed or in cases where due to some discrepancies, the client information needs to be deleted from the system as a whole.

How to use the API


You will need to login before sending request. You are required to pass the access token received from the login call, as authorization header in the Individual Onboarding DELETE Request along with essentials and task

Once user get the verification response , he/she can delete verificatioin data from database using tis request.

Use the following exchange parameters for Individual Onboarding Delete Request:

## Input Parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters           | Descriptions                    |
| -------------------- | ------------------------------- |
| task                 | to delete the verification data |
| essentials           | essential data                  |
| essentials.requestId |                                 |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl https://signzy.tech/api/v2/patrons/....patronid.../individualonboardings
--header 'authorization: '
--header 'content-type: application/json'
{
    "task": "deleteRequest",
    "essentials": {
        "requestId": "...requestId.."
    }
}
```
{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameters | Description |
| ---------- | ----------- |
|            |             |
|            |             |
|            |             |


{% endtab %}

{% tab title="Sample API Response" %}
```
// Some code
```


{% endtab %}
{% endtabs %}

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../individualonboardings" method="post" summary="Delete Verification data" %}
{% swagger-description %}
This method is used for individual onboarding delete request..
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

{% endtab %}
{% endtabs %}

