# Bill Payment

### Introduction

The Bill Payment API is called after fetchBiller API fetches the amount and payment mode selection by the user.

### Headers

The Headers remains the same for all the API calls.

### Request

{% tabs %}
{% tab title="Parameters" %}
| Key               | Type   | Parameter Description                                           |
| ----------------- | ------ | --------------------------------------------------------------- |
| amount            | String | amount is given by fetchBillerApi                               |
| billerId          | String | billerId is given by getBillerDetails Api.                      |
| billerName        | String | billerName is given by fetchBiller Api.                         |
| category          | String | category is given by getBillerList Api .                        |
| customerMobile    | String | Pass Customer Mobile Number                                     |
| customerName      | String | Pass Customer Name                                              |
| merchantTrxnRefId | String | fetchRefrenceId is given by fetchBiller Api with key name refId |
| paramName         | String | paramName is given by fetchBiller Api.                          |
| paramValue        | String | paramValue is customerMobile in Mobile Recharge Case.           |
| PaymentMode       | String | Pass WALLET or UPI                                              |
| optional          | String | String                                                          |
| quickPay          | String | Pass false or true                                              |
| remark            | String | Pass Payment Note                                               |
| serviceName       | String | Pass category                                                   |


{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://api-staging.signzy.app/api/v3/new/postpaidBillPay' \
--header 'Authorization: "...AuthKey..."' \
--header 'Content-Type: application/json' \
--data-raw '{
  "amount": "...amount...",
  "billerId": "...billerId...",
  "billerName": "...billerName...",
  "category": "...category...",
  "customerMobile": "...customerMobile...",
  "customerName": "...customerName...",
  "merchantTrxnRefId": "...merchantTrxnRefId...",
  "paramName": "...paramName...",
  "paramValue: "...paramValue...",
  "paymentMode": "...paymentMode...",
  "optional": "...optional...",
  "quickPay": "...quickPay...",
  "remark": "...remark...",
  "serviceName": "...serviceName..." 
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
| code                  | String |
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
