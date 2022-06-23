# Search by CST Number(obsolete)

CST (Central Sales Tax) ) is a form of indirect tax imposed only on goods sold from one state to another state, which particularly takes into account that the buyer and the seller needs to be in two different states. The CST number is a unique 11 digit number that is issued to the business/dealer that registers for CST

The Search by CST API by Signzy is used to retrieve the details of the particular business owner or dealer who is registered for the CST.&#x20;

You will need to login before sending CST Number request. You are required to pass the access token received from the login call, as authorization header in the CST request along with cstNumber.



Use the following exchange parameters for CST based search

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../csts" method="post" summary="Search by CST Number" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your-patron-id../csts`

\




\


This method is used to search for business details using CST Number.
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

{% swagger-parameter in="body" name="essentials.cstNumber" type="string" %}
The CST number to be searched
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
    "essentials": {
      "cstNumber": "...cstNumber..."
    },
    "id": "...accessToken...",
    "patronId": "...patronId...",
    "result": {
             "cstStatus": "...cstStatus...",
             "pan": "...pan...",
             "status": "...status...",
             "ownerName": "...ownerName...",
             "dealer": "...dealer...",
             "address": "...address...",
             "regDate": "...regDate...",
             "cancelDate": "...cancelDate...",
             "splitAddress": {
                 "district": [
                     "...district..."
                 ],
                 "state": [
                     [
                         "...state..."
                     ]
                 ],
                 "city": [
                     "...city..."
                 ],
                 "pincode": "...pincode...",
                 "country": [
                     "IN",
                     "IND",
                     "INDIA"
                 ],
                 "addressLine": "...addressLine...",
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
    	"cstNumber": ".....company's-cst-to-search-for...."
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| **PARAMETER NAME**       | **DESCRIPTION**                                                                                                                                                                                                                          |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| essentials               | This parameter contains the essential output data.                                                                                                                                                                                       |
| essentials.cstNumber     | The CST number that is being searched.                                                                                                                                                                                                   |
| id                       | This parameter contains the access token received during login request.                                                                                                                                                                  |
| patronId                 | This parameter is returned as userId parameter of login request.                                                                                                                                                                         |
| result                   | This contains the final response parameters to be displayed.                                                                                                                                                                             |
| result.cstStatus         | The central sales tax status for the CST number.                                                                                                                                                                                         |
| result.pan               | The PAN number of the CST holder.                                                                                                                                                                                                        |
| result.status            | The status of the CST is displayed here.                                                                                                                                                                                                 |
| result.ownerName         | The CST holder name is displayed here.                                                                                                                                                                                                   |
| result.dealer            | The dealer name associated with the CST.                                                                                                                                                                                                 |
| result.address           | The address of the business associated with the CST is displayed here.                                                                                                                                                                   |
| result.regDate           | The registration date of the business associated with the CST is displayed by this parameter.                                                                                                                                            |
| result.cancelDate        | The cancellation date for the CST is mentioned here.                                                                                                                                                                                     |
| result.splitAddress      | This parameter distinguishes the various parts of the address of the TIN holder's business into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA” |
| splitAddress.addressLine | This parameter contains the first line of the address.                                                                                                                                                                                   |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/131f713f8cba73232da2)
