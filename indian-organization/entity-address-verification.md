# Entity Address Verification(404)

This is a more generic search-based API which is used when no other valid address proof is available. The API takes user input in the form of Name and registered address for verification.

You will need to [login](https://docs-staging.signzy.tech/) before sending request. You are required to pass the access token received from the login call, as authorization header.

Use the following exchange parameters for Active Address Verification

\


{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/..your-patron-id../activeaddresses" method="post" summary="Search Entity Address Verification" %}
{% swagger-description %}
Production URL:

\




`https://signzy.tech/api/v2/patrons/..your-patron-id../activeaddresses`

\




\


This method is used to verify address details of an individual or organization.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.name" type="object" %}
Name of the individual
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.registeredAddress" type="string" %}
Registered Address of the individual
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
      "essentials": {
        "name": "....name...",
        "registeredAddress": ".....registeredAddress....."
      },
      "id": "....randomId.....",
      "patronId": "....patronid.....",
      "result": {
       "googleAddress": ["...googleAddress..."]
       "registeredAddress": "...registeredAddress...",
  		 "match": {
  			"google": [{
  				"addressDiffInKm": "...addressDiffInKm...",
  				"pinMatchResult": "...pinMatchResult..."
  			}]
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
      "name": "...name...",
      "registeredAddress": ".....registeredAddress....."
      }
    }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME           | DESCRIPTION                                                                                  |
| ------------------------ | -------------------------------------------------------------------------------------------- |
| id                       | This parameter displays the random Id received during login request                          |
| patronId                 | This is returned as userId parameter of login request                                        |
| result                   | This contains the final response parameters.                                                 |
| result.googleAddress     | This parameter shows the address of the entity as can be seen from Google search.            |
| result.registeredAddress | This parameter contains the registered address of the entity.                                |
| result.match             | This parameter determines the match result and shows the details of the matching addresses.  |
| result.google            | The distance difference (if any) and the pincode match results are shown in this parameter.  |
| google.addressDiffInKm   | The difference in kilometres between the Google address and the registered address (if any). |
| google.pinMatchResult    | The parameter displays the result of matching picodes between the two addresses.             |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/c288dfaa3a5f08557b25)\


\
