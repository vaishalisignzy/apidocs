# Singapore UEN Extraction and Fetch

### Auto-reading Singapore UEN

The UEN Certificate Extraction and Fetch is basically a combination API that integrates the salient features of UEN extraction as well as UEN Fetch. Using Signzy’s proprietary algorithms, the UEN certificate details can be retrieved with high precision using this service.

#### Logging in

You would have understood logging in by now. In case you are only integrating UEN Certificate Extraction and Fetch you can understand logging in from [Authentication section.](../../)

UEN Certificate Extraction reading system accepts direct URL of the UEN Certificate.

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../foreignidentitiesextractions" method="post" summary="UEN Certificate Extraction and Fetch" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your patron id../foreignidentitiesextractions`

\




\


This method is used to fetch and extract the details of a UEN Certificate of Singapore.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorisation" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - uenExtractionAndFetch
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the image urls of the UEN Certificate
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.files" type="object" %}
Contains the URLs of the image files
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 "result": {
        "uen": "...uen...",
        "issuanceAgencyId": "...issuanceAgencyId...",
        "uenStatus": "...uenStatus...",
        "entityName": "...entityName...",
        "entityType": "...entityType...",
        "uenIssueDate": "...uenIssueDate...",
        "regStreetName": "...regStreetName...",
        "regPostalCode": "...regPostalCode..."
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{

     "task" : "uenExtractionAndFetch",
     "essentials": {
      "files": ["..files.."]
     }
    }
```
{% endtab %}

{% tab title="Response Parameters" %}
| **PARAMETER NAME**      | **DESCRIPTION**                                                         |
| ----------------------- | ----------------------------------------------------------------------- |
| result                  | This holds the final result parameters of the response.                 |
| result.uen              | The unique UEN ID.                                                      |
| result.issuanceAgencyId | The unique ID of the agency that has issued the UEN for the individual. |
| result.uenStatus        | This parameter returns the current status of the UEN.                   |
| result.entityName       | This parameter returns the mane of the entity.                          |
| result.entityType       | This parameter returns the type of the UEN entity.                      |
| result.uenIssueDate     | This parameter contains the date of issue for the UEN.                  |
| result.regStreetName    | The street name that has been registered with the UEN.                  |
| result.regPostalCode    | The postal code that has been registered with the UEN.                  |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/4aebf0535ad974d89cc7)

\
