# Search Court Case Details by Court Case Reference ID

### Introduction

The Case Detail API, as the name suggests, is used to retrieve the details of a particular case by taking Case reference ID as input. This helps when individual case records need to be processed for further verification.

### API Usecase

This API will be used to get details of a court case just using the Case Reference ID.

### How to call the API

You are required to pass the access token received from the login call, an authorization header in the Court Cases (Case Detail) request along with other parameters.



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

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../courtcases" method="post" summary="Search Court Cases Details by Court Case Reference ID" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../courtcases`

\




\


This method is used to check for Court Cases against individuals/organizations
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task - case count
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.caseReferenceId" type="string" %}
Case Reference Id number of the individual/organization
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
   {
  	"result": {
  		"cases": {
  			"caseReferenceId": "...caseReferenceId...",
  			"courtType": "...courtType...",
  			"cnr": "...cnr...",
  			"courtName": "...courtName...",
  			"stateName": "...stateName...",
  			"cityName": "...cityName...",
  			"caseNumber": "...caseNumber...",
  			"petitioner": "...petitioner...",
  			"respondent": "...respondent...",
  			"nextHearingDate": "...nextHearingDate...",
  			"filingDate": "...filingDate...",
  			"lastUpdateDate": "...lastUpdateDate...",
  			"orders": ["..orders.."],
  			"history": ["..history.."]
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
    "task" : "caseDetail",
    "essentials": {
        "caseReferenceId": "..caseReferenceId.."
    }
  }

```
{% endtab %}

{% tab title="Response Parameters" %}


| PARAMETER NAME        | DESCRIPTION                                                                                                         |
| --------------------- | ------------------------------------------------------------------------------------------------------------------- |
| result                | The final response parameters are displayed here.                                                                   |
| result.cases          | The details of the registered cases against a searched name are stored here.                                        |
| cases.caseReferenceId | This parameter shows the reference ID assigned to a unique case.                                                    |
| case.courtType        | The type of court under which the case has been registered.                                                         |
| case.cnr              | The case number record is a unique number given to cases in District Courts of India.                               |
| cases.courtName       | The name of the court under which the case has been registered.                                                     |
| cases.stateName       | The name of the state in which the case has been registered.                                                        |
| cases.cityName        | The name of the city where the case has been registered is displayed here.                                          |
| case.caseNumber       | The case number is displayed by this parameter.                                                                     |
| case.petitioner       | The name of the petitioner in the registered case.                                                                  |
| case.respondent       | The name of the respondent in the registered case.                                                                  |
| case.nextHearingDate  | The next hearing date for the particular case is shown here.                                                        |
| case.filingDate       | The case filing date is displayed here.                                                                             |
| case.lastUpdateDate   | This parameter displays the last date when the case was updated.                                                    |
| case.orders           | This parameter returns an array which summarizes any particular orders issued by the court for the particular case. |
| case.history          | This parameter displays the case history for the particular case.                                                   |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/85a94010d22778c66ffb)
