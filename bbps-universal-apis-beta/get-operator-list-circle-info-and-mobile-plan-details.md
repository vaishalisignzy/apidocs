# Get Operator List, Circle Info and Mobile Plan Details

### Introduction

The Get Operator List, Circle Info and Mobile Plan Details API is called after the GetBillerList API and GetBillerDetails API are called in the given sequence. This API gives details about the Operator, Circle and Mobile Prepaid plan.

### Header

| Parameter     | Description      |
| ------------- | ---------------- |
| Content-Type  | application/json |
| Authorization | AuthKey          |

### Request

{% tabs %}
{% tab title="Parameters" %}
| Key          | Type   | Parameter Description |
| ------------ | ------ | --------------------- |
| mobileNumber | String | Pass your mobileNo.   |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://api-staging.signzy.app/api/v3/new/getOperatorList' \
--header 'Authorization: "...AuthKey...' \
--header 'Content-Type: application/json' \
--data-raw '{
    "mobileNumber":"...mobileNumber..." 
}'
```
{% endtab %}
{% endtabs %}

### Response

{% tabs %}
{% tab title="Parameters" %}
| Key                 | Parameter Description        |
| ------------------- | ---------------------------- |
| providerName        | String                       |
| providerId          | String                       |
| circleWisePlanLists | An Array of mobile plan list |
{% endtab %}
{% endtabs %}
