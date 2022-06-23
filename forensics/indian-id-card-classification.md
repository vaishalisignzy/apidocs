# Indian ID Card Classification



This product offers an interesting feature in which it can determine the type of ID that has been uploaded by the user. The API figures out the classification and then returns the ID type with a success message. For example, if you have uploaded the front image of your Aadhaar card, the result message is shown as successful and the ID type “Aadhaar” is returned as output.

There are two important properties to note.

1. task - Indian Id Card (only Indian ID cards are supported currently). More to be coming up soon.\

2. essentials - This is the property which holds data for processing.

files - array of images to be processed (batch processing coming soon, currently only one image at a time is allowed).

You need to upload an image of Indian ID card to classify. You may put direct URLs to ID cards, in case you have them.

For best results, please make sure the image you use fits tightly in camera view and is horizontally-aligned. This API also accepts direct URL to an image.

Each image/pdf should be less than 2MB.

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../idclassifications" method="post" summary="Indian ID Card Classification" %}
{% swagger-description %}
**Production URL:**

\


 

****

 

`https://signzy.tech/api/v2/patrons/..patron-id.../idclassifications`

\


****

\


****

This method is used to identify the details of an Indian ID card
{% endswagger-description %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - Indian ID card
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the image urls of the uploaded ID card
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.files" type="object" %}
Contains the URLs of the image files
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
    "essentials": {
        "files": ["..url..to..the..image.."]
    },
    "id": "5babXXXXX0c6",
    "patronId": "5a905XXXXX19d8",
    "task": "indianIdCard",
    "result": [{
        "status": "success",
        "classification": {
            "status": "success",
            "idType": "aadhaar/individualPan/businessPan/unknownPan/passport/dl/unknown",
            "message": "Successfully completed."
        }
    }]
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
    "task": "indianIdCard",
    "essentials": {
        "files": [
            "..url..to..the..image.."
        ]
    }
}
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME         | DESCRIPTION                                                                                                                                    |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| result                 | This holds the final response parameters.                                                                                                      |
| result.status          | The status of completion is displayed here i.e whether status is success/fail.                                                                 |
| result.classification  | This contains the parameters that denote whether the ID type has been classified successfully and which type of ID the uploaded image denotes. |
| classification.status  | Displays whether the id type classification is successful or not.                                                                              |
| classification.idType  | This parameter denotes the id type as one of the following - aadhaar/individualPan/businessPan/unknownPan/passport/dl/unknown                  |
| classification.message | This parameter displays a message upon successful classification of id type.                                                                   |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/c9a764a41052ed0a975e)
