# Validate Payment

### Introduction

The Validate Payment API is called after the Get Operator List, Circle Info, Mobile Plan Details API. This API validates the Payment details associated with the Prepaid Account.

### Headers

The headers remains the same for all API calls.

### Request

{% tabs %}
{% tab title="Parameters" %}
| Key              | Type   | Parameter Description                                           |
| ---------------- | ------ | --------------------------------------------------------------- |
| amount           | String | Pass payment Amount                                             |
| billerId         | String | billerId is given by getBillreDetials Api                       |
| circleRefID      | String | circler refId is given by getOperatorAndCircleInfoAndMobilePlan |
| customerMobileNo | String | Pass customer Mobile number                                     |
| customerName     | String | Pass customer name                                              |
| operatorCode     | String | operatorCode is given by getOperatorAndCircleInfoAndMobilePlan  |
| paramName        | String | paramName is given by GetBillerDetail Api                       |
| paramValue       | String | paramValue is given by getBillerDetial Api                      |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://api-staging.signzy.app/api/v3/new/validatePayment' \
--header 'Authorization: "...AuthKey..."' \
--header 'Content-Type: application/json' \
--data-raw '{ 
  "amount": "...amount...",
  "billerId": "...billerId...",
  "circleRefID": "...circleRefID...",
  "customerMobileNo": "...customerMobileNo...",
  "customerName": "...customerName...",
  "operatorCode": "...operatorCode...",
  "paramName": "...paramName...",
  "paramValue": "...paramValue..." 
}'
```
{% endtab %}
{% endtabs %}

### Response

{% tabs %}
{% tab title="Parameters" %}
|                  |        |
| ---------------- | ------ |
| referenceId      | String |
| requestTimeStamp | String |
| amount           | String |
| billerId         | String |
| additionalParams | String |
{% endtab %}
{% endtabs %}
