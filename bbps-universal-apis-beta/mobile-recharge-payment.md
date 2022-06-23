# Mobile Recharge Payment

### Introduction

This API is called after the Validate Payment API. It completes the recharge process.

### Headers

The Headers remains the for all APIs.

### Request

{% tabs %}
{% tab title="Parameters" %}
| Key               | Type   | Parameter Description                                                |
| ----------------- | ------ | -------------------------------------------------------------------- |
| amount            | String | Pass the recharge amount                                             |
| billerId          | String | billerId is given by get biller detail api                           |
| billerName        | String | billerName is given by get biller detail api                         |
| category          | String | Category is given by get biller list api                             |
| circleRedID       | String | circleRefId is given By getOperatorAndCircleInfoAndMobilePlan Api    |
| customerEmailId   | String | Pass Customer Email Id                                               |
| customerMobileNo  | String | Pass Customer Mobile Number                                          |
| customerName      | String | Pass Customer Name                                                   |
| fetchRefId        | String | Pass RefId (Unique Value Given By Payment Validation API)            |
| merchantTrxnRefId | String | Unique Value                                                         |
| operatorCode      | String | operatorCode is given By getOperatorAndCircleInfoAndMobilePlan Api   |
| paymentInfo       | String | Pass VPA for UPI Pament Mode                                         |
| paymentMode       | String | Pass WALLET or UPI                                                   |
| planId            | String | Pass Plan Name is given By getOperatorAndCircleInfoAndMobilePlan Api |
| quickPay          | String | Pass true                                                            |
| rechargeType      | String | Pass Prepaid                                                         |
| remark            | String | Bill Payment                                                         |
| serviceName       | String | Pass category                                                        |
| paramName         | String | paramName is given by get biller detail api                          |
| paramValue        | String | Pass Customer Mobile Number                                          |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://api-staging.signzy.app/api/v3/new/mobilePaymentAPI' \
--header 'Authorization: "...AuthKey..."' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--data-raw '{ 
  "amount": "...amount...",
  "billerId": "...billerId...",
  "billerName": "...billerName...",
  "category": "...category...",
  "circleRefID": "...circleRefID...",
  "customerEmailId": "...customerEmailId...",
  "customerMobileNo": "...customerMobileNo...",
  "customerName": "...customerName...",
  "fetchRefId": "...fetchRefId...",
  "merchantTransactionReferenceId": "...merchantTransactionReferenceId...",
  "operatorCode": "...operatorCode...",
  "paymentInfo": "...paymentInfo...",
  "paymentMode": "...paymentMode...",
  "planId": "...planId...",
  "quickPay": "...quickPay...",
  "rechargeType": "...rechargeType...",
  "remark": "...remark...",
  "serviceName": "...serviceName...",
  "paramName": "...paramName...",
  "paramValue": "...paramValue..." 
}'
```
{% endtab %}
{% endtabs %}

### Response

{% tabs %}
{% tab title="Parameters" %}
| Key                   | Type   |
| --------------------- | ------ |
| billerId              | String |
| amount                | String |
| billerReferenceNumber | String |
| description           | String |
| billDate              | String |
| refId                 | String |
| paramName             | String |
| merchantTrxnRefId     | String |
| txnReferenceId        | String |
| paramValue            | String |
| trxn\_id              | String |
{% endtab %}
{% endtabs %}
