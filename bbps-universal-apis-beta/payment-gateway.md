# Payment Gateway

### Headers

The Headers are same for all APIs.

### Request

{% tabs %}
{% tab title="Parameters" %}
| Key             | Type   |
| --------------- | ------ |
| amount          | String |
| merchantId      | String |
| mobileNumber    | String |
| redirectUrl     | String |
| transactionNote | String |
| vpa             | String |
| webhookUrl      | String |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --request POST \
  --url https://api-staging.signzy.app/api/v3/new/paymentApi \
  --header 'Authorization: "...AuthKey..."' \
  --header 'Content-Type: application/json' \
  --data '{
  "amount":"...amount...",
  "merchantId":"...merchantId...",
  "mobileNumber":"...mobileNumber...",
  "redirectUrl":"...redirectUrl...",
  "transactionNote":"...transactionNote...",
  "vpa":"...vpa...",
  "webhookUrl":"...webhookUrl..."
}'
```
{% endtab %}
{% endtabs %}

### Response

{% tabs %}
{% tab title="Parameters" %}
| Key         | Parameter Description |
| ----------- | --------------------- |
| timeStamp   | Current Date/Time     |
| paymentLink | URL for Payment       |
{% endtab %}
{% endtabs %}
