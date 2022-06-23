# Date Match

## Introduction

Using this API as a service is essential in cases where the user entered 'date' must match the exact date on records. One can enter two dates as an input and it returns a  match result based on the inputs provided.

## API Usecase

This API is used for the matching the dates that are mentioned in the records for a smoother verification process.

## How to use the API

The Date Match product takes two dates input and returns back a match result of two dates. You will need to log in before sending a search request. This service is important in cases where the user entered date needs to be matched with the exact date on record. For example: if a user enters date like 20/12/1990 as DOB and the actual DOB is 23/12/1992, the API will return month and year as a match and return the difference in a number of days as well.

You are required to pass the access token received from the login call, as an authorization header in the Date Match request.

## API Input Guidelines

* The dates entered must match each other.
* This API needs the date to be manually entered.
* The default value for this parameter is **dd/mm/yyyy**
* If the desired pattern does not match with this pattern then you have to select a format value given below which matches your choice.



Use the following exchange parameters for Date Match.

## Input parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/Optional | Description    |
| -------------- | ----------------- | -------------- |
| task           | Required          | 'datematch'    |
| essentials     | Required          |                |
| date1          | Required          | 'enter date 1' |
| date2          | Required          | 'enter date2'  |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/matchers' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: <accessToken Received After Login>' \
{
    "task": "dateMatch",
    "essentials": {
        "dateBlock": {
            "date1": "02/09/2021",
            "date2": "02/09/2021"
        }
    }
}
```
{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description                                                                                         |
| -------------- | --------------------------------------------------------------------------------------------------- |
| id             | unique id                                                                                           |
| patronID       | your patron id                                                                                      |
| fullDateMatch  | checks if the full date matches                                                                     |
| dateMatch      | matches the two dates                                                                               |
| monthMatch     | It matches the months entered whether they are entered as 'april' or '04' it doesn't affect the API |
| yearMatch      | It checks the year entered.                                                                         |
| diffInDays     | It tells that by how much does the date differs                                                     |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
   "essentials":{
      "dateBlock":{
         "date1":"02/09/2021",
         "date2":"02/09/2021"
      }
   },
   "id":"6142f798f6d4030eae04f9a5",
   "patronId":"6140993ef6d4030eae0497fb",
   "task":"dateMatch",
   "result":{
      "date1_vs_date2_matchResult":{
         "fullDateMatch":"Match",
         "dateMatch":"Match",
         "monthMatch":"Match",
         "yearMatch":"Match",
         "diffInDays":0
      }
   }
}
```
{% endtab %}
{% endtabs %}

## HTTP Response codes&#x20;

| Status code | Description                     |
| ----------- | ------------------------------- |
| **200**     | All response details are valid  |
| **404**     | Not found                       |
| **400**     | bad request                     |
| **401**     | unauthorized                    |
| **422**     | unprocessable entity            |

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../matchers" method="post" summary="Date Match" %}
{% swagger-description %}
This method allows the matching of two dates.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="dateBlock" type="string" %}
Contains the two dates entered as input
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
The type of task to be performed - 
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
     "result": {
         "date1_vs_date2_matchResult": {
                 "fullDateMatch": "Match/No Match",
                 "dateMatch": "Match/No Match",
                 "monthMatch": "Match/No Match",
                 "yearMatch": "Match/No Match",
                 "diffInDays": ..diffInDays...
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

   "task": "dateMatch",
   "essentials": {
     "dateBlock" : {
         "date1" : "...date1(Ex: Format: dd/mm/yyyy)...",
         "date2" : "...date2(Ex: Format: dd/mm/yyyy)..."
     }
```
{% endtab %}

{% tab title="Response Parameter" %}
| Parameter Name                | Description                                                                                                                                                                |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                        | Contains the result of date1\_vs\_date2\_matchResult parameter                                                                                                             |
| date1\_vs\_date2\_matchResult | Contains the values of comparing two dates and the returned data fields like fullDateMatch, date Match, month Match etc. The output of all fields is one of Match/No Match |
{% endtab %}
{% endtabs %}

Help & support

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:

support@signzy.com

