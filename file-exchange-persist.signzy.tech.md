# File Exchange - persist.signzy.tech

Signzy brings to customers a unique file upload system, persist.signzy.tech, which can be used to upload ID cards and documents to get a direct URL. This can be further made use by our API services as the API’s do not need to manually upload the documents, rather just attach the direct URL which can later be used for further verification.

When multiple sides or pages of an ID card are required, you need to upload each of them. For example Aadhar card has information on both sides whereas PAN has only front side containing useful information.

The URLs expire in 30 seconds by default, unless explicitly specified in the inbound request in the ttl parameter.

### Multi-part form data based file upload&#xD;

This is the basic form for accepting image based data, mostly in jpeg format:

{% swagger baseUrl="https://persist.signzy.tech/api/files/upload" path="" method="post" summary="Multi-part File Upload" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="file.protected" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.directURL" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.size" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.filetype" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.id" type="string" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file" type="object" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
      "file": {
        "id": 1388,
        "filetype": "image/jpeg",
        "size": 3181,
        "directURL": "https://persist.signzy.tech/api/files/22/download/yfhywYvErQTAbUIFwENHglQ6K31Z68s6k0HxhAash0KaAZ82ZG.jpg",
        "protected": false
      }
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
      "file": {
        "id": 1388,
        "filetype": "image/jpeg",
        "size": 3181,
        "directURL": "https://preproduction-persist.signzy.tech/api/files/22/download/yfhywYvErQTAbUIFwENHglQ6K31Z68s6k0HxhAash0KaAZ82ZG.jpg",
        "protected": false
      }
    }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME | DESCRIPTION                                                                                                           |
| -------------- | --------------------------------------------------------------------------------------------------------------------- |
| file           | This parameter contains the details about the file.                                                                   |
| file.id        | The unique file id is displayed here.                                                                                 |
| file.filetype  | The type of file being exchanged. (MIME type)                                                                         |
| file.size      | The size of the file.                                                                                                 |
| file.directURL | This contains the URL of the file location. Ex: "https://persist.signzy.tech/api/files/...id.../download/...name...". |
| file.protected | This parameter shows whether the file type is protected or not.                                                       |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/f29f2cf84f9ab161d0d3)

## Base64 based - form data file upload

### Input parameters

#### Form data should have the following parameters.

* base64string : This is mainly used to retrieve 'base64 of the file'
* mimetype: :Used to get  'mime type eg (image/jpeg)'
*   ttl: This parameter accepts the following values:(2 mins, 10 mins, 30 mins, 2 hrs, 12 hrs, 7 days, 15 days, 1 month, 3 month, 6 month, 1 year, 3 years)



{% swagger baseUrl="https://persist.signzy.tech/api/base64strings/upload" path="" method="post" summary="Base64 File Upload" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="file.protected" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.directURL" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.size" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.filetype" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.id" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
      "file": {
        "id": 1388,
        "filetype": "image/jpeg",
        "size": 3181,
        "directURL": "https://persist.signzy.tech/api/base64strings/22/download/yfhywYvErQTAbUIFwENHglQ6K31Z68s6k0HxhAash0KaAZ82ZG.jpg",
        "protected": false
      }
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
      "file": {
        "id": 1388,
        "filetype": "image/jpeg",
        "size": 3181,
        "directURL": "https://preproduction-persist.signzy.tech/api/base64strings/22/download/yfhywYvErQTAbUIFwENHglQ6K31Z68s6k0HxhAash0KaAZ82ZG.jpg",
        "protected": false
      }
    }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME | DESCRIPTION                                                                                                           |
| -------------- | --------------------------------------------------------------------------------------------------------------------- |
| file           | This parameter contains the details about the file.                                                                   |
| file.id        | The unique file id is displayed here.                                                                                 |
| file.filetype  | The type of file being exchanged. (MIME type)                                                                         |
| file.size      | The size of the file.                                                                                                 |
| file.directURL | This contains the URL of the file location. Ex: "https://persist.signzy.tech/api/files/...id.../download/...name...". |
| file.protected | This parameter shows whether the file type is protected or not.                                                       |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/f29f2cf84f9ab161d0d3)

### Base64 JSON based file upload

Input parameters

JSON POST request with the following parameters as part of input

* base64String : 'base64 of the file'
* mimetype: : 'mime type eg (image/jpeg)'
* ttl: Accepts the following values:(2 mins, 10 mins, 30 mins, 2 hrs, 12 hrs, 7 days, 15 days, 1 month, 3 month, 6 month, 1 year, 3 years)

{% swagger baseUrl="https://persist.signzy.tech/api/base64" path="" method="post" summary="JSON based upload" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="file.protected" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.directURL" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.size" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.filetype" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file.id" type="object" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="file" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
      "file": {
        "id": 1388,
        "filetype": "image/jpeg",
        "size": 3181,
        "directURL": "https://persist.signzy.tech/api/files/22/download/yfhywYvErQTAbUIFwENHglQ6K31Z68s6k0HxhAash0KaAZ82ZG.jpg",
        "protected": false
      }
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
      "file": {
        "id": 1388,
        "filetype": "image/jpeg",
        "size": 3181,
        "directURL": "https://preproduction-persist.signzy.tech/api/files/22/download/yfhywYvErQTAbUIFwENHglQ6K31Z68s6k0HxhAash0KaAZ82ZG.jpg",
        "protected": false
      }
    }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME | DESCRIPTION                                                                                                           |
| -------------- | --------------------------------------------------------------------------------------------------------------------- |
| file           | This parameter contains the details about the file.                                                                   |
| file.id        | The unique file id is displayed here.                                                                                 |
| file.filetype  | The type of file being exchanged. (MIME type)                                                                         |
| file.size      | The size of the file.                                                                                                 |
| file.directURL | This contains the URL of the file location. Ex: "https://persist.signzy.tech/api/files/...id.../download/...name...". |
| file.protected | This parameter shows whether the file type is protected or not.                                                       |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/f29f2cf84f9ab161d0d3)

****

**Help & support**

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here:&#x20;support@signzy.com



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/f29f2cf84f9ab161d0d3)
