# Get Biller List

### Introduction

The get Biller List API gets the biller list based on the headers passed. This is the first API that has to be called in sequence.

### Header

| Parameters    | Description        |
| ------------- | ------------------ |
| Content Type  | Application / JSON |
| Authorization | AuthKey            |

### Request

For the Request only pass the Headers.

{% tabs %}
{% tab title="CURL Request" %}
```
curl --location --request POST 'https://api-staging.signzy.app/api/v3/new/getBillerList' \
--header 'Authorization: "...AuthKey..."' \
--header 'Content-Type: application/json' \
--data-raw '{}'
```
{% endtab %}
{% endtabs %}

### Response

{% tabs %}
{% tab title="Parameters" %}
| Key              | Type  |
| ---------------- | ----- |
| billerCategories | Array |
|                  |       |
{% endtab %}
{% endtabs %}
