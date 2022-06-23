# Bank Cancelled Cheque Data Extraction

### Auto-reading cheque

Cancelled Cheques are often used by many banks and other financial institutions as a proof of account and it may be necessary for the same by certain organisations to extract the details of a cancelled cheque that is provided by the user. This unique API makes use of Signzy’s unique extraction algorithm to retrieve the details from the image or image URL provided by the user.

Before going for Auto reading, you first need to create an Identity object.Please make sure the image you use fits tightly in camera view and is horizontally-aligned. Each image/pdf should be less than 2MB.

Cancelled cheque auto-reading system accepts direct URL of the image.

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/snoops" method="post" summary="Cancelled Cheque Extraction" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/snoops`

\




\


This method allows the cancelled cheque details to be extracted.
{% endswagger-description %}

{% swagger-parameter in="body" name="service" type="string" %}
type - identity 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="itemID" type="object" %}
identity Item ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - Auto Recognition
{% endswagger-parameter %}

{% swagger-parameter in="body" name="accessToken" type="object" %}
Identity access token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the URL of the cancelled cheque from which data has to be extracted
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {

  	"result": {
  		"address": "...address...",
  		"ifsc": "...ifsc...",
  		"pincode": "...pincode...",
  		"accountNumber": "...accountNumber...",
  		"bankName": "...bankName...",
  		"micrCode": "....micrCode...",
  		"contact": "...contact..",
  		"branch": "...branch...",
  		"name": "...name...",
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
    "service":"Identity",
    "itemId":"<Identity-id>",
    "task":"autoRecognition","accessToken":"<Identity-access-token>",
    "essentials":{}
   }

```


{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME       | DESCRIPTION                                                                                                                                                                                                                            |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result               | This holds the final response parameters.                                                                                                                                                                                              |
| result.address       | The address of the owner of the cancelled cheque.                                                                                                                                                                                      |
| result.ifsc          | The IFSC code of the bank to which the cancelled cheque is registered.                                                                                                                                                                 |
| result.pincode       | The pincode of the address which is registered to the cheque.                                                                                                                                                                          |
| result.accountNumber | The account number to which the cancelled cheque was issued.                                                                                                                                                                           |
| result.bankName      | The name of the bank which issued the cancelled cheque.                                                                                                                                                                                |
| result.micrCode      | The MICR code of the bank that issued the cheque.                                                                                                                                                                                      |
| result.contact       | The contact information of the bank which had issued the cheque.                                                                                                                                                                       |
| result.branch        | The branch of the bank that had issued the cancelled cheque.                                                                                                                                                                           |
| result.name          | The name of the individual on the cancelled cheque.                                                                                                                                                                                    |
| result.splitAddress  | This parameter distinguishes the various parts of the address of the cheque holder into separate categories like district, state, city, pincode and country. For the country category, acceptable values  is “IN”,”IND”and”INDIA”&#xD; |
| result.addressLine   | The first line of the address.                                                                                                                                                                                                         |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/0ffa0b4fb56f33c950cb)
