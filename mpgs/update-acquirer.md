# Update Acquirer

## Introduction

The MPGS Update Acquirer API enables you to add or update configuration for an acquirer link used by the merchant for payment processing. A merchant can be configured for one or more acquirer links where each acquirer link must have a unique identifier provided in the merchant.acquirerlLink.id field. You must use separate API calls to create or update each link.

How to use the API


You will need to log in before sending MPGS request. You are required to pass the access token received from the login call, as an authorization header in the request for Risk API along with other parameters.



Use the following exchange parameters for Update Acquirer:



### Input parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

### Output Parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

## Sample cURL Response

```
//yet to extract
```

## Sample API response

```
//yet to extract
```







{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../mpgs" method="post" summary="Update Acquirer data" %}
{% swagger-description %}
This method is used for update acquirer information.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - acquirer Update
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.msoId" type="string" %}
Contains the MSO ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.acquirerLink" type="string" %}
The acquirer details are contained here.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.currency" type="array" %}
List of currency accepted by the Acquirer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.defaultTransactionFrequency" type="string" %}
The default transaction frequency of the Ac
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.defaultTransactionSource" type="string" %}
The default transaction frequency of the Ac
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.paymentType" type="string" %}
Payment type used by the Acquirer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.status" type="string" %}
Status of the Acquirer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.acquirerId" type="string" %}
The unique ID of the Acquirer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.allowableTransactionFrequency" type="array" %}
The list of allowable Transaction Frequency for the Acquirer 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.allowableTransactionSource" type="array" %}
The list of allowable Transaction sources for the Acquirer 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.bankMerchantId" type="string" %}
Bank Merchant ID used by the Acquirer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.cardType" type="array" %}
List of card types accepted by the Acquirer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.terminalId" type="array" %}
List of terminal Ids accepted by the Acquirer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="acquirerLink.id" type="string" %}
Transaction ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "result": "SUCCESS"
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
  {
    "task": "acquirerupdate",
    "essentials": {
    	"msoId": "...msoId...",
        "merchantId": "...merchantId...",
        "acquirerLink": {
            "currency": ["...list of currency..."],
            "defaultTransactionFrequency": "...defaultTransactionFrequency...",
            "defaultTransactionSource": "...defaultTransactionSource...",
            "paymentType": "...paymentType...",
            "status": "...status...",
            "acquirerId": "...acquirerId...",
            "allowableTransactionFrequency": ["...list of allowableTransactionFrequency..."],
            "allowableTransactionSource": ["...list of allowableTransactionSource..."],
            "bankMerchantId": "...bankMerchantId...",
            "cardType": ["...list of cardType..."],
            "terminalId": ["...list of terminalId..."],
            "id": "...id..."
        }
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME  | DESCRIPTION                                          |
| --------------- | ---------------------------------------------------- |
| result          | The result is displayed in the form of Success/Fail. |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/a54830dc51afb58ed7d1)



