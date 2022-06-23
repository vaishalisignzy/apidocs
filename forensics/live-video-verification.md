# Video Verification



This API is a slight contrast to the Video Verification product we have seen earlier. This API takes the image of the user ID and a pre-recorded video as input and gives a score on the basis of which we can tell how much the face in the image matches to the face found in the video.&#x20;

Using similar advanced fraud detection features as we have seen in Video Verification, this API also provides a simple yet secure solution for customer on-boarding and does not require live video capture of the user. However, the uploaded video file size must match the requirements of the service for which it is being uploaded.

This API receives input as a video file and performs similar analytical actions as our main iframe product

1. Extract face pictures from the video.
2. Match face images against the video and give score for each image. This would mean user can give option input of face array. ( To be billed as separate and added to billing of face match API).
3. Give video quality

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...your-patron-id.../videoforensics" method="post" summary="Video Verification " %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../videoforensics`

\




\


This method is used to verify the video of the individual against an uploaded ID proof.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - videoAPImode
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.toMatchImage" type="string" %}
Contains the image Face Image which is to be matched against the faces in the video. Supported formats are JPEG, JPG, PNG, PDF. If not passed, face match will not be done.which is to be matched.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.videoUrl" type="string" %}
Contains Input video url (.mp4, .blob, .webm) containing face.customization details for the video 
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
        "essentials": {
            "toMatchImage": "...image url...",
            "videoUrl": "...video url..."
        },
        "id": "...xxxx...",
        "patronId": "...xxxx....",
        "task": "videoApiMode",
        "result": {
            "faceMatch": {
                "matchScore": "...some float value...",
                "isMatch": "no/yes"
            },
            "extractedFacesFromVideos": [
                "...extracted faces image url from video...."                
            ],
            "videoQuality": {
                "VideoQualityScore": "...score between 0-100...",
                "isValid": "yes/no"
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
      "task" : "videoApiMode",
      "essentials" : {
          "toMatchImage" : "...Image Url...",
          "videoUrl" : "...video Url..."
      }
    }
```
{% endtab %}

{% tab title="Response Parameters" %}
| FIELD NAME               | DESCRIPTION                                                                   |
| ------------------------ | ----------------------------------------------------------------------------- |
| matchScore               | Face match score (0 - 100)                                                    |
| isMatch                  | Whether face matched or not ( yes or no)                                      |
| extractedFacesFromVideos | Image urls of faces in the video (first 3 faces based on Depth first search ) |
| videoQualityScore        | Quality of video ( 0 - 100)                                                   |
| isVideoValid             | Whether video can be accepted (yes or no)                                     |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/6e9e904b1818186039e5)
