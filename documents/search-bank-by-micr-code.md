# Search Bank by MICR Code

Magnetic ink character recognition code, known in short as MICR code, is a character recognition technology used mainly by the banking industry to streamline the processing and clearance of cheques and other documents. MICR encoding, called the MICR line, is at the bottom of cheques and other vouchers and typically includes the document-type indicator, bank code, bank account number, cheque number, cheque amount (usually added after a cheque is presented for payment), and a control indicator.&#x20;

Signzy has designed this unique API for Bank Search by MICR Code, that allows the system to read the MICR code of the uploaded document and identify which bank is the issuing authority along with other details like Address, IFSC code etc

You will need to login before sending Bank Search micr code based request. You are required to pass the access token received from the login call, as authorization header in the Bank Search micr code based request along with micrCode.

Use the following exchange parameters for Bank Search by MICR Code\


{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/..your-patron-id../banksearchs" method="post" summary="Search Bank By MICR Code" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your-patron-id../banksearchs`

\




\


This method is used to search the bank by its MICR code.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task to be performed - micrCode
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.micrCode" type="string" %}
MICR code of the bank
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
    "task" : "micrCode",
    "essentials": {
    	"micrCode": ".....micrCode...."
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| **PARAMETER NAME**  | **DESCRIPTION**                                                                                                                                                                                                             |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result              | This holds the final response parameters.                                                                                                                                                                                   |
| result.bankName     | This parameter displays the bank name associated with the MICR code.                                                                                                                                                        |
| result.address      | The address of the bank for which the MICR code is being searched.                                                                                                                                                          |
| result.state        | The state to which the bank address belongs is displayed here.                                                                                                                                                              |
| result.district     | The district in which the bank address is located is shown here.                                                                                                                                                            |
| result.branch       | The branch name of the bank for which MICR code is being searched.                                                                                                                                                          |
| result.contact      | The bank contact information is displayed by this parameter.                                                                                                                                                                |
| result.ifscCode     | The IFSC code of the bank is shown which is assigned to the MICR code that is being searched.                                                                                                                               |
| result.micrCode     | This parameter contains the MICR code of the bank                                                                                                                                                                           |
| result.splitAddress | This parameter splits and displays the various parts of the address of the bank in separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA” |
| result.addressLine  | The first line of the bank address is shown here.                                                                                                                                                                           |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/c06412e5384f7a806335)
