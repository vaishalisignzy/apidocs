---
description: >-
  Use this API to charge the ON_DEMAND eMandate. Not applicable for PERIODIC
  eMandate.
---

# Charge eMandate

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
| Parameter Name | Description                                                               |          |
| -------------- | ------------------------------------------------------------------------- | -------- |
| subReferenceId | The unique ID of the eMandate                                             | Required |
| amount         | Amount to be charged. Should be less than maxAmount set for the eMandate. | Required |
|                |                                                                           |          |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl --location -g --request POST 'https://api.signzy.app/api/v3/eNach/eMandates/:subReferenceId/charge' \
--header 'Authorization: ..authKey..' \
--header 'Content-Type: application/json' \
--data-raw '{
    "amount": 100
}'
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description              |
| -------------- | ------------------------ |
| result.status  | eMandate response status |
| result.message | eMandate charge message  |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "result": {
        "status": "OK",
        "message": "Subscription charge pending",
        "payment": {
            "paymentId": 00000,
            "cfOrderId": 2297619,
            "referenceId": 000000,
            "subReferenceId": 00000,
            "currency": "INR",
            "amount": 1,
            "cycle": 1,
            "status": "PENDING",
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



{% swagger baseUrl="https://api.signzy.app" path="/api/v3/eNach/eMandates/:subReferenceId/charge" method="post" summary="Charge eMandate" %}
{% swagger-description %}
This method charges an eMandate from subReferenceId given in path
{% endswagger-description %}

{% swagger-parameter in="path" name="subReferenceId" required="true" %}
Unique eMandate ID generated on creation of the eMandate
{% endswagger-parameter %}

{% swagger-parameter in="body" name="amount" required="true" type="Number" %}
Amount to be charged. Should be less than maxAmount set for the eMandate.
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
