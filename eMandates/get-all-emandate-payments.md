---
description: >-
  Use this API to get all the payments of an eMandate when required with just
  one request.
---

# Get All eMandate Payments

## Introduction

It takes 1 to 2 working days for the transactions to be complete through eMandates. A description of all the possible statuses for a subscription payment is available in the table below.

## API Use-case

The purpose is to get all e-mandate payments

How to use the API
------------------

The users need to give inputs as per the input guidelines below.

## API Input Guidelines

* Pass a valid JSON body
* Pass a valid Authorization Key in headers

## Input parameters & Sample cURL request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description                                                    |          |
| -------------- | -------------------------------------------------------------- | -------- |
| subReferenceId | A unique ID of the eMandate                                    | Required |
| lastId         | The pagination counter to return results from.                 |          |
| count          | The total number of payments to be shown in a paginated query. |          |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl --location --request GET 'https://api.signzy.app/api/v3/eNach/eMandates/65668/payments?lastId=:id&count=:count' \
--header 'Authorization: ..authKey..'
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name  | Description                                 |
| --------------- | ------------------------------------------- |
| result.status   | eMandate response status                    |
| result.message  | eMandate payments message                   |
| result.payments | Object containing eMandate payments details |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "result": {
        "status": "OK",
        "message": "Subscription Payments",
        "payments": [
            {
                "paymentId": 12345,
                "cfOrderId": 123,
                "referenceId": 123456,
                "subReferenceId": 00000,
                "currency": "INR",
                "amount": 5,
                "cycle": 1,
                "status": "PENDING",
                "remarks": "",
                "addedOn": "2022-03-29 18:49:20",
                "scheduledOn": null,
                "retryAttempts": 0,
                "failureReason": null
            }
        ],
        "lastId": 12345
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



{% swagger baseUrl="https://api.signzy.app" path="/api/v3/eNach/eMandates/:subReferenceId/payments?lastId=:id&count=:count" method="get" summary="Get eMandate All Payments Details" %}
{% swagger-description %}
This method gets eMandate payment details from subReferenceId, lastId, count
{% endswagger-description %}

{% swagger-parameter in="path" name="subReferenceId" required="true" %}
Unique eMandate ID generated on creation of the eMandate
{% endswagger-parameter %}

{% swagger-parameter in="path" name="lastId" %}
The pagination counter to return results from.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="count" %}
The total number of payments to be shown in a paginated query.

\

{% endswagger-parameter %}

{% swagger-response status="200" description="Successful eMandate creation" %}
```
{
    "result": {
        "status": "OK",
        "message": "Subscription Details",
        "subscription": {
            "subReferenceId": ..subReferenceId..,
            "customerName": "..customerName..",
            "customerEmail": "..customerEmail..",
            "customerPhone": "..customerPhone..",
            "mode": "..mode..",
            "cardNumber": null,
            "status": "..status..",
            "firstChargeDate": null,
            "addedOn": "2022-03-22 11:57:41",
            "scheduledOn": "2022-04-23 07:00:00",
            "currentCycle": 0,
            "authLink": "..authLink..",
            "bankAccountNumber": "..bankAccountNumber..",
            "bankAccountHolder": "..bankAccountHolder..",
            "umrn": "..umrn.."
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

## Notes

* lastId and count help in paginating queries for ease of use. Every query returns "count" number of payments. To fetch next page set lastId of the previous page. To get first page do not include lastId in the request.
* Cycle indicates after how many intervals was this payment processed.
* Payment status field values are described in Payment Status Table.

## Payment Status

| Status  | Description                                                                                                   |
| ------- | ------------------------------------------------------------------------------------------------------------- |
| SUCCESS | Payment for the eMandate was processed successfully.                                                          |
| PENDING | Payment for the eMandate was attempted but not yet marked successful. This status is specific for e-mandates. |
| FAILED  | The payment failed for the eMandate.                                                                          |

\


[\
](https://docs.cashfree.com/edit/subscription-status)
