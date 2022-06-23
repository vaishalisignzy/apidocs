# Search Company Negative List by CIN

### Introduction

The Signzy Entity Negative List is designed in compliance with the norms of AML/CFT software in banking/financial institutions as well as other regulated entities. By cross-referencing various government records or Negative Lists.

### API Usecase

This API can use a CIN or Criminal Identification Number to check for the records of prior criminal activities for a certain suspicious identity/identities.

### How to call the API

You are required to pass the access token received from the login call, an authorization header in the Entity Negative List request along with other parameters.

### API Input Guidelines



### Input Parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

### Output Parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

### Sample CURL Request



### Sample API Response



### HTTP Response Codes

| Status Code | Description                    |
| ----------- | ------------------------------ |
| 200         | All response details are valid |
| 400         | bad request                    |
| 401         | unauthorized                   |
| 404         | not found                      |
| 422         | processable entity             |

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../amlcfts" method="post" summary="Search Company Negative List" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../amlcfts`

\




\


This method is used to check for AML/CFT data against blacklisted organizations
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task - entityNegativeList
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.cin" type="string" %}
Company identity Number of the organization.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
  	"result": {
  		"defaulterList": {
  			"found": "true/false",
  			"data": {
  				"companyName": "..companyName..",
  				"cin": "..cin..",
  				"dateOfRejection": "..dateOfRejection.."
  			}
  		}
  	}
  }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
    "task" : "entityNegativeList",
    "essentials": {
        "cin": "..cin.."
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME       | DESCRIPTION                                                                          |
| -------------------- | ------------------------------------------------------------------------------------ |
| result               | The final response parameters to be displayed as output.                             |
| result.defaulterList | This parameter checks the defaulter list to try and match the entity being searched. |
| defaulterList.found  | This parameter verifies whether the entity match is true or false.                   |
| defaulterList.data   | The data of the company/organization being searched is displayed here.               |
| data.companyName     | The name of the company/organization.                                                |
| data.cin             | The company identification number.                                                   |
| data.dateOfRejection | The date of rejection is displayed here, if found.                                   |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/2eda3a906a7efecf1b9c)
