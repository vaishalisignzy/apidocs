# Get Verification Data

## Introduction

Using the unique request ID that was generated in the previous API, the Entity Onboarding get request is used to verify the details provided by the users against government records and display the details as output. Please note that before verification, the details entered by the user must be manually validated.

## How to use the API

You will need to login before sending request. You are required to pass the access token received from the login call, as authorization header in the Entity Onboarding GET Request request along with essentials and task

To get the VE response in the "getData" request you have to pass the "requestId" which you will get in the previous input verification data (save) response.

We will also push the VE response in the callback url as well, if it is provided in the input verification "save" request

Use the following exchange parameters for Entity Onboarding Get Request

## Input Parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters          | Description                 |
| ------------------- | --------------------------- |
| task                | to save data                |
| essentials          | contains the essential data |
| essentials.inputObj | contains input objects      |
{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl 'https://signzy.tech/api/v2/patrons/<patron-id>/entityonboardings' \
  --header 'accept: */*' \
  --header 'accept-language: en-US,en;q=0.8' \
  --header 'authorization: <Access-Token>' \
  --header 'content-type: application/json' \
'{
    "task": "saveData",
    "essentials": {
        "inputObj": "...inputObj.."
    }
}'
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Output Parameters" %}
| Parameters  | Description |
| ----------- | ----------- |
|             |             |
|             |             |
|             |             |


{% endtab %}

{% tab title="Sample API Response " %}
```
// Some code
```


{% endtab %}
{% endtabs %}

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../entityonboardings" method="post" summary="Get Verification data" %}
{% swagger-description %}
This method is used for individual onboarding get request..
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - get Data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.requestID" type="string" %}
Contains the unique get request ID	
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
	"task": "getData",
	"essentials": {
        "requestId": "..requestId...."
    }
}
```
{% endtab %}

{% tab title="Response Parameters" %}


### Output Parameters

#### Id card block

**verificationStatus block**

| PARAMETERS | DESCRIPTION                                                                                                                                     |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| verified   | whether data is verified with the Govt. database or not.(returns string value i.e."true/false")                                                 |
| message    | returns message according to verification status (eg:verification completed with positive result / verification completed with negetive result) |

**Forgery block**

**Final inference**

| PARAMETERS | DESCRIPTION                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| forgery    | This forgery takes a decision based on parameter like **face is found or not** , **QR code is readable or not** , **colors is found or not** and **imageRelatedData is found or not**. If it is a aadhaar and QR code is readable then data in the QR code is matched with the data in the image. If it is not same then it says the id card is **FORGED**, and if QR code is not readable then it is considered to take a decision whether the IDCard is **FORGED or NOT FORGED**. For non-aadhaar id cards it considers the face, imageRelatedData and color. If one of them is not found it says that the image is **FORGED** and if everything is found then it says id card is **NOT FORGED**.(returns string value i.e." FORGED or NOT FORGED ") |
| message    | returns message according to the forgery                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

**Element wise inference**

**Face block**

| PARAMETERS | DESCRIPTION                                                                             |
| ---------- | --------------------------------------------------------------------------------------- |
| found      | whether face is found on id card or not.(returns string value i.e."true/false")         |
| message    | returns message which specifies face is found or not(eg: face is found / No face found) |

**QR Code block**

| PARAMETERS | DESCRIPTION                                                                                                  |
| ---------- | ------------------------------------------------------------------------------------------------------------ |
| found      | whether qrCode is found on id card or not.(returns string value i.e."true/false")                            |
| match      | whether the data is found in qrCode or not(returns string value i.e."true/false") its only valid for aadhaar |
| message    | returns message which specifies QR data is found or not(eg: QR data is not readable / QR data is found)      |

**Colors block**

| PARAMETERS | DESCRIPTION                                                                                                                                          |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| found      | whether id is found on id card photocopied or not.(returns string value i.e."true/false")                                                            |
| message    | returns message which specifies id card is photocopied or not(eg: This seems to be photocopied ID card / This doesnot seem to be a photocopied file) |

**inputMatcher block**

**Final Inference**

| PARAMETERS   | DESCRIPTION                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| forgery      | It does a text match of name ,dob ,idNo and pincode(only for aadhaar / passport) with the text on idcard.(returns string value i.e."NO/YES")                                                                                                                                                                                                                                                                                                                                                                                |
| forgeryScore | <p>Its a score indicates amount of forgery done and its varies from (0-100)</p><ul><li>0 means all data in id card block is matched with the data present in the image that is given as input to API.</li><li>100 means no data in the id card block is matched with the data present in the image that is given as input to API.</li><li><p>Value in between 0 to 100 means some of the data in id card block is matched with the data present in the image that is given as input to API.</p><ul><li></li></ul></li></ul> |

**Element wise inference**

**Fields block**

| PARAMETERS | DESCRIPTION                                                                                              |
| ---------- | -------------------------------------------------------------------------------------------------------- |
| name       | Name that need to be matched with the name on id card.(returns string value i.e."Direct Match/No Match") |
| dob        | dob that need to be matched with the dob on id card.(returns string value i.e."Match/No Match")          |
| idNo       | idNo that need to be matched with the idNo on id card.(returns string value i.e."Match/No Match")        |

**Face Extraction block**

| PARAMETERS     | DESCRIPTION                        |
| -------------- | ---------------------------------- |
| faceExtraction | Url of the image of extracted face |

#### Video block

**Final Interference**

| PARAMETERS             | DESCRIPTION                                                           |
| ---------------------- | --------------------------------------------------------------------- |
| url                    | url of the video                                                      |
| matchImage             | Image which the user will pass for verifing the person in the video.  |
| signzyVerifiableString | Random string that user need to speak in the video.                   |
| seconds                | An array of time interval at which the face will be tracked in video. |
| faceLandmarks          | Direct url of the face image tracked in given match image.            |

**Element Interference**

**videoMatch block**

| PARAMETERS      | DESCRIPTION                                                                                          |
| --------------- | ---------------------------------------------------------------------------------------------------- |
| matchAudioScore | Percentage of match between the Signzy verifiable string and the string spoken by user in the video. |

**forensics block**

**staticRisk block**

| PARAMETERS  | DESCRIPTION                                                                |
| ----------- | -------------------------------------------------------------------------- |
| staticPhoto | It checks the liveliness of video (returns string value i.e."true/false"). |

**videoLandMarks block**

| PARAMETERS | DESCRIPTION                     |
| ---------- | ------------------------------- |
| result     | The url of face track in video. |

**videoFaceMatch block**

| PARAMETERS      | DESCRIPTION                                                          |
| --------------- | -------------------------------------------------------------------- |
| videoImages     | Snap shots taken from video at different time interval.              |
| finalMatchImage | Image which the user will pass for verifing the person in the video. |

**matchStatistics block**

| PARAMETERS      | DESCRIPTION                                                                                                              |
| --------------- | ------------------------------------------------------------------------------------------------------------------------ |
| coVariance      | percentage of coVariance between the different face match scores of the snap shot image of the video to the match image. |
| matchPercentage | Average percentage of face match between different snap shots of the video to the match image .                          |

#### Documents block

**verificationData block**

| PARAMETERS       | DESCRIPTION                                                         |
| ---------------- | ------------------------------------------------------------------- |
| verificationData | It gives data sent by bank for that particular transaction request. |

**nameVerificationStatus block**

| PARAMETERS | DESCRIPTION                                                                                                                     |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------- |
| verified   | Does comparison between the input beneficiaryName and beneName in verification data.(returns string value i.e."Match/No Match") |
| message    | Returns message according to the verification result(eg: Verifcation done with Match/No Match result)                           |

**mobileVerificationStatus block**

| PARAMETERS | DESCRIPTION                                                                                                                         |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| verified   | Does comparison between the input beneficiaryMobile and beneMobile in verification data.(returns string value i.e."Match/No Match") |
| message    | Returns message according to the verification result(eg: Verifcation done with Match/No Match result)                               |


{% endtab %}
{% endtabs %}
