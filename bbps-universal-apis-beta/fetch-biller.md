# Fetch Biller

### Introduction

The Fetch Biller API fetches the biller Details after the Get Biller Details API is called.

### Header

The header remains the same for all API calls.

### Request

{% tabs %}
{% tab title="Parameters" %}
| Key               | Type   | Parameter Description                                                                |
| ----------------- | ------ | ------------------------------------------------------------------------------------ |
| billerId          | String | billerId is given by getBillerDetails Api.                                           |
| category          | String | Pass category                                                                        |
| merchantTrxnRefld | String | Reference ID to identify the transaction as unique transaction. Length should be 35. |
| mobileNo          | String | paramValue is customerMobile                                                         |
| paramName         | String | paramName is given by getBillerDetails Api                                           |
| paramValue        | String | paramValue is customerMobile for MOBILE POSTPAID category                            |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://api-staging.signzy.app/api/v3/new/fetchBill' \
--header 'Authorization: "...AuthKey..."' \
--header 'Content-Type: application/json' \
--data-raw '{
"billerId":"...billerId...",
"category":"...category...",
"merchantTrxnRefId":"...merchantTrxnRefId...",
"mobileNo":"...mobileNo...",
"paramName":"...paramName...",
"paramValue":"...paramValue..."
}'
```
{% endtab %}
{% endtabs %}

### Response

{% tabs %}
{% tab title="Parameters" %}
| Key              | Type   |
| ---------------- | ------ |
| reason           | String |
| additionalParams | String |
| type             | String |
| message          | String |
| refId            | String |
| status           | String |
| errorCode        | String |


{% endtab %}
{% endtabs %}
