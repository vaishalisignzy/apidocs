# Address Match

## Introduction

Similar to the Name Match product, the Address Match product takes two addresses as input and returns a match result of the two addresses. It is basically the same in functionality as Name Match but with addresses as parameters.&#x20;

## API Usecase

This API takes two addresses as inputs and uses them to match each other and returns a match result based on the inputs provided.

How to use  the API
-------------------

The users are required to pass the access token received from the login call as the authorization header in the Address Match request.

## API Input Guidelines

You will need to [login](https://docs-preproduction.signzy.tech/) before sending a search request. You are required to pass the access token received from the login call, as an authorization header in the Address Match request.&#x20;

For Address Match, the following exchange parameters can be used:

Input parameters and Sample cURL Request
----------------------------------------

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name          | Description                                                | Required/Optional |
| ----------------------- | ---------------------------------------------------------- | ----------------- |
| task                    | the task performed to match the dates from the given input | Required          |
| essentials              | contains the essential input data                          | Required          |
| essentials.addressBlock | contains both the input address                            | Required          |
| addressBlock.address1   | address 1 should be given as input                         | Required          |
| addressBlock.address2   | address 2 should be given as input                         | Required          |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/matchers' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: <accessToken Received After Login>' \
  {
    "task": "addressMatch",
    "essentials": {
        "addressBlock": {
            "address1": "NB-135, Ravi textile mills, samba",
            "address2": "NB-135, Ravi textile mills, samba"
        }
    }
}
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name                       | Description                                       |
| ------------------------------------ | ------------------------------------------------- |
| id                                   | a unique ID is to be provided                     |
| taskId                               | the id needed to perform the task                 |
| result                               | Returns the result of the Address Match request.  |
| result.address1\_vs\_address2\_match | stores the result                                 |
| addressDiffInKm                      | is to be left blank                               |
| addressDiffInMeters                  | to be left blank                                  |
| distanceMatch                        | no distance match                                 |
| addressMatch                         | Matches the address from the given inputs         |
| addressMatchJaroWinklerScore         | talks about the output details of Address Match.  |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
   "essentials":{
      "addressBlock":{
         "address1":"NB-135, Ravi textile mills, samba",
         "address2":"NB-135, Ravi textile mills, samba"
      }
   },
   "id":"6142f61ff6d4030eae04f946",
   "patronId":"6140993ef6d4030eae0497fb",
   "task":"addressMatch",
   "result":{
      "address1_vs_address2_matchResult":{
         "addressDiffInKm":"",
         "addressDiffInMeters":"",
         "distanceMatch":"No Match",
         "addressMatch":"Direct Match",
         "addressMatchJaroWinklerScore":"100.00"
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
| **422**     | processable entity              |

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../matchers" method="post" summary="Address Match" %}
{% swagger-description %}
This method is used to match two addresses
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Contains the access token which is returned as id field of log in request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="addressBlock" type="string" %}
Contains the two addresses to be compared for address match
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
The task to be performed - address match
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
     "result": {
          "address1_vs_address2_matchResult": {
            "pinMatchResult": "Match/No Match",
            "addressDiffInKm": ..addressDiffInKm...,
            "distanceMatch": "Match/No Match",
            "addressMatch": "Direct Match/Partial Match/No Match",
            "addressMatchJaroWinklerScore": "..addressMatchJaroWinklerScore from 0 to 100.00..."
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

   "task": "addressMatch",
   "essentials": {
     "addressBlock" : {
         "address1" : "...address1...",
         "address2" : "...address2..."
     }
   }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| Parameter Name | Description                                                                                                                                                                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result         | Returns the result of the Address Match request. The result contains details like distanceMatch, addressMatch, addressMatchJaroWinklerScore which talk about the output details of Address Match. |
{% endtab %}
{% endtabs %}

Help & support

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:

support@signzy.com

