# ITR - Form 26AS Data Extraction

#### Auto-reading of ITR Form-26AS <a href="#reading-aadhaar-card-extraction" id="reading-aadhaar-card-extraction"></a>

Form 26AS is an annual consolidated credit statement issued under Section 203AA of the Income-tax Act, 1961. It contains details of various taxes deducted on your income by deductors: be it your employer, bank, or even a tenant.&#x20;

This API service accepts the form in pdf format and extracts and generates the details like Assessee name, address, Year of Assessment and so on. In case no pdf file is available, you can make use of Signzy converters to get the pdf files.

To make any calls you need to be logged in. Learn more login.

ITR auto-reading system accepts direct URL to the form-26AS pdfs.\


{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/..your-patron-id../itrs" method="post" summary="Form 26AS Extraction" %}
{% swagger-description %}
**Production URL:**

\


****

`https://signzy.tech/api/v2/patrons/..your-patron-id../itrs`

\




\


This method is used to extract the details of Form 26AS.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
Type - Form 26AS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.url" type="string" %}
URL of the image of Form 26AS
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.dob" type="string" %}
Date Of Birth of the individual
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    	"essentials": {
    		"url": "...url...",
            "dob" : "..dob.."
    	},
    	"id": "...accessToken...",
    	"patronId": "...patronId...",
    	"type": "...type...",
    	"result": {
    		"financialYear": "...financialYear...",
    		"addressofAssessee": "...addressofAssessee...",
    		"assessmentYear": "...assessmentYear...",
    		"pan": "...pan...",
    		"statusOfPan": "...statusOfPan...",
    		"nameofAssessee": "...nameofAssessee...",
    		"transactions": {
    			"a": {
    				"description": "...description...",
    				"transactions": [{
    					"srNo": "...srNo...",
    					"nameOfDeductor": "...nameOfDeductor...",
    					"tanOfDeductor": "...tanOfDeductor...",
    					"totalAmountPaidOrCreditedInInr": "...totalAmountPaidOrCreditedInInr...",
    					"totalTaxDeductedInInr": "...totalTaxDeductedInInr...",
    					"totalTDSDepositedInInr": "...totalTDSDepositedInInr..."
    				}]
    			},
    			"a1": {
    				"description": "...description...",
    				"transactions": [{
    					"srNo": "...srNo...",
    					"nameOfDeductor": "...nameOfDeductor...",
    					"tanOfDeductor": "...tanOfDeductor...",
    					"totalAmountPaidOrCreditedInInr": "...totalAmountPaidOrCreditedInInr...",
    					"totalTaxDeductedInInr": "...totalTaxDeductedInInr...",
    					"totalTDSDepositedInInr": "...totalTDSDepositedInInr..."
    				}]
    			},
    			"a2": {
    				"description": "...description...",
    				"transactions": [{
    					"srNo": "...srNo...",
    					"acknowledgementNumber": "...acknowledgementNumber...",
    					"nameOfDeductor": "...nameOfDeductor...",
    					"panOfDeductor": "...panOfDeductor...",
    					"transactionDate": "...transactionDate...",
    					"totalTransactionAmountInInr": "...totalTransactionAmountInInr...",
    					"totalTDSDepositedInInr": "...totalTDSDepositedInInr..."
    				}]
    			},
    			"b": {
    				"description": "...description...",
    				"transactions": [{
    					"srNo": "...srNo...",
    					"nameOfCollector": "...nameOfCollector...",
    					"tanOfCollector": "...tanOfCollector...",
    					"totalAmountPaidOrDebitedInInr": "...totalAmountPaidOrDebitedInInr...",
    					"totalTaxCollectedInInr": "...totalTaxCollectedInInr...",
    					"totalTCSDepositedInInr": "...totalTCSDepositedInInr..."
    				}]
    			},
    			"c": {
    				"description": "...description...",
    				"transactions": [{
    					"srNo": "...srNo...",
    					"majorHead": "...majorHead...",
    					"minorHead": "...minorHead...",
    					"taxInInr": "...taxInInr...",
    					"surchargeInInr": "...surchargeInInr...",
    					"educationCessInInr": "...educationCessInInr...",
    					"others": "...others...",
    					"totalTaxInInr": "...totalTaxInInr...",
    					"bsrCode": "...bsrCode...",
    					"dateOfDeposit": "...dateOfDeposit...",
    					"challanSerialNumber": "...challanSerialNumber...",
    					"remarks": "...remarks..."
    				}]
    			},
    			"d": {
    				"description": "...description...",
    				"transactions": [{
    					"srNo": "...srNo...",
    					"assessmentYear": "...assessmentYear...",
    					"mode": "...mode...",
    					"refundIssued": "...refundIssued...",
    					"natureOfRefund": "...natureOfRefund...",
    					"amountOfRefundInInr": "...amountOfRefundInInr...",
    					"interestInInr": "...interestInInr...",
    					"dateOfPayment": "...dateOfPayment...",
    					"remarks": "...remarks..."

    				}]
    			},
    			"e": {
    				"description": "...description...",
    				"transactions": [{
    					"srNo": "...srNo...",
    					"typeOfTransaction": "...typeOfTransaction...",
    					"nameOfAIRFiler": "...nameOfAIRFiler...",
    					"transactionDate": "...transactionDate...",
    					"singleOrJointPartyTransaction": "...singleOrJointPartyTransaction...",
    					"numberOfParties": "...numberOfParties...",
    					"amountInInr": "...amountInInr...",
    					"mode": "...mode...",
    					"remarks": "...remarks..."
    				}]
    			},
    			"f": {
    				"description": "...description...",
    				"transactions": [{
    					"srNo": "...srNo...",
    					"acknowledgementNumber": "...acknowledgementNumber...",
    					"nameOfDeductee": "...nameOfDeductee...",
    					"panOfDeductee": "...panOfDeductee...",
    					"transactionDate": "...transactionDate...",
    					"totalTransactionAmountInInr": "...totalTransactionAmountInInr...",
    					"totalTDSDepositedInInr": "...totalTDSDepositedInInr...",
    					"totalAmountDepositedOtherThanTDSInInr": "...totalAmountDepositedOtherThanTDSInInr..."
    				}]
    			},
    			"g": {
    				"description": "...description...",
    				"transactions": [{
    					"srNo": "...srNo...",
    					"financialYear": "...financialYear...",
    					"shortPayment": "...shortPayment...",
    					"shortDeduction": "...shortDeduction...",
    					"interestOnTDSPaymentsDefaultInInr": "...interestOnTDSPaymentsDefaultInInr...",
    					"InterestOnTDSDeductionDefaultInInr": "...InterestOnTDSDeductionDefaultInInr...",
    					"lateFillingFeeUS234EInInr": "...lateFillingFeeUS234EInInr...",
    					"interestUS220(2InInr)": "...)...",
    					"totalDefaultInInr": "...totalDefaultInInr..."
    				}]
    			}
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
      "type":"form26",
      "essentials":{
        "url" : "...url...",
        "dob" : "..dob.."
      }
    }
```

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/fd9cc1ae247aa5b30b0f)
{% endtab %}

{% tab title="Response Parameters" %}
The following parameters will be searched for Part a,a1,a2,b

| PARAMETER NAME                              | DESCRIPTION                                                                    |
| ------------------------------------------- | ------------------------------------------------------------------------------ |
| result                                      | The final response parameters to be generated for output.                      |
| result.financialYear                        | The financial year for which Forn 26AS is being searched.                      |
| result.addressofAssessee                    | The address of the assessee whose Form 26AS is being searched.                 |
| result.assessmentYear                       | The assessment year for which Forn 26AS is being searched.                     |
| result.pan                                  | The PAN number of the assessee.                                                |
| result.statusOfPan                          | The status of PAN of the assessee.                                             |
| result.nameofAssessee                       | The name of the assessee.                                                      |
| result.transactions                         | This shows the total transaction information for all parts as mentioned above. |
| description                                 | The description of the part of form 26AS being displayed.                      |
| transactions.srNo                           | The serial number of the transaction.                                          |
| transactions.nameOfDeductor                 | The name of the deductor/assessee whose transaction is being displayed.        |
| transactions.tanOfDeductor                  | The TAN number of the assessee.                                                |
| transactions.totalAmountPaidOrCreditedInInr | The total amount in rupees that has been paid and credited.                    |
| transactions.totalTaxDeductedInInr          | The total amount in rupees for the total tax deducted.                         |
| transactions.totalTDSDepositedInInr         | The total amount in rupees for the total TDS deposited.                        |

The following parameters are used for part c of Form 26AS

| PARAMETER NAME                   | DESCRIPTION                                                                 |
| -------------------------------- | --------------------------------------------------------------------------- |
| transactions.taxInInr            | The total tax amount in rupees.                                             |
| transactions.surchargeInInr      | The total surcharge amount in rupees.                                       |
| transactions.educationCessInInr  | The total education cess in rupees.                                         |
| transactions.others              | This parameter displays any other tax amount payable in rupees, if any.     |
| transactions.totalTaxInInr       | The total tax payable iin rupees.                                           |
| transactions.bsrCode             | The basic statistical return code for the bank account linked to form 26AS. |
| transactions.dateOfDeposit       | The date of deposit of the taxable amount.                                  |
| transactions.challanSerialNumber | The serial number of the challan issued to the assessee.                    |
| transactions.remarks             | This parameter contains any additional notes/remarks.                       |

The following parameters are used for part D of Form 26AS

| PARAMETER NAME                   | DESCRIPTION                                                      |
| -------------------------------- | ---------------------------------------------------------------- |
| transactions.mode                | The mode of transaction of the assessee.                         |
| transactions.refundIssued        | This parameter displays the details of the refund amount issued. |
| transactions.natureOfRefund      | The nature of refund is displayed by this parameter.             |
| transactions.amountOfRefundInInr | The total refund amount issued in Indian rupees.                 |
| transactions.interestInInr       | The interest amount in Indian rupees.                            |
| transactions.dateOfPayment       | The date of payment of the refund amount is displayed here.      |
| transactions.remarks             | This parameter contains any additional notes/remarks.            |

The following parameters are used for part E of Form 26AS

| PARAMETER NAME                             | DESCRIPTION                                                       |
| ------------------------------------------ | ----------------------------------------------------------------- |
| transactions.typeOfTransaction             | The type of transaction being conducted is displayed here.        |
| transactions.nameOfAIRFiler                | The name of annual information return filer.                      |
| transactions.transactionDate               | The date of transaction as recorded in part E of form 26AS.       |
| transactions.singleOrJointPartyTransaction | Whether the transaction is a single or a joint party transaction. |
| transactions.numberOfParties               | The number of parties involved in the transaction.                |
| transactions.amountInInr                   | The total transaction amount in Indian rupees.                    |
| transactions.mode                          | This parameter displays the mode of transaction.                  |
| transactions.remarks                       | This parameter contains any additional notes/remarks.             |

The following parameters are used for part F of Form 26AS

| PARAMETER NAME                                     | DESCRIPTION                                                        |
| -------------------------------------------------- | ------------------------------------------------------------------ |
| transactions.acknowledgementNumber                 | The acknowledgement number for the transaction made.               |
| transactions.nameOfDeductee                        | The name of the deductee.                                          |
| transactions.panOfDeductee                         | The PAN number of the deductee.                                    |
| transactions.transactionDate                       | The date of transaction asociated with part E.                     |
| transactions.totalTransactionAmountInInr           | The total transaction amount in Indian rupees.                     |
| transactions.totalTDSDepositedInInr                | The total TDS amount deposited in Indian rupees.                   |
| transactions.totalAmountDepositedOtherThanTDSInInr | The total amount other than TDS that is deposited in Indian rupees |

The following parameters are used for part G of Form 26AS

| PARAMETER NAME                                  | DESCRIPTION                                                                    |
| ----------------------------------------------- | ------------------------------------------------------------------------------ |
| transactions.financialYear                      | The financial year for which form 26AS is being retrieved.                     |
| transactions.shortPayment                       | The short payment amount is displayed here.                                    |
| transactions.shortDeduction                     | The short deduction amount is displayed here.                                  |
| transactions.interestOnTDSPaymentsDefaultInInr  | The default interest on TDS Payments is displayed in Indian rupees.            |
| transactions.InterestOnTDSDeductionDefaultInInr | The default interest on TDS deductions is displayed in Indian rupees.          |
| transactions.lateFillingFeeUS234EInInr          | The late filing fee amount under section US 234 is displayed in Indian rupees. |
| transactions.interestUS220(2InInr)              | The interest amount under section US 220(2) is displayed in Indian rupees.     |
| transactions.totalDefaultInInr                  | The total default payment amount in Indian rupees.                             |
{% endtab %}
{% endtabs %}

