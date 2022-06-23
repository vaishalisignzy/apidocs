---
description: >-
  Use this API to activate a subscription that is in ONHOLD state. For periodic
  subscriptions, the next charge date is calculated for the next cycle.
---

# Activate eMandate

## Introduction

Use this API to explicitly debit the customer account for an ON-DEMAND eMandate. The customer will receive a notification from their respective bank regarding the payment.

## API Use-case

The purpose of this API is to charge an ON\_DEMAND e-mandate

How to use the API
------------------

The users need to give inputs as per the input guidelines below.

## API Input Guidelines

* Pass a valid JSON body
* Pass a valid Authorization Key in headers

## Input parameters & Sample cURL request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name  | Description                                                                                                               |          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------- | -------- |
| subReferenceId  | The unique ID of the eMandate                                                                                             | Required |
| nextScheduledOn | <p>Applicable for periodic subscriptions. The date when the charge for the next cycle should be scheduled.</p><p><br></p> |          |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl --location --request POST 'https://api.signzy.app/api/v3/eNach/eMandates/:subReferenceId/activate' \
--header 'Authorization: ..authKey..'
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name              | Description                        |
| --------------------------- | ---------------------------------- |
| result.status               | eMandate response status           |
| result.subStatus            | eMandate status                    |
| result.subscriptionResponse | Object containing eMandate Details |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
  "status": "OK",
  "subStatus": "ACTIVE",
  "subscriptionResponse": {
    "subReferenceId": 123456,
    "subscriptionId": "testabcd",
    "planId": "test_demo",
    "customerPhone": "9876543210",
    "customerName": "John Doe",
    "customerEmail": "abc@gmail.com",
    "addedOn": "2021-02-24 11:15:10"
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



{% swagger baseUrl="https://api.signzy.app" path="/api/v3/eNach/eMandates/:subReferenceId/activate" method="post" summary="Activate eMandate" %}
{% swagger-description %}
This method activate an ONHOLD state eMandate from subReferenceId given in path
{% endswagger-description %}

{% swagger-parameter in="path" name="subReferenceId" required="true" %}
Unique eMandate ID generated on creation of the eMandate
{% endswagger-parameter %}

{% swagger-parameter in="body" name="nextScheduledOn" %}
Applicable for periodic subscriptions. The date when the charge for the next cycle should be scheduled.

\

{% endswagger-parameter %}

{% swagger-response status="200" description="Successful eMandate charge" %}
```
{
    "result": {
        "status": "OK",
        "message": "..message..",
        "payment": {
            "paymentId": ..paymentId..,
            "cfOrderId": ..cfOrderId..,
            "referenceId": ..referenceId..,
            "subReferenceId": ..subReferenceId..,
            "currency": "INR",
            "amount": 1,
            "cycle": 1,
            "status": "..status..",
            "addedOn": "2022-03-30 17:13:38",
            "retryAttempts": 0,
            "remarks": "",
            "failureReason": null,
            "scheduledOn": null,
            "initiatedOn": null
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

\


[\
](https://docs.cashfree.com/edit/subscription-status)
