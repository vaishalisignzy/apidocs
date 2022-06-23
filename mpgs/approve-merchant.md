# Approve Merchant

## Introduction

The MPGS Approve Merchant API gives user access to approve any changes (including creation) to the merchant's configuration created by any of the operations described above. If you approve the changes and MasterCard Payment Gateway successfully validates the changes, then the changes take effect immediately.To do so, the API takes MSO Id and Merchant Id as input.

How to use the API


You will need to log in before sending MPGS request. You are required to pass the access token received from the login call, as an authorization header in the request for Risk API along with other parameters.

Use the following exchange parameters for Approve Merchant:

### Input parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

### Output Parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

## Sample cURL Response

```
//yet to extract
```

## Sample API response

```
//yet to extract
```







{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../mpgs" method="post" summary="Approve Merchant data" %}
{% swagger-description %}
This method is used for approve merchant information.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - merchant Approve
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.msoId" type="string" %}
Contains the MSO ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.merchantId" type="string" %}
The IDof the merchant
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "result": "SUCCESS",
    "merchantId":"...merchantId..."
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
    "task": "merchantapprove",
    "essentials": {
        "msoId": "...msoId...",
        "merchantId": "...merchantId..."
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME  | DESCRIPTION                                          |
| --------------- | ---------------------------------------------------- |
| result          | The result is displayed in the form of Success/Fail. |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/9c843e2a9e3982f099d3)
