# Advanced Image Forgery Check

## Advance Forgery Check <a href="#right-to-left-support" id="right-to-left-support"></a>

This API is used to find whether a given image is forged or not forged using Photoshop or any image manipulation tools. The input to the API is an image in compatible format (jp(e)g/png) upon which Signzy does forgery checks using proprietary algorithms.

You need to upload an image of ID card to check forgery. You may put direct URLs to ID cards, in case you have them.

For best results, please make sure the image you use fits tightly in camera view and is horizontally-aligned. This API also accepts direct URL to an image. Supported file formats are ".jpg", ".jpeg", ".png". Note: ".pdf" files are not supported.

Each image should be less than 2MB.

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/..your-patron-id.../forgeries" method="post" summary="Advance ID Card Forgery Check" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../forgeries`

\




\


This method is used to check the thorough details of ID card against forgery.
{% endswagger-description %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - Advance Forgery
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential image URL
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.url" type="object" %}
URL of the ID card image
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "essentials":{
        "url":"...image url..."
    },
    "result":{
        "image":  “....image url....”,

        "photoshopForgery": {
                "cloneDetection": {
                    "forgery": "yes | no",
                    "predictedRegions": "......image url......"
                },

                "splicingDetection": {
                    "forgery": "yes | no",
                    "predictedRegions": "......image url......"
                },

                "imageMetadata": {
                    "imageSource": {
                        "cameraMake": "....camera used to take the picture....",
                        "cameraModel": "....camera model used to take the picture....",
                        "software": "....Windows Photo Editor 10.0.10011.16384",
                        "modifyDate": "2018:12:14 14:59:54"
                    },
                "imageSourceLocation": {
                    "gpsLatitudeRef": "",
                    "gpsLatitude": [],
                    "gpsLongitudeRef": "",
                    "gpsLongitude": [],
                    "gpsTimeStamp": [],
                    "gpsDateStamp": ""
                },
                "forgery":"yes | no"
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
    "task":"advanceForgery",
    "essentials": {
        "url":"...image url..."
    }
}
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME                       | DESCRIPTION                                                                                                                                                                                   |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| image                                | The URL of the image being checked for forgery.                                                                                                                                               |
| photoshopForgery                     | This parameter checks for forgery using Photoshop software.                                                                                                                                   |
| photoshopForgery.cloneDetection      | This parameter detects duplicate image forgery against predicted regions.                                                                                                                     |
| photoshopForgery.splicingDetection   | This parameter detects image splicing forgery against predicted regions.                                                                                                                      |
| photoshopForgery.imageMetadata       | This parameter contains the details of the image source. The details include the camera make and model used to take the picture, any software used to modify the image and modification date. |
| photoshopForgery.imageSourceLocation | This parameter displays the image source location using GPS coordinates of longitude and latitude. The date and time stamp of the image source are also displayed.                            |
| result.forgery                       | This parameter displays whether image forgery has been conducted or not.                                                                                                                      |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/2a86a255e30e39584c07)



\
