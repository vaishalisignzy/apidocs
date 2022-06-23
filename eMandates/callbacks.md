---
description: Functionality to send server callbacks to your server from Signzy.
---

# Callbacks

## Overview

Callbacks are event-based and are sent when specific events related to the transaction happen. Signzy e-mandates enable you to input a callback webhook URL where we will post data related to eMandate status change, eMandate authorization status change, new payment in eMandates.&#x20;

## Configure Callback

You can choose any valid URL to be a callback URL to give in the input while eMandate creation. Event-based data will be posted on the same.\
\


## How to Use Callbacks

Callback will be sent to your configured endpoint as a POST request with the body containing the various parameters specifying the details of each event. Each request contains an event parameter that identifies its type.

Below are the various events that can be sent to your webhook endpoint.

* SUBSCRIPTION\_STATUS\_CHANGE
* SUBSCRIPTION\_NEW\_PAYMENT
* SUBSCRIPTION\_AUTH\_STATUS

## SUBSCRIPTION\_STATUS\_CHANGE

| Parameter      | Type                                   | Description                                                                                                             |
| -------------- | -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| event          | String                                 | This event is triggered whenever the eMandate status changes. The value for this event is SUBSCRIPTION\_STATUS\_CHANGE. |
| subReferenceId | String                                 | A unique Id which was generated when the eMandate was created.                                                          |
| status         | String                                 | The new status of the eMandate. Click [here ](get-emandate-details.md)for information on eMandate statuses.             |
| lastStatus     | String                                 | The old status of the eMandate. Click [here](get-emandate-details.md) for information on eMandate statuses.             |
| eventTime      | String \[format - yyyy-MM-dd HH:mm:ss] | The time when the event was dispatched.                                                                                 |

***

## SUBSCRIPTION\_NEW\_PAYMENT

| Parameter      | Type                                   | Description                                                                                                                                            |
| -------------- | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| event          | String                                 | This event is triggered whenever there is a successful new payment for an authorized eMandate. The value for this event is SUBSCRIPTION\_NEW\_PAYMENT. |
| subReferenceId | String                                 | A unique Id which was generated when the eMandate was created.                                                                                         |
| eventTime      | String \[format - yyyy-MM-dd HH:mm:ss] | The time when the event was dispatched.                                                                                                                |
| paymentId      | Integer                                | The unique paymentId for the payment                                                                                                                   |
| amount         | Float                                  | The amount charged for payment.                                                                                                                        |
| referenceId    | Integer                                | The unique txnId for the payment.                                                                                                                      |
| retryAttempts  | Integer                                | The number of payment retries. This is applicable for failed payments.                                                                                 |

## SUBSCRIPTION\_AUTH\_STATUS

This event is triggered when the checkout fails. The customer can do multiple checkouts through the same eMandate, and you will be notified of every checkout failure.

This event will not be triggered for an active, or bank approval pending eMandate.

| Parameter          | Type                                   | Description                                                                                                                                                                                                   |
| ------------------ | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| event              | String                                 | The event is triggered when the checkout fails The value for this event is SUBSCRIPTION\_AUTH\_STATUS.                                                                                                        |
| subReferenceId     | Integer                                | A unique Id which was generated when the eMandate was created.                                                                                                                                                |
| eventTime          | String \[format - yyyy-MM-dd HH:mm:ss] | The time when the event was dispatched.                                                                                                                                                                       |
| subscriptionStatus | String                                 | The status of the eMandate. Click [here](get-emandate-details.md) for information on eMandate statuses.                                                                                                       |
| authStatus         | String                                 | Checkout status. Allowed value: FAILED                                                                                                                                                                        |
| authTimestamp      | String \[format - yyyy-MM-dd HH:mm:ss] | Checkout initiated timestamp.                                                                                                                                                                                 |
| authFailureReason  | String                                 | Possible checkout failure. It will be empty for successFul authStatus change.                                                                                                                                 |
| signature          | String                                 | A unique string which helps distinguish that the request is genuine and initiated by Cashfree. Click [here](https://docs.cashfree.com/reference/subscription-webhooks#verify-signature) for more information. |
