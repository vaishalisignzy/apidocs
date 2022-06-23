# Image Quality Check

## Image Quality <a href="#right-to-left-support" id="right-to-left-support"></a>

Image quality plays a crucial role for API’s that require extraction, verification, face extraction and similar kinds of algorithms. For the API’s to deliver higher scores in terms of accuracy, image quality needs to be checked first and this API detects the same and decides whether it is usable for further processing. You may use direct URLs over images as well, in case you have them.

To determine the quality of image we give a score out of 0-1, the model is trained on the basis of 4 types of distortions. This API can be used as an add-on to existing product to provide better user experience.

The quality param(qualityParameter) in the request body is optional, by default it's value is **all**.

The product has four types of quality checks namely:

1. **Sharpness check** - This feature tells if the image is sharp i.e. no blur in image is present. 0 is blur, 1 is sharp.
2. ![](https://docs-staging.signzy.tech/assets/images/image\_quality\_blur.jpg)
3. **Brightness check** - This feature tells if the image is bright enough for OCR. 0 is dark, 1 is good bright.
4. ![](https://docs-staging.signzy.tech/assets/images/image\_quality\_brightness.jpg)
5. **Compression quality check** - This feature tells if the image is pixelated. 0 is compressed, 1 is good.
6. ![](https://docs-staging.signzy.tech/assets/images/image\_quality\_compression.jpg)
7. **Text readable** - This tells whether the text present on the image is readable or not. 0 is bad, 1 is good.
8. ![](https://docs-staging.signzy.tech/assets/images/image\_quality\_text.jpg)

Each image should be less than **2MB**.\


{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/….patron...id.../imagequality" method="post" summary="Image Quality Check" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/….patron...id.../imagequality`

\




\


This method is used to check the quality of two images.
{% endswagger-description %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.files" type="array" %}
Enables storing multiple URLs
{% endswagger-parameter %}

{% swagger-parameter in="body" name="qualityParameter" type="string" %}
Used to describe one of four characteristics - all | blur | brightness | compressionQuality | textQuality"
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "essentials": {
        "files": ["...url..to..file.." ] 
    },
    "id": "5baXXXX",
    "patronId": "5a9XXXX",
    "result": {
       "qualityScores": {
           "sharpness": {
               "score": "0 to 1",
               "valid": "yes | no"
           },
           "brightness": {
               "score": "0 to 1",
               "valid": "yes | no"
           },
           "compressionQuality": {
               "score": "0 to 1",
               "valid": "yes | no"
           },
           "textQuality": {
               "score": "0 to 1",
               "valid": "yes | no"
           }
       },
       "extractionQuality": "veryLow | low | medium | high",
       "score": "0 to 1",
       "msg": "done",
       "status": "200"
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
    "files": ["...url..to..file.. (array of length one)"],
    "qualityParameter":"all | blur | brightness | compressionQuality | textQuality"
  }
}
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME                   | DESCRIPTION                                                                                                                        |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| result                           | This holds the final response parameters.                                                                                          |
| result.qualityScores             | This parameter assigns scores on the basis of overall image quality.                                                               |
| qualityScores.sharpness          | This parameter assigns scores based on the sharpness of the image.                                                                 |
| sharpness.score                  | This parameter returns a value between 0 and 1.                                                                                    |
| sharpness.valid                  | This parameter returns the validity as Yes/No.                                                                                     |
| qualityScores.brightness         | This parameter assigns scores based on the brightness of the image.                                                                |
| brightness.score                 | This parameter returns a value between 0 and 1.                                                                                    |
| brightness.valid                 | This parameter returns the validity as Yes/No.                                                                                     |
| qualityScores.compressionQuality | This parameter assigns scores on the basis of compression quality of the image.                                                    |
| compressionQuality.score         | This parameter returns a value between 0 and 1.                                                                                    |
| compressionQuality.valid         | This parameter returns the validity as Yes/No.                                                                                     |
| qualityScores.textQuality        | This parameter assigns scores on the basis of the quality of text on the image.                                                    |
| textQuality.score                | This parameter returns a value between 0 and 1.                                                                                    |
| textQuality.valid                | This parameter returns the validity as Yes/No.                                                                                     |
| result.extractionQuality         | This parameter determines the overall extraction quality of the image and returns one of the following - very Low/low/medium/high. |
| extractionQuality.score          | This parameter returns a score between 0 to 1.                                                                                     |
| extractionQuality.msg            | This returns a status message.                                                                                                     |
| extractionQuality.status         | The status code is displayed here.                                                                                                 |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/b04b79a1012ff58c0c91)
