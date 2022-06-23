---
description: Use this API to retry the last failed payment for an eMandate in ONHOLD state.
---

# Retry Payment

## Introduction

Use this API to retry the last failed payment for an eMandate in ONHOLD state. On a successful retry, the eMandate gets activated.

## API Use-case

The purpose of this API is to retry payment of an e-mandate

How to use the API
------------------

The users need to give inputs as per the input guidelines below.

## API Input Guidelines

* Pass a valid JSON body
* Pass a valid Authorization Key in headers

## Input parameters & Sample cURL request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name  | Description                                                                                                                    |          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------ | -------- |
| subReferenceId  | The unique ID of the eMandate                                                                                                  | Required |
| nextScheduledOn | <p>Applicable for periodic subscriptions only. The date when the charge for the next cycle should be scheduled.</p><p><br></p> |          |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl --location --request POST 'https://api.signzy.app/api/v3/eNach/eMandates/:subReferenceId/retry-charge' \
--header 'Authorization: ..authKey..'
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name   | Description                       |
| ---------------- | --------------------------------- |
| result.status    | eMandate response status          |
| result.subStatus | eMandate status                   |
| result.payment   | Object containing payment details |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
  "status": "OK",
  "subStatus": "ON_HOLD",
  "payment": {
    "paymentId": 3293789,
    "amount": 1,
    "status": "SUCCESS",
    "addedOn": "2021-12-17 08:41:30",
    "retryAttempts": 2
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



{% swagger baseUrl="https://api.signzy.app" path="/api/v3/eNach/eMandates/:subReferenceId/retry-charge" method="post" summary="Retry Payment eMandate" %}
{% swagger-description %}
This method retries an eMandate payment
{% endswagger-description %}

{% swagger-parameter in="path" name="subReferenceId" required="true" %}
Unique eMandate ID generated on creation of the eMandate
{% endswagger-parameter %}

{% swagger-parameter in="body" name="nextScheduledOn" %}
Applicable for periodic subscriptions only. The date when the charge for the next cycle should be scheduled.

\

{% endswagger-parameter %}

{% swagger-response status="200" description="Successful eMandate charge" %}
```
{
  "status": "OK",
  "subStatus": "ON_HOLD",
  "payment": {
    "paymentId": ..paymentId..,
    "amount": ..amount..,
    "status": "..status..",
    "addedOn": "2021-12-17 08:41:30",
    "retryAttempts": ..retryAttempts..
  }
}
```
{% endswagger-response %}
{% endswagger %}

\


[\
](https://docs.cashfree.com/edit/subscription-status)
