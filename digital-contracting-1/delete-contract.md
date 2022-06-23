# Delete Contract

The Delete Contract API is used to delete a contract in case it is no longer valid or there is some discrepancy in the existing contract, for which a new one has to be drafted. This can only be done with the authorisation of all parties concerned.

Client can choose to delete the contract from Signzy system once the contract is executed and need not be available in Signzy system. Parameters contactId and customerId are used to identify the contract to be deleted.

{% swagger baseUrl="https://contracting.signzy.tech" path="/api/contractdetails/deleteContract" method="post" summary="Delete Contract" %}
{% swagger-description %}
This method is used to delete an existing contract.
{% endswagger-description %}

{% swagger-parameter in="body" name="contractId" type="string" %}
The unique ID of the contract to be pulled
{% endswagger-parameter %}

{% swagger-parameter in="body" name="customerId" type="string" %}
The unique customer ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "deleteResponse": "SUCCESS"
    }

```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
        "contractId": "..contractId..",
        "customerId": "..customerId.."
    }
```
{% endtab %}

{% tab title="Response Parameters" %}


| PARAMETERS     | DESCRIPTION                             |
| -------------- | --------------------------------------- |
| deleteResponse | delete response status for the contract |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/10bcfab6a7a9c7074402)
