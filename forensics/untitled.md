# ID Card Re-orientation

Sometimes, the image of the uploaded ID card may be inverted or tilted and while the frame is horizontal, the ID card may need to be rotated or its direction may need to be changed so that it faces upward direction for convenience This API by Signzy allows you to correct the orientation of the identity card.&#x20;

You need to upload an image of ID card to correct its orientation. You may put direct URLs of ID cards. Supported file formats are ".jpg", ".jpeg", ".png" . Each image should be less than 2MB. Please consider the points below for better performance:

1. Only images (JPG & PNG) are supported. PDF is not supported
2. This works only on Identity cards
3. Preferred to call this API before calling face match for improving accuracy
4. Don't use this API before calling extractions. Will increase your response time
5. Performance might be degraded if image is blurred
6. Default ttl is 3 years, which you can override
7. Performance might be bad if junk text are present in the background of the Identity card area

### Creating request for Reorienting Id Card

Use the following exchange parameters for Reorienting Id Card:

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../utils" method="post" summary="ID Card Reorientation" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../utils`

\




\


This method is used to reorient ID card.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token (returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - Reorient ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.url" type="string" %}
Contains the image URL of the ID card
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.ttl" type="string" %}
Contains the time string
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
      "essentials": {
          "url": "...image url...",
          "ttl": "..time string.."
      },
      "id": "..id..",
      "patronId": "..patron id..",
      "task": "reOrientId",
      "result": {          
              "message": "successfully reoriented",
              "status": "200",
              "reOrientedCard": "..reoriented image url..."          
      }
  }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {

   "task": "reOrientId",
   "essentials": {
     "url": "...image url......",
     "ttl": "...expiry time(optional parameter)... // Default value is 3 years"
   }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| **PARAMETER  NAME**     | **DESCRIPTION**                                                            |
| ----------------------- | -------------------------------------------------------------------------- |
| essentials              | Contains the essential input data.                                         |
| essentials.url          | Contains the image URL of the ID card uploaded.                            |
| essentials.id           | This parameter contains the unique Id received from the identity request.  |
| essentials.patronId     | This parameter returns the unique ID of the ID card holder.                |
| essentials.task         | The type of task to be performed - reorientId.                             |
| result                  | This holds final result parameters of the response.&#xD;                   |
| result.message          | Returns the message to the user about successful reorientation of ID card. |
| result.status           | This parameter returns the status code.                                    |
| result.reorientedIdCard | This parameter contains the URL of the reoriented ID card.                 |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/b2ebfca6faba493d622b)
