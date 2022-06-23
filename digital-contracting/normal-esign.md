# Normal ESign

Unlike SIgnzy’s ESIGN 2.0, the Normal Esign API service follows the conventional method of signing each and every document one at a time. This is mainly useful for documents like tax return forms or aadhar card, where electronic signature is required for authenticity of the document.

#### Create URL

Once customer get logged in, he/she can create the url for Signzy ESIGN platform.

### Normal Esign Details:

* For Normal ESIGN without adhaar please select one of the undermentioned options for Signing the document.
  * Upload Signature
  * Font based Signature
  * Draw Signature
* Once the Signature is done then the signzy API will confirm that your ESIGN Transaction is successful.
* If the Callback URL is provided then whole response in JSON format will be posted(POST REQUEST) is posted to that URL.
* If Redirect URL is provided then once response is posted in Callback URL the iframe redirects itself it to the Redirect URL provided.

{% swagger baseUrl="https://esign.signzy.tech" path="/api/customers/..customerid../aadhaaresigns" method="post" summary="Normal E-Sign" %}
{% swagger-description %}
This method is used for Normal E-Sign of a document.
{% endswagger-description %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - URL
{% endswagger-parameter %}

{% swagger-parameter in="body" name="callbackUrl" type="string" %}
Callback url for posting data if it is required to post the post data to some other url for the particular request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="redirectUrl" type="string" %}
Redirection URL is for redirecting the application to the provided URL once the ESIGN transaction is over.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="uid" type="string" %}
Aadhaar Number
{% endswagger-parameter %}

{% swagger-parameter in="body" name="inputFile" type="string" %}
File which has to be signed.File size should be less than 5mb.	
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" %}
Name of person signing the document
{% endswagger-parameter %}

{% swagger-parameter in="body" name="multiPages" type="string" %}
If False signature while appear on a single page if pageNo parameter is not set if True then signature on all Pages
{% endswagger-parameter %}

{% swagger-parameter in="body" name="signaturePosition" type="string" %}
Position where signature is required
{% endswagger-parameter %}

{% swagger-parameter in="body" name="pageNo" type="string" %}
PageNo where signature only valid when multipages is false	
{% endswagger-parameter %}

{% swagger-parameter in="body" name="signatureType" type="string" %}
aadhaaresign for adhaar esignature Esign for normal esign where you can either draw ot upload or select font for esignature
{% endswagger-parameter %}

{% swagger-parameter in="body" name="xCoordinate" type="string" %}
xCoordinate where signature block should start
{% endswagger-parameter %}

{% swagger-parameter in="body" name="yCoordinate" type="string" %}
yCoordinate where signature block should start
{% endswagger-parameter %}

{% swagger-parameter in="body" name="height" type="string" %}
Height of signature block
{% endswagger-parameter %}

{% swagger-parameter in="body" name="width" type="string" %}
Width of signature block
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
             "result": {
              "token": "..token...",
              "isUsed": 0,
              "url": "https://esign-preproduction.signzy.tech/customer/59bbeb8dd3ad01181faa58da/token/GfQnm5aTldf5RDnN8zUf",
              "uid": "..uid..",
              "inputFile": "https://persist.signzy.tech/api/files/714754/download/hu2OYX7YWtn1oq5OAbVhK2LpbWhVayKaGnU9wTTche5Yu2dKiB.pdf",
              "redirectUrl": "http://preproduction.signzy.tech",
              "redirectTime":"Time in which it will redirect to the redirectUrl"
              "callbackUrl": "http://development.signzy.tech",
              "signatureType": "esign",
              "name": "..name..",
              "selectPage": "ALL",
              "signaturePosition": "Customize",
              "pageNo": "5",
              "xCoordinate": "10",
              "yCoordinate": "10",
              "width": "150",
              "height": "250"
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
       "callbackUrl" : "http://development.signzy.tech",
       "redirectUrl" : "http://preproduction.signzy.tech",
       "uid" : "..uid...",
       "inputFile" : "https://persist.signzy.tech/api/files/714754/download/hu2OYX7YWtn1oq5OAbVhK2LpbWhVayKaGnU9wTTche5Yu2dKiB.pdf",
       "name" : "name",
       "multiPages" : "true",
       "signaturePosition" : "Customize",
       "pageNo" : "5",
       "signatureType" : "esign",
       "xCoordinate" : "10",
       "yCoordinate" : "10",
       "height" : "250",
       "width" : "150"
      }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETERS        | DESCRIPTION                                                                                                                                                                                                                                                |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| TASK              | Type of Transaction performed in Signzy System                                                                                                                                                                                                             |
| Customer ID       | Unique ID for each Customer                                                                                                                                                                                                                                |
| Token             | Unique ID for each transaction                                                                                                                                                                                                                             |
| UID               | Aadhaar Number                                                                                                                                                                                                                                             |
| Callback URL      | Callback url for posting data if it is required to post the post data to some other url for the particular request                                                                                                                                         |
| Redirect URL      | Redirection URL is for redirecting the application to the provided URL once the transaction is over.                                                                                                                                                       |
| InputFile         | File which has to be signed.File size should be less than **5mb**.                                                                                                                                                                                         |
| Name              | Name of person signing the document                                                                                                                                                                                                                        |
| MultiPages        | If False signature while appear on a single page if pageNo parameter is not set if True then signature on all Pages                                                                                                                                        |
| signaturePosition | <p>Position where signature is required</p><ol><li>TOP-LEFT</li><li>TOP-CENTER</li><li>TOP-RIGHT</li><li>MIDDLE-LEFT</li><li>MIDDLE-CENTER</li><li>MIDDLE-RIGHT</li><li>BOTTOM-LEFT</li><li>BOTTOM-CENTER</li><li>BOTTOM-RIGHT</li><li>CUSTOMIZE</li></ol> |
| signatureType     | <p> For normal sign, you can either draw or upload or select font for esignature</p><ol><li>aadhaaresign</li><li>esign</li></ol>                                                                                                                           |
| pageNo            | PageNo where signature only valid when multipages is false                                                                                                                                                                                                 |
| xCoordinate       | xCoordinate where signature block should start                                                                                                                                                                                                             |
| yCoordinate       | yCoordinate where signature block should start                                                                                                                                                                                                             |
| height            | Height of signature block                                                                                                                                                                                                                                  |
| width             | Width of signature block                                                                                                                                                                                                                                   |
{% endtab %}
{% endtabs %}



* After getting the verification url, put the url in web browser tab and enter. It will navigate to the signzy page where below page will display.
* While creating the URL if document to be signed URL is not passed and signer name is not passed then enter the details in the window.
* After this clicking on the Confirm button it will navigate to the ESP page. Displayed as below and select the type of signature to be done on the document.

{% swagger baseUrl="https://esign.signzy.tech" path="/api/callbacks" method="post" summary="Getting Data" %}
{% swagger-description %}
This method is used to get the data of the esign request
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token (returned as id field of login request)
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task - getData
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.token" type="string" %}
token received in the Unique URL Generation Request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.patronId" type="string" %}
patron ID is returned as userId parameter of login request
{% endswagger-parameter %}

{% swagger-response status="200" description=" {" %}
```
 {
          "customerId": ".customerId...",
          "token": ".token..",
          "id": 4,
          "result": {
              "token": ".token..",
              "isUsed": 1,
              "url": "https://esign-preproduction.signzy.tech/customer/59bbeb8dd3ad01181faa58da/token/cDZmciLrym0gwCsnKDlL",
              "uid": "..uid..",
              "inputFile": "https://persist.signzy.tech/api/files/714754/download/hu2OYX7YWtn1oq5OAbVhK2LpbWhVayKaGnU9wTTche5Yu2dKiB.pdf",
              "redirectUrl": "https://preproduction.signzy.tech",
              "callbackUrl": "http://development.signzy.tech",
              "signatureType": "esign",
              "name": "..name..",
              "selectPage": "ALL",
              "signaturePosition": "Customize",
              "pageNo": "5",
              "xCoordinate": "10",
              "yCoordinate": "10",
              "width": "150",
              "height": "250",
              "esignedFile": "https://preproduction-persist.signzy.tech/api/base64strings/57/download/nCs44JxBDDd2Xd5kwBIqkumdKdxWCYFBkxyu7w2XuxjPLs6kAn.pdf"
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

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/8958e842c3a5607b783a)
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETERS        | DESCRIPTION                                                                                                                                                                                                                                                |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| TASK              | Type of Transaction performed in Signzy System                                                                                                                                                                                                             |
| Customer ID       | Unique ID for each Customer                                                                                                                                                                                                                                |
| Token             | Unique ID for each transaction                                                                                                                                                                                                                             |
| UID               | Aadhaar Number                                                                                                                                                                                                                                             |
| Callback URL      | Callback url for posting data if it is required to post the post data to some other url for the particular request                                                                                                                                         |
| Redirect URL      | Redirection URL is for redirecting the application to the provided URL once the transaction is over.                                                                                                                                                       |
| InputFile         | File which has to be signed.File size should be less than **5mb**.                                                                                                                                                                                         |
| Name              | Name of person signing the document                                                                                                                                                                                                                        |
| MultiPages        | If False signature while appear on a single page if pageNo parameter is not set if True then signature on all Pages                                                                                                                                        |
| signaturePosition | <p>Position where signature is required</p><ol><li>TOP-LEFT</li><li>TOP-CENTER</li><li>TOP-RIGHT</li><li>MIDDLE-LEFT</li><li>MIDDLE-CENTER</li><li>MIDDLE-RIGHT</li><li>BOTTOM-LEFT</li><li>BOTTOM-CENTER</li><li>BOTTOM-RIGHT</li><li>CUSTOMIZE</li></ol> |
| signatureType     | <p> For normal sign, you can either draw or upload or select font for esignature</p><ol><li>aadhaaresign</li><li>esign</li></ol>                                                                                                                           |
| pageNo            | PageNo where signature only valid when multipages is false                                                                                                                                                                                                 |
| xCoordinate       | xCoordinate where signature block should start                                                                                                                                                                                                             |
| yCoordinate       | yCoordinate where signature block should start                                                                                                                                                                                                             |
| height            | Height of signature block                                                                                                                                                                                                                                  |
| width             | Width of signature block                                                                                                                                                                                                                                   |
{% endtab %}
{% endtabs %}
