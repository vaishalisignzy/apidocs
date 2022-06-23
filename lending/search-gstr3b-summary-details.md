# Search GSTR3B Summary Details

### &#xD;Introduction

The GSTR 3B is a simple tax return form that has to be maintained separately for every GSTIN holder and contains the total values of sales and purchases that are reported in the forms       GSTR 1, 2, 3.&#x20;

### API Usecase

Similar to the other GSTR API’s, the GSTR3B Summary request generates all the transaction details of the form that is made available on the portal after submission. This eliminates the need for having to separately extract the details from the portal and can be issued by the API directly.

### How to call the API

You will need to login before sending GSTR3B summary Request. You are required to pass the access token received from the login call, as authorization header in the GSTR2a summary Request along with other parameters.

### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**
* Username registered on **GST Portal**
* **Auth Token** received from **** [GSTR Initiation Flow - Get Auth Token](gstr-initiation-flow-get-auth-token.md)
* **Secret Key**
* **App key r**eceived from **** [GSTR Initiation Flow - Get OTP Request](gstr-initiation-flow-get-otp-request.md)
*   Return Period

    <mark style="color:blue;"></mark>

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for GSTR3B summary Request

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization        | Required | String  | Access Token                                      |
| -------------------- | -------- | ------- | ------------------------------------------------- |
| Content-Type         | Required | String  | Application/JSON                                  |
| task                 | Required | String  | Type of task performed - Summary                  |
| essentials           | Required | Object  | This parameter contains the essential input data. |
| essentials.gstin     | Required | String  | GST Number of the organization                    |
| essentials.username  | Required | String  | Username from GST portal credentials              |
| essentials.authToken | Required | String  | AuthToken received in the authToken request       |
| essentials.appKey    | Required | String  | APP Key received in the OTP request               |
| essentials.sek       | Required | String  | Secret Key                                        |
| essentials.retPer    | Required | String  | Return period for which details to be searched    |
{% endtab %}

{% tab title="CURL Request" %}
```
 {
    "task" : "summary",
    "essentials": {
        "gstin": "..gstin..",
        "username": "..username..",
        "authToken": "..authToken..",
        "appKey": "..appKey..",
        "sek": "..sek..",
        "retPeriod": "..retPeriod.."
    }
  }
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters " %}
| PARAMETER NAME                                     | DESCRIPTION                                                                                                                                                                                              |
| -------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                                             | The final response parameters to be displayed as output.                                                                                                                                                 |
| result.message                                     | The status message is displayed here.                                                                                                                                                                    |
| result.data                                        | The details about the GSTR3B request are contained here.                                                                                                                                                 |
| data.gstin                                         | The GST identification number.                                                                                                                                                                           |
| data.retPeriod                                     | The return period for which GSTR3B is being fetched.                                                                                                                                                     |
| data.supplyDetails                                 | The detailed information about outward and inward supplies of the dealer/organization.                                                                                                                   |
| supplyDetails.outwardTaxableSuppliesNonZero        | This contains the details about the supplies on which GST rate is non-zero.                                                                                                                              |
| outwardTaxableSuppliesNonZero.totalTaxableValue    | The total taxable value of the supplies on which GST is applied.                                                                                                                                         |
| outwardTaxableSuppliesNonZero.integratedTax        | The total integrated GST on the supplies.                                                                                                                                                                |
| outwardTaxableSuppliesNonZero.centralTax           | The central GST on the supplies.                                                                                                                                                                         |
| outwardTaxableSuppliesNonZero.stateTax             | The state GST on the supplies.                                                                                                                                                                           |
| outwardTaxableSuppliesNonZero.cess                 | The cess amount applicable on the supplies.                                                                                                                                                              |
| supplyDetails.outwardTaxableSuppliesZero           | This contains the details about the supplies on which GST rate is zero.                                                                                                                                  |
| outwardTaxableSuppliesZero.totalTaxableValue       | The total taxable value of the supplies on which GST is applied.                                                                                                                                         |
| outwardTaxableSuppliesZero.integratedTax           | The total integrated GST on the supplies.                                                                                                                                                                |
| outwardTaxableSuppliesZero.centralTax              | The central GST on the supplies.                                                                                                                                                                         |
| outwardTaxableSuppliesZero.stateTax                | The state GST on the supplies.                                                                                                                                                                           |
| outwardTaxableSuppliesZero.cess                    | The cess amount applicable on the supplies.                                                                                                                                                              |
| supplyDetails.otherOutwardSupplies                 | This parameter contains information about other categories of outward supplies.                                                                                                                          |
| otherOutwardSupplies.totalTaxableValue             | The total taxable value of the supplies on which GST is applied.                                                                                                                                         |
| otherOutwardSupplies.integratedTax                 | The total integrated GST on the supplies.                                                                                                                                                                |
| otherOutwardSupplies.centralTax                    | The central GST on the supplies.                                                                                                                                                                         |
| otherOutwardSupplies.stateTax                      | The state GST on the supplies.                                                                                                                                                                           |
| otherOutwardSupplies.cess                          | The cess amount applicable on the supplies.                                                                                                                                                              |
| supplyDetails.inwardSuppliesReverseCharge          | This parameter contains the details of the reverse charge incurred on inward supplies.                                                                                                                   |
| inwardSuppliesReverseCharge.totalTaxableValue      | The total taxable value of the supplies on which GST is applied.                                                                                                                                         |
| inwardSuppliesReverseCharge.integratedTax          | The total integrated GST on the supplies.                                                                                                                                                                |
| inwardSuppliesReverseCharge.centralTax             | The central GST on the supplies.                                                                                                                                                                         |
| inwardSuppliesReverseCharge.stateTax               | The state GST on the supplies.                                                                                                                                                                           |
| inwardSuppliesReverseCharge.cess                   | The cess amount applicable on the supplies.                                                                                                                                                              |
| supplyDetails.outwardSuppliesNonGst                | This parameter contains the details of the outward supplies which are not applicable to GST.                                                                                                             |
| outwardSuppliesNonGst.totalTaxableValue            | The total taxable value of the supplies.                                                                                                                                                                 |
| outwardSuppliesNonGst.integratedTax                | The integrated tax applicable on the outward supplies.                                                                                                                                                   |
| outwardSuppliesNonGst.centralTax                   | The central tax applicable on the outward supplies.                                                                                                                                                      |
| outwardSuppliesNonGst.stateTax                     | The state tax applicable on the outward supplies.                                                                                                                                                        |
| outwardSuppliesNonGst.cess                         | The cess applicable on the outward supplies.                                                                                                                                                             |
| supplyDetails.interStateSupplies                   | This parameter contains the details on the inter-state supplies.                                                                                                                                         |
| interStateSupplies.unregisteredPersonSupplyDetails | This parameter displays the supply details for a person not registered with GST.                                                                                                                         |
| interStateSupplies.compositionPersonSupplyDetails  | This parameter displays the supply details for a person under the GST Composition Scheme.                                                                                                                |
| interStateSupplies.uinHolderSupplydetails          | This parameter displays the supply details for a person holding UIN or unique identification number and is exempt from GST.                                                                              |
| result.inputTaxCreditEligible                      | This parameter contains the input tax credit eligibility details.                                                                                                                                        |
| inputTaxCreditEligible.inputTaxCreditAvailable     | This parameter contains the details about the available input tax credit and displays the type of tax along with the amounts of integrated tax, central tax, state tax and cess applicable.              |
| inputTaxCreditEligible.inputTaxCreditReversed      | This parameter contains the information about reversed input tax credit and displays the type of tax along with the amounts of integrated tax, central tax, state tax and cess applicable.               |
| inputTaxCreditEligible.inputTaxCreditNet           | This parameter contains the details of the net input tax credit and displays the amounts of integrated tax, central tax, state tax and cess applicable.                                                  |
| inputTaxCreditEligible.inputTaxCreditIneligible    | This parameter contains the information about the ineligible input tax credit and displays the type of tax along with the amounts of integrated tax, central tax, state tax and cess applicable.         |
| result.inwardSupplies                              | This parameter contains details about the inward supplies and displays the type of inward supplies along with the type of inter-state and intra-state supplies'information.                              |
| result.interestLateFeePayable                      | This parameter contains the details about the interest fee and late fee payable and displays the amounts of integrated tax, central tax, state tax and cess applicable on the interest fee and late fee. |
| result.taxPayment                                  | This parameter contains details about the total tax payable and shows the breakup in the tax payable, interest payable and fee towards IGST, CGST,SGST and cess.                                         |
| result.paidThroughCash                             | This parameter contains details about the tax paid through cash towards IGST,CGST,SGST and cess. It also displays the transaction type, interest fee and late fee paid towards each.                     |
| result.paidThroughCredit                           | This parameter contains details about the tax paid through credit towards IGST,CGST,SGST and cess as well as the transaction type performed.                                                             |
{% endtab %}

{% tab title="Response" %}
```
 {
  "result": {
      "message": "..message..",
      "data": {
          "gstin": "..gstin..",
          "retPeriod": "..retPeriod..",
          "supplyDetails": {
              "outwardTaxableSuppliesNonZero": {
                  "totalTaxableValue": "..totalTaxableValue..",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..centralTax..",
                  "cess": "..cess.."
              },
              "outwardTaxableSuppliesZero": {
                  "totalTaxableValue": "..totalTaxableValue..",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..centralTax..",
                  "cess": "..cess.."
              },
              "otherOutwardSupplies": {
                  "totalTaxableValue": "..totalTaxableValue..",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..centralTax..",
                  "cess": "..cess.."
              },
              "inwardSuppliesReverseCharge": {
                  "totalTaxableValue": "..totalTaxableValue..",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..centralTax..",
                  "cess": "..cess.."
              },
              "outwardSuppliesNonGst": {
                  "totalTaxableValue": "..totalTaxableValue..",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..centralTax..",
                  "cess": "..cess.."
              }
          },
          "interStateSupplies": {
              "unregisteredPersonSupplyDetails": ["..unregisteredPersonSupplyDetails..."],
              "compositionPersonSupplyDetails": ["..compositionPersonSupplyDetails.."],
              "uinHolderSupplydetails": ["..uinHolderSupplydetails..."]
          },
          "inputTaxCreditEligible": {
              "inputTaxCreditAvailable": [{
                  "type": "..type...",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              }],
              "inputTaxCreditReversed": [{
                  "type": "..type...",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              }],
              "inputTaxCreditNet": [{
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              }],
              "inputTaxCreditIneligible": [{
                  "type": "..type...",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              }]
          },
          "inwardSupplies": {
              "inwardSuppliesDetails": [{
                  "type": "..type..",
                  "interStateSupplies": "..interStateSupplies..",
                  "intraStateSupplies": "..intraStateSupplies.."
              }]
          },
          "interestLateFeePayable": {
              "interestDetails": {
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              },
              "latefeeDetails": {
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              }
          },
          "taxPayment": {
              "taxPayable": [{
                  "transactionDescription": "..transactionDescription...",
                  "liabilityLedgerId": "..liabilityLedgerId...",
                  "transactionType": "..transactionType..",
                  "igst": {
                      "taxPayable": "...taxPayable...",
                      "interestPayable": "..interestPayable...",
                      "fee": "..fee.."
                  },
                  "cgst": {
                      "taxPayable": "...taxPayable...",
                      "interestPayable": "..interestPayable...",
                      "fee": "..fee.."
                  },
                  "sgst": {
                      "taxPayable": "...taxPayable...",
                      "interestPayable": "..interestPayable...",
                      "fee": "..fee.."
                  },
                  "cess": {
                      "taxPayable": "...taxPayable...",
                      "interestPayable": "..interestPayable...",
                      "fee": "..fee.."
                  }
              }],
              "paidThroughCash": [{
                  "liabilityLedgerId": "..liabilityLedgerId...",
                  "transType": "..transType...",
                  "igstPaid": "..igstPaid..",
                  "cgstPaid": "..cgstPaid..",
                  "sgstPaid": "..sgstPaid..",
                  "cessPaid": "..cessPaid..",
                  "interestPaidAgainstIGST": "..interestPaidAgainstIGST..",
                  "interestPaidAgainstCGST": "..interestPaidAgainstCGST..",
                  "interestPaidAgainstSGST": "..interestPaidAgainstSGST..",
                  "interestPaidAgainstCess": "..interestPaidAgainstCess..",
                  "lateFeePaidAgainstIGST": "..lateFeePaidAgainstIGST..",
                  "lateFeePaidAgainstCGST": "..lateFeePaidAgainstCGST..",
                  "lateFeePaidAgainstSGST": "..lateFeePaidAgainstSGST..",
                  "lateFeePaidAgainstCESS": "..lateFeePaidAgainstCESS.."
              }],
              "paidThroughCredit": {
                  "liabilityLedgerId": "..liabilityLedgerId...",
                  "transType": "..transType..",
                  "igstPaidusingIgst": "..igstPaidusingIgst...",
                  "igstPaidusingCgst": "..igstPaidusingCgst..",
                  "igstPaidusingSgst": "..igstPaidusingSgst..",
                  "cgstPaidusingIgst": "..cgstPaidusingIgst..",
                  "cgstPaidusingCgst": "..cgstPaidusingCgst..",
                  "sgstPaidusingIgst": "..sgstPaidusingIgst..",
                  "sgstPaidusingSgst": "..sgstPaidusingSgst..",
                  "cessPaidusingCess": "..cessPaidusingCess.."
              }
          }
      }
  }
}
```
{% endtab %}
{% endtabs %}

### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |
|             |                                        |



Use the following exchange parameters for GSTR3b summary Request

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../gstr3bs" method="post" summary="Search GSTR3B Summary details" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../gstr3bs`

\




\


This method is used to search the GSTR3B details.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - Summary
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.gstin" type="string" %}
GST Number of the organization	
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.username" type="string" %}
Username of your GST Portal Credentials
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.authToken" type="string" %}
AuthToken received in the authToken request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.appKey" type="string" %}
APP Key received in the OTP request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.sek" type="string" %}
Secret Key
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.retPeriod" type="string" %}
Return Period
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
  "result": {
      "message": "..message..",
      "data": {
          "gstin": "..gstin..",
          "retPeriod": "..retPeriod..",
          "supplyDetails": {
              "outwardTaxableSuppliesNonZero": {
                  "totalTaxableValue": "..totalTaxableValue..",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..centralTax..",
                  "cess": "..cess.."
              },
              "outwardTaxableSuppliesZero": {
                  "totalTaxableValue": "..totalTaxableValue..",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..centralTax..",
                  "cess": "..cess.."
              },
              "otherOutwardSupplies": {
                  "totalTaxableValue": "..totalTaxableValue..",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..centralTax..",
                  "cess": "..cess.."
              },
              "inwardSuppliesReverseCharge": {
                  "totalTaxableValue": "..totalTaxableValue..",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..centralTax..",
                  "cess": "..cess.."
              },
              "outwardSuppliesNonGst": {
                  "totalTaxableValue": "..totalTaxableValue..",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..centralTax..",
                  "cess": "..cess.."
              }
          },
          "interStateSupplies": {
              "unregisteredPersonSupplyDetails": ["..unregisteredPersonSupplyDetails..."],
              "compositionPersonSupplyDetails": ["..compositionPersonSupplyDetails.."],
              "uinHolderSupplydetails": ["..uinHolderSupplydetails..."]
          },
          "inputTaxCreditEligible": {
              "inputTaxCreditAvailable": [{
                  "type": "..type...",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              }],
              "inputTaxCreditReversed": [{
                  "type": "..type...",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              }],
              "inputTaxCreditNet": [{
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              }],
              "inputTaxCreditIneligible": [{
                  "type": "..type...",
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              }]
          },
          "inwardSupplies": {
              "inwardSuppliesDetails": [{
                  "type": "..type..",
                  "interStateSupplies": "..interStateSupplies..",
                  "intraStateSupplies": "..intraStateSupplies.."
              }]
          },
          "interestLateFeePayable": {
              "interestDetails": {
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              },
              "latefeeDetails": {
                  "integratedTax": "..integratedTax..",
                  "centralTax": "..centralTax..",
                  "stateTax": "..stateTax..",
                  "cess": "..cess.."
              }
          },
          "taxPayment": {
              "taxPayable": [{
                  "transactionDescription": "..transactionDescription...",
                  "liabilityLedgerId": "..liabilityLedgerId...",
                  "transactionType": "..transactionType..",
                  "igst": {
                      "taxPayable": "...taxPayable...",
                      "interestPayable": "..interestPayable...",
                      "fee": "..fee.."
                  },
                  "cgst": {
                      "taxPayable": "...taxPayable...",
                      "interestPayable": "..interestPayable...",
                      "fee": "..fee.."
                  },
                  "sgst": {
                      "taxPayable": "...taxPayable...",
                      "interestPayable": "..interestPayable...",
                      "fee": "..fee.."
                  },
                  "cess": {
                      "taxPayable": "...taxPayable...",
                      "interestPayable": "..interestPayable...",
                      "fee": "..fee.."
                  }
              }],
              "paidThroughCash": [{
                  "liabilityLedgerId": "..liabilityLedgerId...",
                  "transType": "..transType...",
                  "igstPaid": "..igstPaid..",
                  "cgstPaid": "..cgstPaid..",
                  "sgstPaid": "..sgstPaid..",
                  "cessPaid": "..cessPaid..",
                  "interestPaidAgainstIGST": "..interestPaidAgainstIGST..",
                  "interestPaidAgainstCGST": "..interestPaidAgainstCGST..",
                  "interestPaidAgainstSGST": "..interestPaidAgainstSGST..",
                  "interestPaidAgainstCess": "..interestPaidAgainstCess..",
                  "lateFeePaidAgainstIGST": "..lateFeePaidAgainstIGST..",
                  "lateFeePaidAgainstCGST": "..lateFeePaidAgainstCGST..",
                  "lateFeePaidAgainstSGST": "..lateFeePaidAgainstSGST..",
                  "lateFeePaidAgainstCESS": "..lateFeePaidAgainstCESS.."
              }],
              "paidThroughCredit": {
                  "liabilityLedgerId": "..liabilityLedgerId...",
                  "transType": "..transType..",
                  "igstPaidusingIgst": "..igstPaidusingIgst...",
                  "igstPaidusingCgst": "..igstPaidusingCgst..",
                  "igstPaidusingSgst": "..igstPaidusingSgst..",
                  "cgstPaidusingIgst": "..cgstPaidusingIgst..",
                  "cgstPaidusingCgst": "..cgstPaidusingCgst..",
                  "sgstPaidusingIgst": "..sgstPaidusingIgst..",
                  "sgstPaidusingSgst": "..sgstPaidusingSgst..",
                  "cessPaidusingCess": "..cessPaidusingCess.."
              }
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
    "task" : "summary",
    "essentials": {
        "gstin": "..gstin..",
        "username": "..username..",
        "authToken": "..authToken..",
        "appKey": "..appKey..",
        "sek": "..sek..",
        "retPeriod": "..retPeriod.."
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME                                     | DESCRIPTION                                                                                                                                                                                              |
| -------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                                             | The final response parameters to be displayed as output.                                                                                                                                                 |
| result.message                                     | The status message is displayed here.                                                                                                                                                                    |
| result.data                                        | The details about the GSTR3B request are contained here.                                                                                                                                                 |
| data.gstin                                         | The GST identification number.                                                                                                                                                                           |
| data.retPeriod                                     | The return period for which GSTR3B is being fetched.                                                                                                                                                     |
| data.supplyDetails                                 | The detailed information about outward and inward supplies of the dealer/organization.                                                                                                                   |
| supplyDetails.outwardTaxableSuppliesNonZero        | This contains the details about the supplies on which GST rate is non-zero.                                                                                                                              |
| outwardTaxableSuppliesNonZero.totalTaxableValue    | The total taxable value of the supplies on which GST is applied.                                                                                                                                         |
| outwardTaxableSuppliesNonZero.integratedTax        | The total integrated GST on the supplies.                                                                                                                                                                |
| outwardTaxableSuppliesNonZero.centralTax           | The central GST on the supplies.                                                                                                                                                                         |
| outwardTaxableSuppliesNonZero.stateTax             | The state GST on the supplies.                                                                                                                                                                           |
| outwardTaxableSuppliesNonZero.cess                 | The cess amount applicable on the supplies.                                                                                                                                                              |
| supplyDetails.outwardTaxableSuppliesZero           | This contains the details about the supplies on which GST rate is zero.                                                                                                                                  |
| outwardTaxableSuppliesZero.totalTaxableValue       | The total taxable value of the supplies on which GST is applied.                                                                                                                                         |
| outwardTaxableSuppliesZero.integratedTax           | The total integrated GST on the supplies.                                                                                                                                                                |
| outwardTaxableSuppliesZero.centralTax              | The central GST on the supplies.                                                                                                                                                                         |
| outwardTaxableSuppliesZero.stateTax                | The state GST on the supplies.                                                                                                                                                                           |
| outwardTaxableSuppliesZero.cess                    | The cess amount applicable on the supplies.                                                                                                                                                              |
| supplyDetails.otherOutwardSupplies                 | This parameter contains information about other categories of outward supplies.                                                                                                                          |
| otherOutwardSupplies.totalTaxableValue             | The total taxable value of the supplies on which GST is applied.                                                                                                                                         |
| otherOutwardSupplies.integratedTax                 | The total integrated GST on the supplies.                                                                                                                                                                |
| otherOutwardSupplies.centralTax                    | The central GST on the supplies.                                                                                                                                                                         |
| otherOutwardSupplies.stateTax                      | The state GST on the supplies.                                                                                                                                                                           |
| otherOutwardSupplies.cess                          | The cess amount applicable on the supplies.                                                                                                                                                              |
| supplyDetails.inwardSuppliesReverseCharge          | This parameter contains the details of the reverse charge incurred on inward supplies.                                                                                                                   |
| inwardSuppliesReverseCharge.totalTaxableValue      | The total taxable value of the supplies on which GST is applied.                                                                                                                                         |
| inwardSuppliesReverseCharge.integratedTax          | The total integrated GST on the supplies.                                                                                                                                                                |
| inwardSuppliesReverseCharge.centralTax             | The central GST on the supplies.                                                                                                                                                                         |
| inwardSuppliesReverseCharge.stateTax               | The state GST on the supplies.                                                                                                                                                                           |
| inwardSuppliesReverseCharge.cess                   | The cess amount applicable on the supplies.                                                                                                                                                              |
| supplyDetails.outwardSuppliesNonGst                | This parameter contains the details of the outward supplies which are not applicable to GST.                                                                                                             |
| outwardSuppliesNonGst.totalTaxableValue            | The total taxable value of the supplies.                                                                                                                                                                 |
| outwardSuppliesNonGst.integratedTax                | The integrated tax applicable on the outward supplies.                                                                                                                                                   |
| outwardSuppliesNonGst.centralTax                   | The central tax applicable on the outward supplies.                                                                                                                                                      |
| outwardSuppliesNonGst.stateTax                     | The state tax applicable on the outward supplies.                                                                                                                                                        |
| outwardSuppliesNonGst.cess                         | The cess applicable on the outward supplies.                                                                                                                                                             |
| supplyDetails.interStateSupplies                   | This parameter contains the details on the inter-state supplies.                                                                                                                                         |
| interStateSupplies.unregisteredPersonSupplyDetails | This parameter displays the supply details for a person not registered with GST.                                                                                                                         |
| interStateSupplies.compositionPersonSupplyDetails  | This parameter displays the supply details for a person under the GST Composition Scheme.                                                                                                                |
| interStateSupplies.uinHolderSupplydetails          | This parameter displays the supply details for a person holding UIN or unique identification number and is exempt from GST.                                                                              |
| result.inputTaxCreditEligible                      | This parameter contains the input tax credit eligibility details.                                                                                                                                        |
| inputTaxCreditEligible.inputTaxCreditAvailable     | This parameter contains the details about the available input tax credit and displays the type of tax along with the amounts of integrated tax, central tax, state tax and cess applicable.              |
| inputTaxCreditEligible.inputTaxCreditReversed      | This parameter contains the information about reversed input tax credit and displays the type of tax along with the amounts of integrated tax, central tax, state tax and cess applicable.               |
| inputTaxCreditEligible.inputTaxCreditNet           | This parameter contains the details of the net input tax credit and displays the amounts of integrated tax, central tax, state tax and cess applicable.                                                  |
| inputTaxCreditEligible.inputTaxCreditIneligible    | This parameter contains the information about the ineligible input tax credit and displays the type of tax along with the amounts of integrated tax, central tax, state tax and cess applicable.         |
| result.inwardSupplies                              | This parameter contains details about the inward supplies and displays the type of inward supplies along with the type of inter-state and intra-state supplies'information.                              |
| result.interestLateFeePayable                      | This parameter contains the details about the interest fee and late fee payable and displays the amounts of integrated tax, central tax, state tax and cess applicable on the interest fee and late fee. |
| result.taxPayment                                  | This parameter contains details about the total tax payable and shows the breakup in the tax payable, interest payable and fee towards IGST, CGST,SGST and cess.                                         |
| result.paidThroughCash                             | This parameter contains details about the tax paid through cash towards IGST,CGST,SGST and cess. It also displays the transaction type, interest fee and late fee paid towards each.                     |
| result.paidThroughCredit                           | This parameter contains details about the tax paid through credit towards IGST,CGST,SGST and cess as well as the transaction type performed.                                                             |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/de6a76b3bcbad389624b)
