# Update Payment

## Introduction

This API enables you to add or update payment configuration details for an existing merchant. The payment details include details about how a merchant will transact (for example, Authorization then Capture mode or Purchase mode), the type of transactions (for example, Verification Only, Standalone Capture transactions), and the associated privileges.&#x20;

API Usecase


The service also assists you to enable/disable and configure services offered by the MasterCard Payment Gateway such as API, Reporting, Hosted Payment Session, Batch, Tokenization, Transaction Filtering and Risk Management.

How to use the API


You will need to log in before sending MPGS request. You are required to pass the access token received from the login call, as an authorization header in the request for Risk API along with other parameters.

Use the following exchange parameters for Update Payment:



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





{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../mpgs" method="post" summary="Update Payment data" %}
{% swagger-description %}
This method is used for update merchant payment information.
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

{% swagger-parameter in="body" name="essentials.merchantId" type="string" %}
The ID of the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.cardMaskingFormat" type="string" %}
The card Masking Format used by the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.systemCapturedCardMaskingFormat" type="string" %}
The card masking Format that is captured by the system for the respective merchant.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.transactionMode" type="string" %}
Specifies the mode of transaction used by the merchant.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.privilege" type="array" %}
List of priviledges provided to the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.service" type="array" %}
List of services provided by the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.Tokenization" type="string" %}
Tokenization details of the merchant
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Tokenization.verificationStrategy" type="string" %}
Verification strategy followed for Tokenization
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Tokenization.tokenRepository" type="string" %}
Details about the Token Repository
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Tokenrepository.tokenGeneration" type="string" %}
USed to generate a token into the Token Repository
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Tokenrepository.tokenManagementStrategy" type="string" %}
Token management strategy followed by the token repository
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
      "task": "paymentupdate",
      "essentials": {
        "msoId": "...msoId...",
        "merchantId": "...merchantId...",
        "cardMaskingFormat": "...cardMaskingFormat...",
        "systemCapturedCardMaskingFormat": "...systemCapturedCardMaskingFormat...",
        "transactionMode": "...transactionMode...",
        "privilege": ["...list of privileges..."],
        "service": ["... list of services..."],
        "tokenization": {
            "verificationStrategy": "...verificationStrategy...",
            "tokenRepository": {
                "tokenGeneration": "...tokenGeneration...",
                "tokenManagementStrategy": "...tokenManagementStrategy..."
            }
        }
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME | DESCRIPTION                                          |
| -------------- | ---------------------------------------------------- |
| result         | The result is displayed in the form of Success/Fail. |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/9f1db743b4a316d6d7cc)

