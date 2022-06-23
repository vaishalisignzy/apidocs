# Live Video Verification

## Live Video Verification Workflow <a href="#right-to-left-support" id="right-to-left-support"></a>

Video verification is an iframe-based product which allows secure end-customer on-boarding digitally. It helps you capture live randomized video of your end-user and match against a predefined ID proof/photograph that is uploaded by the user.. The system has advanced video fraud detection capabilities which eliminate identity theft in user on-boarding process. This ensures a simple yet secure customer on-boarding. This makes video verification workflow an important process to Signzy’s Forensics process.

If you have a web based application (be it mobile web or desktop web) you can access this through an iframe. In your mobile application you can use web view. If you have ever integrated iframe based payment gateways, you would find this to be very similar:

Bet you already knew this, so let’s get to the know- how of how this is done..

You can check the browser compatibility from the list of browsers provided below:



You can check the **browser compatibility**.

| OS                  | PLATFORM | BROWSER    | COMPATIBILITY | VIDEO RECORDING TYPE |
| ------------------- | -------- | ---------- | ------------- | -------------------- |
| Windows 7           | Web      | Chrome     | Yes           | Auto                 |
| Windows 10          | Web      | Chrome     | Yes           | Auto                 |
| Linux Ubuntu 16.0.4 | Web      | Chrome     | Yes           | Auto                 |
| macOS-Mojave        | Web      | Chrome     | Yes           | Manual               |
| Windows 7           | Web      | Firefox    | Yes           | Auto                 |
| Windows 10          | Web      | Firefox    | Yes           | Auto                 |
| Linux Ubuntu 16.0.4 | Web      | Firefox    | Yes           | Auto                 |
| macOS-Mojave        | Web      | Firefox    | Yes           | Manual               |
| Windows 7           | Web      | Opera      | Yes           | Auto                 |
| Windows 10          | Web      | Opera      | Yes           | Auto                 |
| macOS-Mojave        | Web      | Safari     | Yes           | Manual               |
| Windows 7           | Web      | UC Browser | Yes           | Auto                 |
| Windows 10          | Web      | UC Browser | Yes           | Auto                 |
| Windows 7           | Web      | IE11       | Yes           | Manual               |
| Windows 10          | Web      | IE11       | Yes           | Manual               |
| Windows 10          | Web      | Edge       | Yes           | Manual               |
| Android 7+          | Mobile   | Chrome     | Yes           | Auto                 |
| Android 7+          | Mobile   | Firefox    | Yes           | Auto                 |
| Android 7+          | Mobile   | UC Browser | Yes           | Auto                 |
| Android 7+          | Mobile   | Opera      | Yes           | Auto                 |
| iOS                 | Mobile   | Chrome     | Yes           | Manual               |
| iOS                 | Mobile   | Safari     | Yes           | Manual               |

### Product Flow

1. User initiates a video verification.
2. Signzy iframe takes over and does a randomized video session with the user of 10 seconds.
3. This video data now passes onto the backend fraud engine. Final output of the product gives 2 different scores and two Boolean values which achieves the following.
   * Predict if the user present in the video is same as the one in ID proof.
   * Ensure that the a live person was present infront of the camera. Static photo risk and Pre-recorded video risk scores indicate chances of fraud on this front.

### Integration Flow

#### Logging in

You would have understood logging in by now. In case you are only integrating video verification you can understand logging in from [Authentication section.](https://docs-staging.signzy.tech/)

#### Create URL

Once you are logged in, you need to initiate video verification session by creating a url in the following manner.

**Note:** Before initiating a video verification session you will also need to pass a matchURL which can be an array of ID/ face images. You can use your own filesystem or use our system as explained in our [file exchange](https://docs-staging.signzy.tech/file-exchange) section. please note that **rotated images are not supported**.

You could also provide optional video record time between 5 to 30 seconds in field named customVideoRecordTime. By default it is 10 seconds. You can hide the default signzy logo present at the top and bottom position by passing in the two parameters hideTopLogo and hideBottomLogo as true, by default there value is false, these are optional parameters. while integrating it in iframe allow the **microphone and camera** in attribute of iframe tag. **allow="camera; microphone;"**

#### Color Customization

You can change the colors of iframe screen by passing in the following json along with the request body. Remember this is an optional parameter, it will use the default colors if you don't use it. This feature is **not supported in internet explorer**. Use Hex code for values of the color.

```
customizations: {          
            "--main-bg-color": "...main background color...",
            "--capture-bg": "...capture screen header color for mobile...",
            "--timer-color": "...color of the timer...",
            "--number-panel-bg": "...background color of the number...",
            "--number-color": "...color of the numbers...",
            "--box-shadow-color": "...shadow of the box...",
            "--box-choice-border-top-color": "...border top color...",
            "--gradient-inner-color": "...inner color of the progress bar...",
            "--gradient-outer-color": "...outer color of the progress bar...",
            "--passive-text-color": "...sub heading in last page...",
            "--finished-text-color": "...main heading in last page...",
            "--timer-capture-color": "...timer color...",
            "--hint-wrapper-capture": "...header background color of screens for desktop flow...",
            "--button-bg-color": "...button background color...",
            "--button-bg-color-hover": "...button background color on hover...",
            "--footer-instructions-bg": "...background color of the footer...",
            "--main-heading": "...color of the main heading...",
            "--sub-heading": "...color of the sub heading..."
            "--capture-screen-instruction-color": "...instructions color of the capture screen...",
            "--button-text-color": "...text of the button...",
            "--button-text-color-hover": "...text color of button on hover...",
            "logoUrl": "...url of the logo image..."
        }
```



Above json showing the all properties, you can use only which u want and leave other to default.\


The Video verification API uses the id verification(**idCardVerification**) parameter to check for two cases, this is an optional parameter, default value is false:

1. True- In this case, the facial id is scanned and accepted and the parameter moves to verify your identification card and confirm the id number verbally.
2. False- In this case, the parameter does not ask the user to hold up the ID card.

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...your-patron-id.../videoiframes" method="post" summary="Live Video Verification" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../videoiframes`

\




\


This method is used to verify the video of the individual against an uploaded ID proof.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorisation" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - URL
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.matchImage" type="string" %}
Images Array where maximum two images are allowed
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.customVideoRecordTime" type="string" %}
number between 5-30
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.hideTopLogo" type="string" %}
Returns true/false
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.hideBottomLogo" type="string" %}
Returns true/false
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.callbackURL" type="string" %}
URL on which response to be pushed once the Video Verification is Completed
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.redirectURL" type="string" %}
URL on which iframe to be redirected once the Video Verification is Completed
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.idCardVerification" type="string" %}
Returns True/False
{% endswagger-parameter %}

{% swagger-parameter in="body" name="customizations" type="string" %}
Contains the customization details for the video 
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
         "result": {
             "token": "jGdJgjIWpcqVUw2Vd5D6",
             "videoUrl": "..URL to be loaded in iframe..."
          }
     }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
      "task" : "url",
      "essentials" : {
          "matchImage" : ["Images Array maximum two images are allowed"],
          "customVideoRecordTime": "..number between 5-30...(optional)",
          "hideTopLogo":"true/false",
          "hideBottomLogo":"true/false",
          "callbackUrl" : "...URL on which response to be pushed once the Video Verification is Completed...",
          "redirectUrl" : "...URL on which iframe to be redirected once the Video Verification is Completed...",
          "idCardVerification":"true/false",
          "customizations":{}
      }
    }
```
{% endtab %}

{% tab title="Response Parameters" %}

{% endtab %}
{% endtabs %}



#### Load videoURL

Once you receive the videoURL.

* In case of webapp product,load the URL in the iframe
* In case of mobile APP, **WebView is not supported**, but you can use chrome custom tab.\
  To use this just import following in your **app.gradle** file

```
implementation 'saschpe.android:customtabs:2.0.0'
```

and instead of Webview, use:

```
CustomTabsIntent customTabsIntent = new CustomTabsIntent.Builder()
.addDefaultShareMenuItem()
.setToolbarColor(this.getResources().getColor(R.color.colorPrimary))
.setShowTitle(true)
.build();

// This is optional but recommended
CustomTabsHelper.addKeepAliveExtra(this, customTabsIntent.intent);

// This is where the magic happens...
CustomTabsHelper.openCustomTab(this, customTabsIntent,
Uri.parse("...video url that u have recieved..."),
new WebViewFallback());
```

The session will now record the video of the end- customer.

#### Getting the results:

If Callback URL is provided then whole response/error in JSON format will be posted(POST METHOD) is posted to that URL.

#### Getting data:

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../videoiframes" method="post" summary="Getting Results' Data" %}
{% swagger-description %}
This method is used to get the result data from the provided Callback URL.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - Get Data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.token" type="string" %}
token received in the Unique URL Generation Request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.patronId" type="string" %}
patron ID is returned as userId parameter of login request
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
      "result": {
          "token": "jGdJgjIWpcqVUw2Vd5D6",
          "videoUrl": "..URL loaded in iframe...",
          "callbackUrl":"...callback url....",
          "isUsed": 1,
          "videoVerification": {
              "videoFaceMatch": [
              {
                  "videoImages": [
                        "...images extracted from the video... "
                    ],
                    "finalMatchImage": "matchImage used for the the video",
                    "matchStatistics": {
                        "coVariance": "..coVariance..",
                        "matchPercentage": "..average percentage match of the images.."
                    }
             }
       ],
       "audioMatch": {
           "matchAudioScore": "...audio match with the random text shown on the screen.."
       },
       //This blocks has value when more than two match Images are passed
       "matchImageFaceMatch": {
           "verified": "true/false",
           "message": "...Verification result in text..",
           "matchPercentage": "..percentage match of the images.."
       },
        "videoForensics": {
            "staticRisk": "..whether a static photo is used to record the video..",
            "prerecordedRisk": "..whether a precorded video is used to record the video..",
            "videoLandMarks": "..url of face tracked video",
            "faceLandMarks": ["..url of face demarcated image.."]
        },
        "video": "... video url ...."
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
       "task" : "getData",
       "essentials" : {
           "token":"..token received in the Unique URL Generation Request...",
           "patronId":"..patron ID is returned as userId parameter of login request..."
       }
     }
```
{% endtab %}

{% tab title="Response Parameters" %}

{% endtab %}
{% endtabs %}

#### Redirect post session

If Redirect URL is provided then the iframe redirects itself it to the Redirect URL provided once the video Verification is successfully completed and if Redirect URL is not provided it will stay in the same page.

#### Other important observations

You cannot use a single URL twice post a successful Video Verification. In case you it will redirect to an error page**("/expired")**.

#### Parameter Description

| PARAMETERS   | DESCRIPTION                                                                                                                                                                                                                                                                                                                                            | POSSIBLE VALUES         |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------- |
| TASK         | Type of Transaction performed in Signzy System.                                                                                                                                                                                                                                                                                                        | url,getData(Compulsory) |
| Patron ID    | <p>Unique ID for each Patron.</p><p>Example : Will be a alphanumeric value of 24 length such as 5a12eaf09fa3e67936b43c52</p>                                                                                                                                                                                                                           | Compulsory              |
| Token        | <p>Unique ID for each Video Verification Session Transaction.</p><p>Example : Will be a alphanumeric value of 20 length such as AfZwmorpcBp17nYZkIJY</p>                                                                                                                                                                                               | Compulsory              |
| MatchImage   | <p>The ID/Face images of the individual which is used to match with face in the video.</p><p>Example : <a href="https://persist.signzy.tech/api/files/1417647/download/VBm2fO90UZAHxRLCz4C5lItT1lhF9TinHn7EBhxJsrZlsZzBjj.jpeg">https://persist.signzy.tech/api/files/1417647/download/VBm2fO90UZAHxRLCz4C5lItT1lhF9TinHn7EBhxJsrZlsZzBjj.jpeg</a></p> | Compulsory              |
| Video Url    | The unique URL generated in response of Create URL request which should be loaded in the iframe.                                                                                                                                                                                                                                                       | Compulsory              |
| Callback URL | <p>Callback url is to post results to some other url for the particular request.</p><p>Example : <a href="https://www.w3schools.com/">https://www.w3schools.com/</a></p>                                                                                                                                                                               | Optional                |
| Redirect URL | <p>Redirection URL to redirect user post the transaction.</p><p>Example : <a href="https://signzy.com/">https://signzy.com/</a></p>                                                                                                                                                                                                                    | Optional                |

**Note:** Any field that is compulsory has to be passed or else you would get an error.

#### Error Codes

| CODE | TITLE           | DESCRIPTION                                    |
| ---- | --------------- | ---------------------------------------------- |
| 304  | No Content      | Successfully Logged Out.                       |
| 400  | Token is Used   | URL is expired.                                |
| 400  | Token not found | Invalid Token or token is found in our system. |

For other error codes please click [here](../error-codes.md)
