# Indian ID Workflow

### The entire identity workflow consists of the following stages.:

* **Auto read** (Extraction) - This is used to extract the information from the image of the ID card.
* **Data verification** - This is done to check data consistency and authenticity.
* **Forgery check** - This is done to check data integrity and to prevent &#x20;

This document is designed to illustrate a clear idea of how the Identity APIs work.

You can use the navigation on the left to walk through each ID-card and the processes involved.

Now let us talk about the various stages of the workflow in depth:

#### Auto reading&#xD;

Auto reading is done to save users from the trouble of manually entering values each and every data field. This API reads the fields mentioned on an ID card. The API accepts image(s) of Identity cards and returns the fields it could read from them.

You could pre-fill the form fields using the auto read output and ensure that user does not have to type all the information from his card. The autofilled data can then be validated to make sure any mistakes that might have crept in from the machine reading are removed before sending it for verification.

#### Data verification&#xD;

Once the data from the ID card has been extracted, the data has to be checked for correct entries or in other words, the data needs to be validated. The verification step should be executed once the data has been validated for correctness. The input data is further checked against government and other trusted ledgers for validity of information. The API returns with true/false indicating the input information is correct.

#### Task parameters & Snoop requests

After you create an Identity object as described in the following section, you can perform the following tasks in the name of snoop requests.

* autoRecognition
* verification

### Creating an Identity card object&#xD;

The purpose of creating an identity card object is to ensure that the API can easily identify and utilise the data fields provided in the ID card before performing any auto recognition, verification or forgery check, you need to create an Identity object. All operations related to a particular ID card are executed through this object.

Creating an Identity object will require you to be logged in using the username and API-key. To know how to authenticate visit the Authentication section.

The following is a list of parameters that are supported for the creation of Identity objects:

* individualPan
* businessPan
* aadhaar
* passport
* drivingLicence
* cheque
*   VoterId



#### Creating Identity object:&#xD;

#### The following example demonstrates creation of an Identity object for verifying an 'individualPan':

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/<patron-id>/identities" method="post" summary="Identity Object" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/<patron-id>/identities`

\




\


This method allows the creation of identity object.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authentication" type="string" %}
Contains the id parameter returned from the login step
{% endswagger-parameter %}

{% swagger-parameter in="body" name="callbackURL" type="string" %}
This parameter for posting data if it is required to post the post data to some other URL for the particular request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="images" type="string" %}
Contains the URLs of the uploaded images
{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" type="string" %}
Email-Id of the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
Type of ID card 
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
              "type": "individualPan",
              "email": "admin@signzy.com",
              "callbackUrl": "https://your-domain.com/your-callback-system",
              "images": [
                "<urls-to-uploaded-files>"
              ],
              "autoRecognition": [],
              "verification": [],
              "forgeryCheck": [],
              "accessToken": "..access-token-for-the-snoop-request..",
              "id": "..itemId-for-the-snoop-request....",
              "patronId": "..your-id-into-signzy-system-(userId-returned-from-the-login-call).."
            }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
              "type": "individualPan",
              "email": "admin@signzy.com",
              "callbackUrl": "https://your-domain.com/your-callback-system",
              "images": [
                "<urls-to-uploaded-files>"
              ]
}
```
{% endtab %}

{% tab title="Response Parameter" %}
| Parameter Name  | Description                                                    |
| --------------- | -------------------------------------------------------------- |
| autoRecognition | Used for identifying the document                              |
| verification    | Used for verifying the document                                |
| accessToken     | Access token for the snoop request                             |
| id              | item id for the snoop request                                  |
| patronId        | The id for Signzy system that is returned from the login call. |
{% endtab %}
{% endtabs %}

