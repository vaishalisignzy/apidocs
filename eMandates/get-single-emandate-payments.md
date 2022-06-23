---
description: Use this API to get details of a particular payment of the eMandate.
---

# Get Single eMandate Payments

## Introduction

A description of all the possible statuses for a subscription payment is available in the table below.

## API Use-case

The purpose is to get single payment details of an e-mandate

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
| paymentId      | A unique Id for the payment.  | Required |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl --location --request GET 'https://api.signzy.app/api/v3/eNach/eMandates/:subReferenceId/payments/:paymentId' \
--header 'Authorization: ..authKey..'
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description                                |
| -------------- | ------------------------------------------ |
| result.status  | eMandate response status                   |
| result.message | eMandate payments message                  |
| result.payment | Object containing eMandate payment details |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "result": {
        "status": "OK",
        "message": "Subscription Payment",
        "payment": {
            "paymentId": 12345,
            "referenceId": 000000,
            "cfOrderId": 00000,
            "subReferenceId": 00000,
            "currency": "INR",
            "amount": 5,
            "cycle": 1,
            "status": "PENDING",
            "remarks": null,
            "scheduledOn": null,
            "addedOn": "2022-03-29 18:49:20",
            "retryAttempts": 0,
            "failureReason": null
        }
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



{% swagger baseUrl="https://api.signzy.app" path="/api/v3/eNach/eMandates/:subReferenceId/payments/:paymentId" method="get" summary="Get eMandate Single Payments Details" %}
{% swagger-description %}
This method gets single eMandate payment details from subReferenceId, paymentId
{% endswagger-description %}

{% swagger-parameter in="path" name="subReferenceId" required="true" %}
Unique eMandate ID generated on creation of the eMandate
{% endswagger-parameter %}

{% swagger-parameter in="path" name="paymentId" required="true" %}
The unique payment ID to return results from.
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
}
```
{% endswagger-response %}
{% endswagger %}

## Notes

* Payment Id is generated at every payment.
* Cycle indicates after how many intervals was this payment processed.
* Payment status field values are described in payments status table below.

## Payment Status

| Status  | Description                                                                                                   |
| ------- | ------------------------------------------------------------------------------------------------------------- |
| SUCCESS | Payment for the eMandate was processed successfully.                                                          |
| PENDING | Payment for the eMandate was attempted but not yet marked successful. This status is specific for e-mandates. |
| FAILED  | The payment failed for the eMandate.                                                                          |

\


[\
](https://docs.cashfree.com/edit/subscription-status)
