# Text Match

## Introduction

Text-matching identifies either similar or exact matches between submitted work and other digital material. This material may include the Internet, electronic databases, etc.

## API Usecase

The purpose of text match is to quickly test out whether the user data entered is valid and matches the document. For example Name/DOB in Aadhar card. This API matches the fields on the recorded ID card to the ones we provide and from here we can decide whether the user has provided correct information against the ID card.

How to use the API
------------------

The users need to upload an image of the particular ID card to match. Placing direct URLs in place of ID cards, in case you have them, is also permissible.

For best results, please make sure the image you use fits tightly in camera view and is horizontally aligned.&#x20;

**Please note that each image/pdf should be less than 2MB.**

There are two important properties to note:

* essentials - This is the property that holds data for processing.
* fields - These are the data fields with values. &#x20;

## API Input Guidelines

* Pass a valid image URL
* Enter the field names correctly
* The image uploaded should be less than 2MB&#x20;

## Input parameters & Sample cURL request

{% tabs %}
{% tab title="Input Parameters" %}


| Parameter Name    | Description                               | Required/Optional |   |
| ----------------- | ----------------------------------------- | ----------------- | - |
| essentials        | contains the essential input data         | Required          |   |
| essentials.images | contains the image url                    | Required          |   |
| fields.dob        | contains the fields it matches data from. | Required          |   |
{% endtab %}

{% tab title="Sample cURL request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/textmatches' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: <accessToken Received After Login>' \
  --data-raw '{
   "essentials":{
      "images":[
         "https://preproduction-persist.signzy.tech/api/files/25778373/download/754571f4789f4807978cdd0de8d3edc8f7dd9903a7c74cbfaed87ef4a407cfcb.jpeg"
      ],
      "fields":{
         "DOB":"18/06/1994",
      }
   }
}
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name       | Description                               |
| -------------------- | ----------------------------------------- |
| id                   | a unique ID is to be provided             |
| patronId             | your patron ID                            |
| result               | Retrieves the output of the given request |
| result.dob           | Retrieves the result as dob and matches   |
| result.dob.score     | gives a score on the match                |
| result.dob.verb      | checks the verb                           |
| result.dob.bestMatch | gives the best match as an output         |


{% endtab %}

{% tab title="Sample API Response" %}
```
{
   "essentials":{
      "images":[
         "https://preproduction-persist.signzy.tech/api/files/25778373/download/754571f4789f4807978cdd0de8d3edc8f7dd9903a7c74cbfaed87ef4a407cfcb.jpeg"
      ],
      "fields":{
         "DOB":"18/06/1994"
      }
   },
   "id":"6141efa3f6d4030eae04d1ea",
   "patronId":"59536fbaec27fe12d4e9aa1d",
   "result":{
      "DOB":{
         "score":1,
         "verb":"MATCH",
         "bestMatch":"18/06/1994"
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



{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/..patron-id.../textmatches" method="post" summary="Text Match" %}
{% swagger-description %}
This method matches the text fields of ID cards
{% endswagger-description %}

{% swagger-parameter in="body" name="fields" type="string" %}
The text fields to be compared
{% endswagger-parameter %}

{% swagger-parameter in="body" name="images" type="string" %}
URL to the image which contains the text
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="string" %}
Contains the essential input data
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "essentials": {
        "images": [
            "...url..to..the..image..."
        ],
        "fields": {

            "..field1..":"..it's value..",
            "..field2..":"..it's value..",
            ..
            ..
            ..
            ..
            "..fieldN..":"..it's value.."
        }
    },
    "id": "5bxxxxxxxxxx474",
    "patronId": "5a9xxxxxxxxxxxx119d8",
    "result": {
            "field1": {
                "score": "score between 0-1",
                "verb": "NO MATCH/MATCH/PARTIAL MATCH",
                "bestMatch": "Best Match found"
            },
            "field2": {
                "score":  "score between 0-1",
                "verb": "NO MATCH/MATCH/PARTIAL MATCH",
                "bestMatch": "Best Match found"
            },
            ..
            ..
            ..
            "fieldN": {
                "score": "score between 0-1",
                "verb": "NO MATCH/MATCH/PARTIAL MATCH",
                "bestMatch": "Best Match found"
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
"essentials": {
"images":["..url..to..the..image.."],
"fields": {

   "..field1..":"..it's value..",
   "..field2..":"..it's value..",
   ..
   ..
   ..
   ..
   "..fieldN..":"..it's value.."

 }
```
{% endtab %}

{% tab title="Response Parameter" %}
| Parameter Name | Description                                                                                  |
| -------------- | -------------------------------------------------------------------------------------------- |
| result         | Contains the fields which contain the compared text and displays the match/no match scenario |

Help & support

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:

support@signzy.com
{% endtab %}
{% endtabs %}

|   |
| - |

