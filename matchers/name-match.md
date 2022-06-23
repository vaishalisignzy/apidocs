# Name Match

## Introduction

The Name Match product takes two names input and returns a match result of two names. This ensures the authenticity of the name. Before conducting a name match, users need to log in after which a search request can be sent.

## API Usecase

This API ensures the authenticity of the name in the document. It matches the name with the given inputs.

How to use the API


You will need to [login](https://docs-preproduction.signzy.tech/) before sending a search request. You are required to pass the access token received from the login call, as an authorization header in the Name Match request.

## API Input Guidelines

* Both the inputs should be the same
* Before hitting the submit, check the spelling for it to return the match result.



The following exchange parameters can be used for conducting a Name Match:

## Input parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name       | Description                                                | Required/Optional |
| -------------------- | ---------------------------------------------------------- | ----------------- |
| task                 | the task performed to match the name from the given inputs | Required          |
| essentials           | contains the essential data                                | Required          |
| essentials.nameblock | contains the name parameters                               | Required          |
| nameblock.name1      | name1 input stored                                         |                   |
| nameblock.name2      | name2 input stored                                         |                   |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/matchers' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: <accessToken Received After Login>' \
 {
    "task": "nameMatch",
    "essentials": {
        "nameBlock": {
            "name1": "venkateshwar",
            "name2": "venkateshwar"
        }
    }
}
```
{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| id                                   | a unique id is to be provided                        |
| ------------------------------------ | ---------------------------------------------------- |
| patronId                             | your patronId                                        |
| result                               | Contains the output of the given request             |
| result.name1\_vs\_name2\_matchResult | tells the matched result                             |
| result.name1\_vs\_name2\_matchScore  | gives the score. for eg., '1' for the matched result |
| result.name1\_vs\_name2\_matchReason | gives a statement when the result is matched         |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
   "essentials":{
      "nameBlock":{
         "name1":"venkateshwar",
         "name2":"venkateshwar"
      }
   },
   "id":"6142ec6ff6d4030eae04f6d6",
   "patronId":"6140993ef6d4030eae0497fb",
   "task":"nameMatch",
   "result":{
      "name1_vs_name2_matchResult":"Direct Match",
      "name1_vs_name2_matchScore":1,
      "name1_vs_name2_matchReason":"Both names matched completely"
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
| **422**     | processable entity              |

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../matchers" method="post" summary="Name Match" %}
{% swagger-description %}
This method matches the entered two names
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Contains the access token which is returned as id field of login request.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="nameBlock" type="string" %}
Contains the two names which are to be compared for a successful name match.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains the essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task " type="string" %}
The task to be performed - name Match
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
     "result": {
         "name1_vs_name2_matchResult": "Direct Match/Partial Match/No Match",

      }
   }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {

   "task": "nameMatch",
   "essentials": {
     "nameBlock" : {
         "name1" : "...name1...",
         "name2" : "...name2..."
     }
```
{% endtab %}

{% tab title="Response Parameter" %}
| Parameter Name  | Description                                                                                                         |
| --------------- | ------------------------------------------------------------------------------------------------------------------- |
| result          | Contains the output of the given request. Here, it returns one of three values: Direct Match/Partial Match/No Match |
{% endtab %}
{% endtabs %}

Help & support

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:

support@signzy.com

