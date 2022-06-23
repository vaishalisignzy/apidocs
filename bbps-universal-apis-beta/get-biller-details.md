# Get Biller Details

### Introduction

The Get Biller Details API gets the biller Details based on the headers passed. This API is subsequently called after Get Biller List.

### Headers

| Parameters    | Description        |
| ------------- | ------------------ |
| Content Type  | Application / JSON |
| Authorization | Basic Auth         |

### Request

{% tabs %}
{% tab title="Input Parameter" %}
| Key      | Type   | Parameter Description                    |
| -------- | ------ | ---------------------------------------- |
| category | String | Category is given by Get Biller List API |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://api-staging.signzy.app/api/v3/new/getBillerdetails' \
--header 'Authorization: "...AuthKey..."' \
--header 'Content-Type: application/json' \
--data-raw '{
    "category":"...category..."
}'
```
{% endtab %}
{% endtabs %}

### Response

{% tabs %}
{% tab title="Parameters" %}
| Key         | Type   | Parameter Description       |
| ----------- | ------ | --------------------------- |
| billersId   | String | ID                          |
| fetchOption | String | MANDATORY/ NOT\_SUPPORTED   |
| billersName | String | Name of the biller/provider |
| paramName   | String | Name of the parameter       |
| category    | String | Bill type                   |
{% endtab %}
{% endtabs %}

