# Search Bank by IFSC Code

The Indian Financial System Code (IFSC) is an 11 digit alphanumeric code that is uniquely assigned to banks which are part of the National Electronic Funds Transfer network. Using the IFSC code, this API can retrieve the bank details for a particular bank.&#x20;

You will need to login before sending Bank Search ifsc code based request. You are required to pass the access token received from the login call, as authorization header in the Bank Search ifsc code based request along with ifscCode.

Use the following exchange parameters for Bank Search by IFSC Code\


{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/..your-patron-id../banksearchs" method="post" summary="Search Bank By IFSC Code" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your-patron-id../banksearchs`

\




\


This method is used to search the bank by its IFSC code.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task to be performed - ifscCode
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.ifscCode" type="string" %}
IFSC code of the bank
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "result": {
      "bankName": "..bankName...",
      "address": "..address..",
      "state": "..state..",
      "district": "..district...",
      "branch": "..branch...",
      "contact": "..contact..",
      "ifscCode": "..ifscCode...",
      "micrCode": "..micrCode...",
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
    "task" : "ifscCode",
    "essentials": {
    	"ifscCode": ".....ifscCode...."
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME      | DESCRIPTION                                                                                                                                                                                                                 |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result              | This holds the final response parameters.                                                                                                                                                                                   |
| result.bankName     | This parameter displays the bank name associated with the IFSC code.                                                                                                                                                        |
| result.address      | The address of the bank for which the IFSC code is being searched.                                                                                                                                                          |
| result.state        | The state to which the bank address belongs is displayed here.                                                                                                                                                              |
| result.district     | The district in which the bank address is located is shown here.                                                                                                                                                            |
| result.branch       | The branch name of the bank for which IFSC code is being searched.                                                                                                                                                          |
| result.contact      | The bank contact information is displayed by this parameter.                                                                                                                                                                |
| result.ifscCode     | The IFSC code of the bank is shown as output.                                                                                                                                                                               |
| result.micrCode     | This parameter contains the MICR code of the bank which is assigned the IFSC code that is being searched.                                                                                                                   |
| result.splitAddress | This parameter splits and displays the various parts of the address of the bank in separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA” |
| result.addressLine  | The first line of the bank address is shown here.                                                                                                                                                                           |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/af6e8883383d19a50d15)
