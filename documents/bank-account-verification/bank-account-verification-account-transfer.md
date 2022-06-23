# Bank Account Verification - Account Transfer

### Bank Account Transfer

You will need to [login](../../) before sending search request. You are required to pass the access token received from the login call, as authorization header in the IMPS transfer request.

For Account Transfer below fields are mandatory:

* Beneficiary Account
* Beneficiary IFSC
* Beneficiary Name (Optional)
* Beneficiary Mobile (Optional)

IFSC has two parameters - one will identify the name of the bank and another will identify the branch. So, here it will check the name of the bank, not the branch of the bank. It will verify the transaction based on the bank irrespective of any branch of that bank.

Example: SBIN0011542/ SBIN0011545 both will work here to complete the transaction for a particular beneficiary account belongs with the same bank.

Name of the account holder will be returned as it is registered in NPCI .

Use the following exchange parameters for bank account transfer.

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../bankaccountverifications" method="post" summary="Account Transfer" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../bankaccountverifications`

\




\


This method allows the verification of Bank Account Transfer.
{% endswagger-description %}

{% swagger-parameter in="body" name="essentials.beneficiaryName" type="string" %}
Beneficiary Name
{% endswagger-parameter %}

{% swagger-parameter in="body" name="namefuzzy" type="string" %}
Returns true/false
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
type Task to be performed - Bank Transfer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the essential beneficiary details
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.beneficiaryAccount" type="number" %}
Beneficiary Account number
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.beneficiaryIFSC" type="string" %}
Beneficiary IFSC code
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.beneficaryMovile" type="string" %}
Beneficiary Mobile Number
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
    "task": "bankTransfer",
    "essentials": {
      "beneficiaryMobile": ".....beneficiaryMobile.....",
      "beneficiaryAccount": "....beneficiaryAccount...",
      "beneficiaryName": "....beneficiaryName....",
      "beneficiaryIFSC": "....beneficiaryIFSC....",
      "nameFuzzy" : "true/false"
          },
    "id": ".....id.....",
    "patronId": "...patronID....",
    "result": {
       "active": "yes/no",
       "nameMatch": "yes/no",
       "mobileMatch": "yes/no",
       "signzyReferenceId": "...signzyReferenceId.....",
       "auditTrail": {
           "nature": "BANK RRN",
           "value": "....value....",
           "timestamp": "...timestamp....."
       },
       "bankTransfer": {
         "response": "...response...",
         "bankRRN": "...bankRRN...",
         "beneName": "...beneName..",
         "beneMMID": "...beneMMID...",
         "beneMobile": "...beneMobile...",
         "beneIFSC": "...beneIFSC.."
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
   "task" : "bankTransfer",
   "essentials": {
       "beneficiaryAccount": "......beneficiaryAccount.....",
       "beneficiaryIFSC": "......beneficiaryIFSC.....",
       "beneficiaryMobile": "....beneficiaryMobile (Optional)....",
       "beneficiaryName": "......beneficiaryName (Optional).....",
       "nameFuzzy" : "true/false"
    }
   }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME           | DESCRIPTION                                                                                                                                                                                         |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                   | This holds the final response parameters.                                                                                                                                                           |
| result.active            | This parameter displays whether the transfer status is active or not and returns a Yes/No response.                                                                                                 |
| result.nameMatch         | This parameter matches the entered name against the name in the bank records and returns a Yes/No response.                                                                                         |
| result.mobileMatch       | Whenever a transaction is generated, the reference is returned to the registered mobile number and this parameter checks if there is a match with the mobile reference to return a Yes/No response. |
| result.signzyReferenceId | This is the unique Signzy reference Id that is attached to the transaction for user reference.                                                                                                      |
| result.auditTrail        | This parameter is used to perform the details of an initiated transaction for later use for audit purposes.                                                                                         |
| auditTrail.nature        | This displays the unique receiver registration number or RRN for the particular bank where the transaction was initiated.                                                                           |
| auditTrail.value         | A unique reference value of the transaction is shown here.                                                                                                                                          |
| auditTrail.timestamp     | The timestamp of the transaction is displayed by this parameter.                                                                                                                                    |
| result.banktransfer      | The details of the bank transaction are recorded in this parameter.                                                                                                                                 |
| banktransfer.response    | The response received from the bank regarding the transaction.                                                                                                                                      |
| banktransfer.bankRRN     | The bank RRN number of the transaction.                                                                                                                                                             |
| banktransfer.beneName    | The name of the beneficiary on the transaction is displayed here.                                                                                                                                   |
| banktransfer.beneMMID    | The Mobile Money Identifier or MMID number of the beneficiary is shown here.                                                                                                                        |
| banktransfer.beneMobile  | The registered mobile number of the beneficiary is shown by this parameter.                                                                                                                         |
| banktransfer.beneIFSC    | The IFSC code of the beneficiary bank.                                                                                                                                                              |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/baaa150cbd46b3685c5b)

\
