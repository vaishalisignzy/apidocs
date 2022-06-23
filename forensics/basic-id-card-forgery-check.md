# Basic ID Card Forgery Check



This API checks the forgery on the provided ID card. It detects forgery on basis of following three criteria.

1. **Type of identity card** - i.e. whether the id type submitted by the user actually matches the id type predicted by the ML system
2. **Photo-copy check** - i.e. whether the image submitted is a photocopied file or not
3.  **Check text information** - i.e. whether text present in the image matches the user input

    You need to upload an image of ID card to check forgery. You may put direct URLs to ID cards, in case you have them.

    For best results, please make sure the image you use fits tightly in camera view and is horizontally-aligned. This API also accepts direct URL to an image. Supported file formats are ".jpg", ".jpeg", ".png". Note: ".pdf" files are not supported.

    Each image should be less than **2MB**.

Using the data that is input by the user, the API service can conduct checks on multiple fields of the ID card. Along with the image, the user has to manually enter the data fields which is required to be checked for forgery.

You need to upload an image of ID card to check forgery. You may put direct URLs to ID cards, in case you have them. For best results, please make sure the image you use fits tightly in camera view and is horizontally-aligned. This API also accepts direct URL to an image. Supported file formats are ".jpg", ".jpeg", ".png". Note: ".pdf" files are not supported.

Each image should be less than 2MB.

Below are the optimal threshold you can use for text-match.

1. Numbers, dates and Unique identity fields - 100
2. Names - 94
3. Addresses like - 70

**Points to note:**

1. For best results make sure the background of image should be clear, it should not have image of any other ID card.
2. This API does not detect face.
3. Any random image will be classified as unknown by the system.

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/..patron-id.../forgeries" method="post" summary="Basic ID Card Forgery Check" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../forgeries`

\




\


This method is used to check the basic details of ID card against forgery.
{% endswagger-description %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - Basic Forgery
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.images" type="object" %}
URL of the ID card image
{% endswagger-parameter %}

{% swagger-parameter in="body" name="verifyData" type="string" %}
Contains the values of Identity type
{% endswagger-parameter %}

{% swagger-parameter in="body" name="verifyData.identityCard" type="object" %}
Contains the type of ID card which is uploaded.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="textMatch" type="string" %}
Compares the values of text fields for verification.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "essentials": {
        "images": [
            "...url..to..the..image..."
        ],
        "verifyData":{
            "identityCard":{
                "type":"aadhaar | individualPan | businessPan | dl | passport | unknown"
            },
            "textMatch":{
                "fields": {

                   "..field1..":"..it's value..",
                   "..field2..":"..it's value..",
                   "..fieldN..":"..it's value.."
                }
            }
        }
    },
    "id": "5bxxxxxxxxxx474",
    "patronId": "5a9xxxxxxxxxxxx119d8",
    "task":"basicForgery",
    "result": {
        "forgery": "NOT FORGED | FORGED",
        "message": "message about issue if found any.",
        "identityCard": {
            "match": "yes | no",
            "predictedType": "aadhaar | individualPan | businessPan | dl | passport | unknown"
        },
        "color": {
            "forgery": "NOT FORGED | FORGED",
            "message": "message about the file.",
            "dominantColors": [
                "#colorCode",
                "#colorCode",
                ..
                ..
                ..
                "#colorCode"
            ]
        },
        "textMatch": {
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
            ..
            "fieldN": {
                "score": "score between 0-1",
                "verb": "NO MATCH/MATCH/PARTIAL MATCH",
                "bestMatch": "Best Match found"
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
    "task":"basicForgery",
    "essentials": {
        "images":["..url..to..the..image.."],
        "verifyData":{
            "identityCard":{
                "type":"aadhaar | individualPan | businessPan | dl | passport | unknown"
            },
            "textMatch": {
                "fields": {

                   "..field1..":"..it's value..",
                   "..field2..":"..it's value..",
                   ..
                   ..
                   ..
                   ..
                   "..fieldN..":"..it's value.."
                }
            }
        }
    }
}
```
{% endtab %}

{% tab title="Response Parameters" %}

{% endtab %}
{% endtabs %}
