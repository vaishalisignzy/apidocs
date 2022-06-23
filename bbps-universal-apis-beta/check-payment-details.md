# Check Payment Details

### Introduction

This API is called for checking payment detials after the bill is paid with Bill Payment API.

### Headers

The Headers remains the same for all the API calls.

### Request

{% tabs %}
{% tab title="Parameter" %}
| Key       | Type   | Parameter Description                         |
| --------- | ------ | --------------------------------------------- |
| trxn\_id  | String | Pass the merchantTrxnRefIdgiven by billPayAPI |
| urlAppend | String | Pass the trxn\_id by billPayAPI               |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://api-staging.signzy.app/api/v3/new/checkPaymentDetails' \
--header 'Authorization: "...AuthKey..."' \
--header 'Content-Type: application/json' \
--data-raw '{
    "trxnId":"...trxnId..."
    "urlAppend":"...urlAppend..." //this will be the merchantTrxnId we get from Bill Payment API
}'
```
{% endtab %}
{% endtabs %}

### Response

{% tabs %}
{% tab title="Parameters" %}
| Key       | Type   |
| --------- | ------ |
| trxnRefId | String |
| refId     | String |
{% endtab %}
{% endtabs %}
