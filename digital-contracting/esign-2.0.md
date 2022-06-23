# ESIGN 2.0

The ESIGN 2.0 is an innovative product by Signzy that allows multiple pdf documents to be uploaded into the API wherein the user can upload his/her signature for easily signing multiple documents. The API service provides a simple yet secure solution for users who wish to have multiple documents signed electronically without the hassle of multiple entry by opening each document separately.

#### File exchange - persist.signzy.tech

You first need to upload the required pdfs before sending for signature. Use the file upload system, persist.signzy.tech, to upload each document and get a direct Url to each

### Authentication

#### Authorizing your access

If you are seeing this page, you already have a username and an API key. The key also acts like your password to the APIs. You need to have an access token for making any further API calls, which you can receive by logging in manually or programmatically using these credentials.

Signzy APIs adhere to authentication defined by Swagger 2.0 specifications. Each call to the APIs should include an 'Authorization' header or 'access\_token' query parameter for authentication.

You can find working examples at the bottom of this page.

#### Logging in

Logging in into the API service password requires a simple HTTP call. Following section mentions data to be input, expected output and meaning of fields.

{% swagger baseUrl="https://esign.signzy.tech" path="/api/customers/login" method="post" summary="Log In" %}
{% swagger-description %}
This method allows authentication during login.
{% endswagger-description %}

{% swagger-parameter in="body" name="username" type="string" %}
The username for the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" type="string" %}
The password for the user
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
      "id": "...id...",
      "ttl": 1209600,
      "created": "2017-06-23T11:10:08.534Z",
      "userId": "..userId..."
    }

```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
      "username": "enter your valid username",
      "password": "enter your valid password"
    }
```
{% endtab %}

{% tab title="Response Parameters" %}

{% endtab %}
{% endtabs %}

#### Sending authenticated requests

Once you have an access token from the login API call, you can send further calls to different endpoints by passing the access-token in Authorization header or in access\_token query (GET) parameter.

It is advisable to send Access Token in header since, query parameters are sometimes saved in the log files thereby exposing vulnerabilities until the access\_token is deleted from sessions.

#### Security

Anybody with your API key/password or an Access Token generated using them can access all information you have created and also send requests on behalf of you.. It is strongly recommended to not send API-key/Password to client side and instead use reverse proxy to call Signzy APIs.

If case you think an access token is compromised, you should delete it using logout. Let us know if your Signzy Password/API-key is compromised as soon as possible, so that we can disable & create new ones and prevent any misuse of your data.

#### Logging out

To logout you simply need to call the logout route with the access token in 'access\_token' query parameter or as 'Authorization' header.

```
// Logout
      // Data exchange
      For Test Credentials
      // POST :: https://esign-preproduction.signzy.tech/api/customers/logout?access_token=...accessToken...
      For Production Credentials
      // POST :: https://esign.signzy.tech/api/customers/logout?access_token=...accessToken...
      // Response is 204 status code with no content, indicating the Access-token has been deleted.

```



#### Digital Signature Customizations:

| PARAMETERS        | DESCRIPTION                                                                                                                                                                                                                                                | POSSIBLE VALUES                                                             |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| TASK              | Type of Transaction performed in Signzy System                                                                                                                                                                                                             | url(Compulsory)                                                             |
| Customer ID       | Unique ID for each Customer                                                                                                                                                                                                                                | Compulsory                                                                  |
| Token             | Unique ID for each ESIGN Transaction                                                                                                                                                                                                                       | Compulsory                                                                  |
| UID               | Aadhaar Number                                                                                                                                                                                                                                             | Optional(only required for aadhaaresign)                                    |
| Callback URL      | Callback url for posting data if it is required to post the post data to some other url for the particular request                                                                                                                                         | Optional                                                                    |
| Redirect URL      | Redirection URL is for redirecting the application to the provided URL once the ESIGN transaction is over.                                                                                                                                                 | Optional                                                                    |
| InputFile         | File which has to be signed.File size should be less than 5 **Mb**.                                                                                                                                                                                        | Compulsory(either while creating the URL) or upload the file on the portal. |
| Name              | Name of person signing the document                                                                                                                                                                                                                        | Compulsory(either while creating the URL) or upload the file on the portal  |
| MultiPages        | If False signature while appear on a single page if pageNo parameter is not set if True then signature on all Pages                                                                                                                                        | Optional(Default True)                                                      |
| signaturePosition | <p>Position where signature is required</p><ol><li>TOP-LEFT</li><li>TOP-CENTER</li><li>TOP-RIGHT</li><li>MIDDLE-LEFT</li><li>MIDDLE-CENTER</li><li>MIDDLE-RIGHT</li><li>BOTTOM-LEFT</li><li>BOTTOM-CENTER</li><li>BOTTOM-RIGHT</li><li>CUSTOMIZE</li></ol> | Optional(Default BOTTOM-RIGHT)                                              |
| signatureType     | <p>aadhaaresign for adhaar esignature Esign for normal esign where you can either draw ot upload or select font for esignature</p><ol><li>aadhaaresign</li><li>esign</li></ol>                                                                             | Optional(aadhaaresign default)                                              |
| pageNo            | PageNo where signature only valid when multipages is false                                                                                                                                                                                                 | Optional(last page)                                                         |
| xCoordinate       | xCoordinate where signature block should start                                                                                                                                                                                                             | Optional                                                                    |
| yCoordinate       | yCoordinate where signature block should start                                                                                                                                                                                                             | Optional                                                                    |
| height            | Height of signature block                                                                                                                                                                                                                                  | Optional                                                                    |
| width             | Width of signature block                                                                                                                                                                                                                                   | Optional                                                                    |

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/c5b32f7827efc08a8ee8)
