# Bank Account Verification - Verify Transfer

## Bank Account Verification <a href="#right-to-left-support" id="right-to-left-support"></a>

Signzy has provided users with this API so that any amount that has been previously transferred can be verified here. The user needs to provide a unique SIgnzy Id and Amount as input and the system will verify the MMID, Owner name and other details of the transfer.

You will need to login before sending search request. You are required to pass the access token received from the login call, as authorization header in the IMPS transfer request.

Use the following exchange parameters for bank account Verify.\


{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../bankaccountverifications" method="post" summary="Bank Account Verify Transfer" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../bankaccountverifications`

\




\


This method is used to verify the Bank Account transfer
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task to be performed - verifyAmount
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.amount" type="string" %}
Amount which is transferred
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.signzyId" type="string" %}
Assigned unique Signzy ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
    "task": "verifyAmount",
    "essentials": {
       "amount": ".....amount.....",
       "signzyId":  "...signzyID....."
     },
    "id": ".....id.....",
    "patronId": "...patronID....",
    "result": {
       "amountMatch": "true/false",
       "owerName": "......ownername.....",
       "mobile": "...mobile....",
        "mmid": "...mmid..."
      }
    }
```


{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME     | DESCRIPTION                                                                                                                                           |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                 | Contains the unique Id of the snoop request&#xD;                                                                                                      |
| patronId           | The patron Id that was received during identity request.                                                                                              |
| result             | This contains the final response parameters.                                                                                                          |
| result.amountMatch | This parameter verifies whether the amount entered by the user is the same as the amount received on the registered mobile number of the beneficiary. |
| result.ownerName   | The owner name of the bank transaction is displayed here.                                                                                             |
| result.mobile      | The mobile number of the owner is shown here.                                                                                                         |
| result.mmid        | The MMID number of the transaction owner is displayed here.                                                                                           |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/81667d2324bf8d9d2287)
