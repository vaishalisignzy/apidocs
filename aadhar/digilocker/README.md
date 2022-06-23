# DigiLocker (D)

## Digilocker Workflow <a href="#right-to-left-support" id="right-to-left-support"></a>

DigiLocker Iframe is the portal wherein User enters his digilocker credentials and gives to one of many issued documents to the client.

Signzy is providing an Digilocker iframe where user enters the digilocker credentials and gives the access of the file to the client.

### Integration Flow

#### Logging in

You would have understood logging in by now. In case you are only integrating Aadhaar Auth you can understand logging in from [Authentication section.](https://docs-staging.signzy.tech/)

#### Create DigiLocker URL

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/..your-patron-id../digilockers" method="post" summary="Create DigilockerURL" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your-patron-id../digilockers`

\




\


In this method, a DigiLocker URL is created.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorisation" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="callbackUrl" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="redirectURL" type="object" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
         "result": {
             "token": "..token..",
             "digilockerUrl": "..URL to be loaded in iframe..."
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
          "redirectUrl" : "..redirectUrl..",
          "callbackUrl" : "...callbackUrl..."
      }
    }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME       | DESCRIPTION                                                         |
| -------------------- | ------------------------------------------------------------------- |
| result               | This contains the final response parameters.                        |
| result.token         | This parameter contains the identity access token.                  |
| result.digilockerUrl | This parameter contains the URL that is to be loaded in the iframe. |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/b379dcb712423f4d5d78)

#### Load Digilocker Url

Once you receive the Digilocker Url.

* Open the url in a web browser.
* In case of web app product, load the URL in the iframe
* In case of mobile APP, load the URL in the webview and you need to enable local storage in our APP. For Android you can use this [link](https://stackoverflow.com/questions/5899087/android-webview-localstorage) to enable it.
* Once url is loaded into the browser a web iframe will open and where you have to hit the Fetch from DigiLocker button
* One more popup will open where you have to enter your digilocker credentials and give consent that signzy can download the file on client behalf
* Select the issued document which you want to share and click on share
* Once the file is successfully shared the popup closes and signzy receives the file and shares it with the client.

#### Getting the results:

If Callback URL is provided then whole response/error in JSON format will be posted(POST METHOD) to that URL.

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/..your-patron-id../digilockers" method="post" summary="Getting Data" %}
{% swagger-description %}
In this method, a DigiLocker URL is created.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorisation" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - getData
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the token and patron ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.token" type="object" %}
token received in the Unique URL Generation Request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.patronID" type="object" %}
patron ID is returned as userId parameter of login request
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
"result": {
          "token": "..token..",
          "webUrl": "..webUrl..",
          "isUsed": 1,
          "file": {
            "fileName": "..fileName...",
            "source": "..source..",
            "txn": ..txn..,
            "sharedTill": "..sharedTill..",
            "contentType": "..contentType..",
            "docType": "..docType..",
            "docId": "..docId..",
            "url": "..url.."
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
| PARAMETER NAME   | DESCRIPTION                                                     |
| ---------------- | --------------------------------------------------------------- |
| result           | The final response parameters are contained here.               |
| result.token     | Unique ID for each Video Verification Session Transaction.      |
| result.webUrl    | The webUrl from which Digilocker data is taken.                 |
| result.isUsed    | Whether the file is being used.                                 |
| result.file      | The file details which is being uploaded for Digilocker.        |
| file.filename    | The name of the file.                                           |
| file.txn         | The DigiLocker transaction ID.                                  |
| file.source      | The source of the file is displayed here.                       |
| file.sharedTill  | The time till which file is accessible.                         |
| file.contentType | The content type of the file.                                   |
| file.docType     | If the file is a document, the document type is displayed here. |
| file.docId       | If the file is a document, the document ID is displayed here.   |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/b379dcb712423f4d5d78)

#### Redirect post session

If Redirect URL is provided then the iframe redirects itself it to the Redirect URL once the Aadhaar Auth is successfully completed and if Redirect URL is not provided it will stay in the same page.

#### Other important observations

You cannot use a single URL twice post a successful Aadhaar Authentication. In case you use it, it will redirect to an error page**("/error.html")**.

#### Parameter Description

| PARAMETERS     | DESCRIPTION                                                                                                                                                              | POSSIBLE VALUES         |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------- |
| TASK           | Type of Transaction performed in Signzy System.                                                                                                                          | url,getData(Compulsory) |
| Patron ID      | <p>Unique ID for each Patron.</p><p>Example : Will be a alphanumeric value of 24 length such as 5a12eaf09fa3e67936b43c52</p>                                             | Compulsory              |
| Token          | <p>Unique ID for each Video Verification Session Transaction.</p><p>Example : Will be a alphanumeric value of 20 length such as AfZwmorpcBp17nYZkIJY</p>                 | Compulsory              |
| Digilocker Url | The unique URL generated in response of Create URL request which should be loaded in the iframe.                                                                         | Compulsory              |
| Callback URL   | <p>Callback url is to post results to some other url for the particular request.</p><p>Example : <a href="https://www.w3schools.com/">https://www.w3schools.com/</a></p> | Optional                |
| Redirect URL   | <p>Redirection URL to redirect user post the transaction.</p><p>Example : <a href="https://signzy.com/">https://signzy.com/</a></p>                                      | Optional                |

**Note:** Any field that is compulsory has to be passed or else you would get an error.

#### Error Codes

| CODE | TITLE           | DESCRIPTION                                    |
| ---- | --------------- | ---------------------------------------------- |
| 304  | No Content      | Sucessfully Logged Out.                        |
| 400  | Token is Used   | URL is expired.                                |
| 400  | Token not found | Invalid Token or token is found in our system. |

For other error codes please [click here](../../error-codes.md)
