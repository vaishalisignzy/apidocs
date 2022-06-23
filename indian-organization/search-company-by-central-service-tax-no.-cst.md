# Search Company by Central Service Tax No. (CST)(Obsolete)

The Central Service Tax was a tax that was levied by the Central Government of India on the services provided by service providers. This indirect tax came into being under the Finance Act, 1994. Using the unique 15-digit CST number that is issued to the business owner/service provider, the Search By Central Service Tax API can retrieve the detail of the individual/organisation to whom the Central Service Tax number has been issued.

You will need to login before sending Central Service Tax request. You are required to pass the access token received from the login call, as authorization header in the Central Service TAX request along with assesseeCode.

Use the following exchange parameters for Central Service Tax based search

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../cservicetaxs" method="post" summary="Search by Company CST Number" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../cservicetaxs`

\




\


This method is used to search for organization details using Company CST Number.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token (returned as id field of login request)
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.assesseeCode" type="string" %}
The assessee Code that is to be searched.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
    "essentials": {
      "assesseeCode": "...assesseeCode..."
    },
    "id": "...accessToken...",
    "patronId": "...patronId...",
    "result": {
      "divisionCode": "...divisionCode...",
      "nameOfAssessee": "...nameOfAssessee...",
      "status": "....status...",
      "locationCode": "...location...",
      "addressOfAssessee": "...address....",
      "assesseeBelongsTo": "SERVICE TAX",
      "commissionerateCode": ".....commissionerate code...",
      "rangeCode": "...range code....",
      "splitAddress": {
        "state": [
          []
        ],
        "district": [],
        "city": [],
        "pincode": "...pincode...",
        "country": [
          "IN",
          "IND",
          "INDIA"
        ],
        "addressLine": "...addressLine..."
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
    "essentials": {
    	"assesseeCode": ".....assesseecode...."
    }
  }

```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME             | DESCRIPTION                                                                                                                                                                                                                   |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| essentials                 | This parameter contains the essential data for output.                                                                                                                                                                        |
| essentials.assesseeCode    | The assessee code that is being searched.                                                                                                                                                                                     |
| id                         | This contains the access token received during login request.                                                                                                                                                                 |
| patronId                   | This parameter is returned as userId parameter of login request.                                                                                                                                                              |
| result                     | This contains the final response parameters to be displayed.                                                                                                                                                                  |
| result.divisionCode        | The code that designates the divisional area where the assessee belongs to.                                                                                                                                                   |
| result.nameOfAssessee      | The name of the assessee is displayed by this parameter.                                                                                                                                                                      |
| result.status              | The current status of the assessee is displayed here.                                                                                                                                                                         |
| result.locationCode        | The location code, if any, designates the location to which the assessee belongs to.                                                                                                                                          |
| result.addressOfAssessee   | The address of the assessee is shown by this parameter.                                                                                                                                                                       |
| result.assesseeBelongsTo   | This category determines the tax category to which the assessee belongs to. In this case it is SERVICE TAX.                                                                                                                   |
| result.commissionerateCode | The Commisionerate Code for the particular assessee is displayed here.                                                                                                                                                        |
| result.rangeCode           | The range code to which the assessee belongs to.                                                                                                                                                                              |
| result.splitAddress        | This parameter distinguishes the various parts of the address of the assessee into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine   | The first line of the address is displayed here.                                                                                                                                                                              |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/131f713f8cba73232da2)
