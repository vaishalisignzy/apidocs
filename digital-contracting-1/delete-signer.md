# Delete Signer

This API is used to delete a particular signer at the request of the client.

Client can choose to delete a particular signer from a particular contract created earlier in the Signzy system. Parameters like contractId ,customerId and signerEmail are used to identify the particular signer of the contract to be deleted.

{% swagger baseUrl="https://contracting.signzy.tech" path="/api/contractdetails/deleteSigner" method="post" summary="Delete Signer" %}
{% swagger-description %}
This method is used to delete the signer of an existing contract.
{% endswagger-description %}

{% swagger-parameter in="body" name="contractId" type="string" %}
The unique ID of the contract to be pulled
{% endswagger-parameter %}

{% swagger-parameter in="body" name="customerId" type="string" %}
The unique customer ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="signerId" type="string" %}
Unique ID created per signer per contract	
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "deleteSignerResponse": "SUCCESS"
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
        "contractId": "..contractId..",
        "customerId": "..customerId..",
        "signerId" : "..signerId.."
    }
```
{% endtab %}

{% tab title="Response Parameters" %}


| PARAMETERS           | DESCRIPTION                                                                                          |
| -------------------- | ---------------------------------------------------------------------------------------------------- |
| deleteSignerResponse | status response of particular signer deletion from the contract created earlier in the Signzy system |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/8790c65d7d8535c49154)
