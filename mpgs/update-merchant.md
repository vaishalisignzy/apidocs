# Update Merchant

## Introduction

&#x20;A service for acquirers, enabling their merchant clients to accept electronic payments by a variety of payment methods. Gateway services that feature a platform that provides **financial institutions** and merchants with a single connection for all transaction switching. MPGS stands for Mastercard Payment Gateway Service. This is an external API that is used by Signzy for managing PG information.&#x20;

API Usecase


The MPGS Update Merchant API enables users to create or update a merchant account and set general information. The generic details include merchant details (for example, merchant id, merchant name, locale), contact details (for example, address, phone numbers), and the password for the merchant Administrator of the merchant account.&#x20;When a merchant account is created, the gateway automatically creates a merchant administrator user. This user has limited access privileges. In order to allow the merchant to conduct an in-depth configuration or use the Merchant Administration portal to perform transactions, the merchant administrator must create a new merchant operator with the requisite privileges.

How to use the API


You will need to log in before sending MPGS request. You are required to pass the access token received from the login call, as an authorization header in the request for Risk API along with other parameters.

Use the following exchange parameters for Update Merchant:



## Input Parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description |
| -------------- | ----------- |
|                |             |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
// Some code
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description |
| -------------- | ----------- |
|                |             |


{% endtab %}

{% tab title="Sample API response" %}
```
// Some code
```
{% endtab %}
{% endtabs %}

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../mpgs" method="post" summary="Update Merchant data" %}
{% swagger-description %}
This method is used for update merchant information.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - merchant Update
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.msoId" type="string" %}
Contains the MSO ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.address" type="string" %}
The address details of the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="address.street" type="string" %}
Street name 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="address.city" type="string" %}
City name
{% endswagger-parameter %}

{% swagger-parameter in="body" name="address.state" type="string" %}
State name
{% endswagger-parameter %}

{% swagger-parameter in="body" name="address.postcode" type="string" %}
Postal code of the address 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="address.countryCode" type="string" %}
Country code of the merchant address
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.categoryCode" type="string" %}
Category Code of the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.goodsDescription" type="string" %}
Goods Description of the merchant provider
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.locale" type="string" %}
Locale name of the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.name" type="string" %}
Merchant name
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.timeZone" type="string" %}
Time Zone followed by the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.phone" type="number" %}
phone number of the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.tradingName" type="string" %}
trading name of the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.webSite" type="object" %}
Merchant website URL
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.administrativePassword" type="string" %}
Password for the merchant portal
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "result": "SUCCESS",
    "merchantId":"...merchantId..."
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
    "task": "merchantupdate",
    "essentials": {
        "msoId": "...msoId...",
        "address": {
            "street": "...street...",
            "city": "...city...",
            "state": "...state...",
            "postcode": "...postcode...",
            "countryCode": "...countryCode..."
        },
        "categoryCode": "...categoryCode...",
        "goodsDescription": "...goodsDescription...",
        "locale": "...locale...",
        "name": "...name...",
        "timeZone": "...timeZone...",
        "phone": "...phone...",
        "tradingName": "...tradingName...",
        "webSite": "...webSite...",
        "administrativePassword": "...administrativePassword..."
    }
}
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME | DESCRIPTION                                          |
| -------------- | ---------------------------------------------------- |
| result         | The result is displayed in the form of success/fail. |
| merchantId     | The updated merchant ID is displayed.                |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/559d3acfaf45d6d5dca5)
