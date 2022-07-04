---
description: Individual PAN 206 Compliance API
---

# Individual Search - 206 Compliance API

## Overview

Sections 206AB and 206CCA of Income Tax Act 1961 are introduced in Finance Bill, 2021 to ensure compliance with ITR filing. Sections 206AB and 206CCA mandate tax deduction or collection at a higher rate if a ‘specified person’ has failed to file income tax returns for the previous two financial years. While Section 206AB deals with TDS (tax deducted at source), 206CCA is applicable for TCS (tax collected at source) at a higher rate.

In both the sections, if a person satisfies the following two conditions, then he/ she is regarded as a ‘specified person’- He/She has not filed the income tax returns for the previous two financial years preceding the year in which TDS or TCS is required to be deducted or collected. For example, previous years for the financial year 2021-22 would be 2018-19 and 2019-20. The total TDS or TCS is more than Rs. 50,000 in each of the previous two financial years. When does this come into effect? Section 206AB and Section 206CCA come into effect from 1st July 2021.

## API Use-case

The purpose is to query pan numbers for 206 compliance check

## How to use the API

The users need to give inputs as per the input guidelines below.

## API Input Guidelines

* Pass a valid JSON body
* Pass a valid Authorization Key in headers

## Input parameters & Sample cURL request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description       |          |
| -------------- | ----------------- | -------- |
| panNumber      | Valid PAN Number  | Required |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl --location --request POST 'https://api.signzy.app/api/v3/pan/compliance-206-individual-search' \
--header 'Authorization: ..authKey..' \
--header 'Content-Type: application/json' \
--data-raw '{
    "panNumber":"..panNumber.."
}'
```
{% endtab %}
{% endtabs %}

## Output Parameters and Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description              |
| -------------- | ------------------------ |
| result.status  | eMandate response status |
| result.message | eMandate cancel message  |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "result": {
        "number": "ABCDE00000",
        "compliant": "true",
        "isSpecified": "false",
        "entityName": "ZXXXXZ ZXXZ",
        "panAllotmentDate": "23-04-2017",
        "currentFY": "2022-23",
        "panAadhaarLinkStatus": "Linked"
    }
}
```
{% endtab %}
{% endtabs %}

## HTTP Response codes

| Status code | Description                    |
| ----------- | ------------------------------ |
| **200**     | All response details are valid |
| **404**     | Not found                      |
| **400**     | Bad Request                    |
| **401**     | Unauthorized                   |
| **403**     | Forbidden                      |
| **422**     | Unprocessable entity           |

{% swagger baseUrl="" path="" method="post" summary="Individual Search" %}
{% swagger-description %}
This method takes in pan number of an entity/individual to check for 206 compliance
{% endswagger-description %}

{% swagger-parameter in="path" name="panNumber" required="true" %}
Pan Number of individual/entity
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful compliance run" %}
```
{
    "result": {
            {
            "number": "...number...",
            "compliant": "...compliant...",
            "isSpecified": "...isSpecified...",
            "entityName": "...entityName...",
            "panAllotmentDate": "...panAllotmentDate...",
            "currentFY": "...currentFY...",
            "panAadhaarLinkStatus": "...panAadhaarLinkStatus..."
        }
}
```
{% endswagger-response %}
{% endswagger %}



[\
](https://docs.cashfree.com/edit/subscription-status)
