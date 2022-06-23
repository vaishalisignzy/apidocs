# Search Director/Secretary Negative List by DIN or PAN No.

### Introduction

The Signzy Director/Secretary Negative List is designed in compliance with the norms of AML/CFT software in banking/financial institutions as well as other regulated entities.

### API Usecase

Similar to the Entity Negative List, this API service can be used to check DIN/PAN information to check for high ranking officials or government members for any criminal records and other details pertaining to the same.

### How to call the API

You are required to pass the access token received from the login call, an authorization header in the Director/Secretary Negative List request along with other parameters.

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
| 401         | unauthorised                   |
| 404         | not found                      |
| 422         | processable entity             |

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../amlcfts" method="post" summary="Search Director/Secretary Negative List" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../amlcfts`

\




\


This method is used to check for AML/CFT data against director/secretary of an organization
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

{% swagger-parameter in="body" name="essentials.din" type="string" %}
Company identity Number of the organization.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
    "result":{
        "defaulterList": {
            "found" : "true/false",
            "data":[{
                "din": "..din..",
                "name": "..name..",
                "companyName": "..companyName..",
                "cin": "..cin..",
                "defaultingYear" : "..defaultingYear..",
                "dateOfRejection": "..dateOfRejection.."
            }]
        },
        "dormantList": {
            "found" : "true/false",
            "data":[{
                "din": "..din..",
                "name": "..name..",
                "companyName": "..companyName..",
                "cin": "..cin..",
                "dateOfRejection": "..dateOfRejection.."
            }]
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
    "task" : "directorNegativeList",
    "essentials": {
        "din": "..din.."
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
| defaulterList.data   | The data of the director member being searched is displayed here.                    |
| data.din             | The director identification number.                                                  |
| data.name            | The name of the director being searched.                                             |
| data.companyName     | The name of the company/organization.                                                |
| data.cin             | The company identification number.                                                   |
| data.defaultingYear  | The defaulting year, if any.                                                         |
| data.dateOfRejection | The date of rejection is displayed here, if found.                                   |
| result.dormantList   | This parameter checks the director information against dormant lists.                |
| dormantList.found    | This parameter verifies whether the entity match is true or false.                   |
| dormantList.data     | The data of the director member being searched is displayed here.                    |
| data.din             | The director identification number.                                                  |
| data.name            | The name of the director being searched.                                             |
| data.companyName     | The name of the company/organization.                                                |
| data.cin             | The company identification number.                                                   |
| data.dateOfRejection | The date of rejection is displayed here, if found.                                   |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/94549466fde403bfc4a5)
