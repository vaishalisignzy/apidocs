# Singapore Business Details (UEN Certificate) Extraction

## UEN Certificate  <a href="#right-to-left-support" id="right-to-left-support"></a>

#### Auto-reading passport

The UEN certificate is issued to residents of Singapore and stands for Unique Entity Number(UEN). It is similar to Aadhar Number and contains the details of individuals for government records.Using Signzy’s UEN Certificate Extraction API, the details can be retrieved from both sides of the certificate as required.&#x20;

#### Logging in

You would have understood logging in by now. In case you are only integrating UEN Certificate Extraction you can understand logging in from [Authentication section.](../../)

UEN Certificate Extraction reading system accepts direct URL of the UEN Certificate.



## Input Parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
|            |             |
| ---------- | ----------- |
| Parameters | Description |
|            |             |
|            |             |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl --request POST \
  --url https://signzy.tech/api/v2/patrons/....patronid.../foreignidentitiesextractions \
  --header 'accept: */*' \
  --header 'accept-language: en-US,en;q=0.8' \
  --header 'authorization: <Access-Token>' \
  --header 'content-type: application/json' \
  --data '{"task":"uenExtraction","essentials":{"files":["...files.."]}}'
```


{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
|            |             |
| ---------- | ----------- |
| Parameters | Description |
|            |             |
|            |             |


{% endtab %}

{% tab title="Sample API Response" %}
```
```


{% endtab %}
{% endtabs %}



{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../foreignidentitiesextractions" method="post" summary="UEN Certificate Extraction" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..patronID../foreignidentitiesextractions`

\




\


This method is used to extract the details of a UEN Certificate of Singapore.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorisation" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - UEN Extraction
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the image urls of the UEN Certificate
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.files" type="object" %}
Contains the URLs of the image files
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
        "essentials": {
            "files": ["...image url..."]
        },
        "id": "...id...",
        "patronId": "...patron id...",
        "task": "uenExtraction",
        "result": {
            "entityName": "...entityName...",
            "uen": "...uen..."
        }
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {

     "task" : "uenExtraction",
     "essentials": {
      "files": ["..files.."]
     }
    }

```
{% endtab %}

{% tab title="Response Parameters" %}
| **PARAMETER  NAME** | **DESCRIPTION**                                                           |
| ------------------- | ------------------------------------------------------------------------- |
| essentials          | Contains the essential input data.                                        |
| essentials.files    | Contains the image URL of the file/files uploaded.                        |
| essentials.id       | This parameter contains the unique Id received from the identity request. |
| essentials.patronId | This parameter returns the unique ID of the UEN holder.                   |
| essentials.task     | The type of task to be performed - UEN Extraction.                        |
| result              | This holds final result parameters of the response.&#xD;                  |
| result.entityName   | The name of the identity - UEN.                                           |
| result.uen          | The UEN number that is assigned.                                          |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/025bfb068d3dd8e8bfa2)
