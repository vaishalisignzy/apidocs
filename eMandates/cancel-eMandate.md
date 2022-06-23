---
description: Use this API to cancel the eMandate.
---

# Cancel eMandate

## Introduction

Use this API to cancel the eMandate. After a successful cancellation, the eMandate status will move to "CANCELLED", and the customer will no longer be charged. eMandate, once cancelled, cannot be reactivated.

## API Use-case

The purpose is to cancel an e-mandate

How to use the API
------------------

The users need to give inputs as per the input guidelines below.

## API Input Guidelines

* Pass a valid JSON body
* Pass a valid Authorization Key in headers

## Input parameters & Sample cURL request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description                   |          |
| -------------- | ----------------------------- | -------- |
| subReferenceId | The unique ID of the eMandate | Required |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl --location --request POST 'https://api.signzy.app/api/v3/eNach/eMandates/:subReferenceId/cancel' \
--header 'Authorization: ..authKey..'
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description              |
| -------------- | ------------------------ |
| result.status  | eMandate response status |
| result.message | eMandate cancel message  |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "result": {
        "status": "OK",
        "message": "Subscription Cancelled"
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
| **400**     | Bad Request                     |
| **401**     | Unauthorized                    |
| **403**     | Forbidden                       |
| **422**     | Unprocessable entity            |



{% swagger baseUrl="https://api.signzy.app" path="/api/v3/eNach/eMandates/:subReferenceId/cancel" method="post" summary="Cancel eMandate" %}
{% swagger-description %}
This method cancels an eMandate from subReferenceId given in path
{% endswagger-description %}

{% swagger-parameter in="path" name="subReferenceId" required="true" %}
Unique eMandate ID generated on creation of the eMandate
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful eMandate creation" %}
```
{
    "result": {
        "status": "OK",
        "message": "Subscription Payment",
        "payment": {
            "paymentId": ..paymentId..,
            "referenceId": ..referenceId..,
            "cfOrderId": ..cfOrderId.,
            "subReferenceId": ..subReferenceId..,
            "currency": "INR",
            "amount": ..amount..,
            "cycle": ..cycle..,
            "status": "..status..",
            "remarks": null,
            "scheduledOn": null,
            "addedOn": "2022-03-29 18:49:20",
            "retryAttempts": 0,
            "failureReason": null
        }
    }

```
{% endswagger-response %}
{% endswagger %}

\


[\
](https://docs.cashfree.com/edit/subscription-status)
