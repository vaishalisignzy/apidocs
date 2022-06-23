---
description: Use this API to cancel a transaction that is in the INITIALIZED state.
---

# Cancel Charge eMandate

## Introduction

Use this API to cancel a transaction that is in the INITIALIZED state.&#x20;

## API Use-case

The purpose of this API is to cancel payment of an ON\_DEMAND e-mandate

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
| paymentId      | The unique ID of the payment  | Required |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl --location --request POST 'https://api.signzy.app/api/v3/eNach/eMandates/:subReferenceId/charge/:paymentId/cancel' \
--header 'Authorization: ..authKey..'
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description                               |
| -------------- | ----------------------------------------- |
| result.status  | eMandate response status                  |
| result.message | eMandate charge cancel message            |
| result.payment | Payment object containing payment details |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
  "status": "OK",
  "message": "Subscription charge cancelled",
  "payment": {
    "paymentId": 1234,
    "referenceId": 00000,
    "subReferenceId": 0000,
    "cfOrderId": 0101101,
    "currency": "INR",
    "amount": 100,
    "cycle": 5,
    "status": "CANCELLED",
    "remarks": null,
    "scheduledOn": "2021-09-13",
    "addedOn": "2021-09-09 11:05:19",
    "retryAttempts": 0,
    "failureReason": null
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



{% swagger baseUrl="https://api.signzy.app" path="/api/v3/eNach/eMandates/:subReferenceId/charge/:paymentId/cancel" method="post" summary="Cancel charge eMandate" %}
{% swagger-description %}
This method cancels charge of an eMandate from subReferenceId, paymentId given in path
{% endswagger-description %}

{% swagger-parameter in="path" name="subReferenceId" required="true" %}
Unique eMandate ID generated on creation of the eMandate
{% endswagger-parameter %}

{% swagger-parameter in="path" name="paymentId" required="true" %}
Unique payment ID 
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful eMandate charge" %}
```
{
  "status": "OK",
  "message": "Subscription charge cancelled",
  "payment": {
    "paymentId": ..paymentId..,
    "referenceId": ..referenceId..,
    "subReferenceId": ..subReferenceId..,
    "cfOrderId": ..cfOrderId..,
    "currency": "INR",
    "amount": ..amount..,
    "cycle": ..cycle..,
    "status": "CANCELLED",
    "remarks": null,
    "scheduledOn": "2021-09-13",
    "addedOn": "2021-09-09 11:05:19",
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
