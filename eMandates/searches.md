---
description: Use this API to get the details of all the eMandates created.
---

# Search eMandates

## Introduction

Use this API to get the details of all the eMandates created. It allows for filtering of data which enables the user to view more streamlined results.

## API Use-case

The purpose of this API is to an query among e-mandates and view streamlined results.

How to use the API
------------------

The users need to give inputs as per the input guidelines below.

## API Input Guidelines

* Pass a valid JSON body
* Pass a valid Authorization Key in headers

## Input parameters & Sample cURL request

{% tabs %}
{% tab title="Input Parameters" %}


| Parameter Name         | Description                                                                |          |
| ---------------------- | -------------------------------------------------------------------------- | -------- |
| filters.date.startDate | To query eMandates created on or after the given date (YYYY-MM-DD Format)  | Optional |
| filters.date.endDate   | To query eMandates created on or before the given date (YYYY-MM-DD Format) | Optional |
| filters.mandateType    | PERIODIC/ON\_DEMAND                                                        | Optional |
|                        |                                                                            |          |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl --location --request POST 'https://api.signzy.app/api/v3/eNach/eMandates/searches' \
--header 'Authorization: ..authKey..' \
--header 'Content-Type: application/json' \
--data-raw '{
    "filters": {
        "date": {
            "startDate": "2022-04-08",
            "endDate": "2022-04-30"
        },
        "mandateType": "ON_DEMAND"
    }   
}'
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name              | Description                                                               |
| --------------------------- | ------------------------------------------------------------------------- |
| result.subReferenceId       | eMandate unique ID                                                        |
| result.requestData          | Object containing eMandate details given at the time of eMandate creation |
| result.subscriptionResponse | Object containing eMandate updates and details                            |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "result": [
        {
            "subReferenceId": 0000,
            "requestData": {
                "customerName": "...customerName...",
                "customerEmail": "...customerEmail...",
                "customerPhone": "...customerPhone...",
                "mandateName": "...mandateName...",
                "mandateType": "...mandateType...",
                "mandateFlow": "...mandateFlow...",
                "maxCycles": ...maxCycles...,
                "description": "...description...",
                "returnUrl": "...returnUrl...",
                "expiresOn": "...expiresOn...",
                "firstChargeDate": "...firstChargeDate...",
                "intervalType": "...intervalType...",
                "amount": ...amount...,
                "intervals": "...intervals...",
                "emandateAccountHolder": "...emandateAccountHolder...",
                "emandateAccountNumber": "...emandateAccountNumber...",
                "emandateBankId": "...emandateBankId...",
                "emandateAuthMode": "...emandateAuthMode...",
                "paymentOption": "...paymentOption..."
            },
            "subscriptionResponse": [
                {
                    "status": "OK",
                    "message": "Subscription created successfully",
                    "subReferenceId": ..subReferenceId..,
                    "authLink": "..authLink..",
                    "subStatus": "..subStatus.."
                }
            ]
        }
    ]
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



{% swagger baseUrl="https://api.signzy.app" path="/api/v3/eNach/eMandates/searches" method="post" summary="Search eMandates" %}
{% swagger-description %}
This method searches the eMandates
{% endswagger-description %}

{% swagger-parameter in="body" name="filters" type="Objct" %}
Contains mandateType and/or date
{% endswagger-parameter %}

{% swagger-parameter in="body" name="filters.mandateType" type="" %}
PERIODIC/ON_DEMAND
{% endswagger-parameter %}

{% swagger-parameter in="body" name="filters.date" type="Object" %}
Contains startDate and endDate (both in YYYY-MM-DD Format) 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="filters.startDate" %}
YYYY-MM-DD Format
{% endswagger-parameter %}

{% swagger-parameter in="body" name="filters.endDate" %}
YYYY-MM-DD Format
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful eMandate creation" %}
```
{
    "result": [
        {
            "subReferenceId": 0000,
            "requestData": {
                "customerName": "...customerName...",
                "customerEmail": "...customerEmail...",
                "customerPhone": "...customerPhone...",
                "mandateName": "...mandateName...",
                "mandateType": "...mandateType...",
                "mandateFlow": "...mandateFlow...",
                "maxCycles": ...maxCycles...,
                "description": "...description...",
                "returnUrl": "...returnUrl...",
                "expiresOn": "...expiresOn...",
                "firstChargeDate": "...firstChargeDate...",
                "intervalType": "...intervalType...",
                "amount": ...amount...,
                "intervals": "...intervals...",
                "emandateAccountHolder": "...emandateAccountHolder...",
                "emandateAccountNumber": "...emandateAccountNumber...",
                "emandateBankId": "...emandateBankId...",
                "emandateAuthMode": "...emandateAuthMode...",
                "paymentOption": "...paymentOption..."
            },
            "subscriptionResponse": [
                {
                    "status": "OK",
                    "message": "Subscription created successfully",
                    "subReferenceId": ..subReferenceId..,
                    "authLink": "..authLink..",
                    "subStatus": "..subStatus.."
                }
            ]
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

## Notes

* Current cycle shows how many payments have been initiated for the eMandate.
* scheduledOn and firstChargeDate will be null for ON\_DEMAND type eMandates.

## eMandate Status



| Status                  | Description                                                                                                    |
| ----------------------- | -------------------------------------------------------------------------------------------------------------- |
| INITIALIZED             | The eMandate has just been created and is ready to be authorized by the customer.                              |
| BANK\_APPROVAL\_PENDING | E-Mandate has been authorised and registration is pending at the Bank. This status is specific for e-mandates. |
| ACTIVE                  | The customer has authorized the eMandate and will be debited accordingly.                                      |
| ON\_HOLD                | The eMandate failed due to insufficient funds, expiration of payment method, and so on.                        |
| CANCELLED               | The eMandate was cancelled by the merchant and can no longer be activated.                                     |
| COMPLETED               | The eMandate has completed its total active period.                                                            |

\


[\
](https://docs.cashfree.com/edit/subscription-status)
