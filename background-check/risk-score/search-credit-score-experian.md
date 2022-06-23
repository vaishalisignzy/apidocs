# Search Credit Score (EXPERIAN)

### Introduction

This API calculates the credit score and is similar to the CIBIL rating system. This is **Credit Score(Consumer Bureau) API**.

### API Usecase

Whenever an applicant applies for any kind of loan amount, the Credit Score API can be used to compare whether the candidate is eligible for the amount loaned and to extract the details regarding the eligibility of the applicant who is requesting the loan amount.

### How to call the API

You are required to pass the access token received from the login call, an authorization header in the request for Risk API along with other parameters.

### API Input Guidelines

You have to give applicant name, address, gender, address details in order to check credit score.

### Input Parameters & CURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/ optional | Description                                                                        |
| -------------- | ------------------ | ---------------------------------------------------------------------------------- |
| essentials     | Required           | Contains request data as JSON object                                               |
| task           | Required           | Type of task performed - Consumer                                                  |
| applicant      | Required           | Contains the applicant details like name, gender, pan number, passport number etc. |
| address        | Required           | Contains the address specifics like city, landmark, state, pincode etc.            |
{% endtab %}

{% tab title="Sample CURL Request" %}
```
```
{% endtab %}
{% endtabs %}

### Output Parameters & API Response

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME                              | DESCRIPTION                                                                                                                                                                                            |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| result                                      | This contains the final response parameters.                                                                                                                                                           |
| result.summary                              | The summary of the applicant.                                                                                                                                                                          |
| summary.score                               | The credit score of the applicant.                                                                                                                                                                     |
| score.userProfile                           | The user profile details,                                                                                                                                                                              |
| score.CreditProfile                         | This parameter contains the credit history of the applicant.                                                                                                                                           |
| creditProfile.creditAccountSummary          | This parameter contains the details of the applicant's credit account.                                                                                                                                 |
| creditProfile.currentBalanceAmountSummary   | This parameter displays the current balance amount details of the applicant.                                                                                                                           |
| result.detailed                             | This parameter contains the detailed system report information.                                                                                                                                        |
| detailed.header                             | The system report information is attached to the top of the report as header.                                                                                                                          |
| header.systemCode                           | The system code is displayed here.                                                                                                                                                                     |
| header.reportData                           | This parameter displays the data about whom the credit report is displayed.                                                                                                                            |
| header.reportTime                           | The time of the report.                                                                                                                                                                                |
| result.userMessage                          | This parameter contains the text information for the user.                                                                                                                                             |
| result.creditProfileHeader                  | This parameter contains the details about the applicant profile such as username of the enquirer, date and time of the report, version number, report number and the name of the subscriber/applicant. |
| result.currentApplication                   | This parameter describes the details on the application like first and last name, gender, PAN number and date of birth of the applicant.                                                               |
| result.currentApplicantAddressDetails       | This parameter contains the detailed applicant address details like flat number, building number, city,state, pincode and country code.                                                                |
| currentApplicantDetails.enquiryReason       | The reason of enquiry for the applicants credit report.                                                                                                                                                |
| currentApplicantDetails.amountFinanced      | The amount that has been financed to the credit applicant is shown here.                                                                                                                               |
| currentApplicantDetails.durationOfAgreement | This parameter shows the duration of agreement for the amount financed to the credit applicant.                                                                                                        |
| result.caisAccount                          | This parameter displays the account information as available from the credit account information sharing network against the credit applicant.                                                         |
| result.caisAccountDetails                   | This parameter displays the detailed account information of the credit applicant showing the existing credit line and history.                                                                         |
| result.caisHolderDetails                    | This parameter displays the name and demographic information of the credit applicant as registered with CAIS.                                                                                          |
| result.caisHolderAddressDetails             | This parameter displays the detailed address information as available with the CAIS portal.                                                                                                            |
| result.caisHolderPhoneDetails               | This parameter displays the phone number of the credit applicant.                                                                                                                                      |
| result.caisHolderIDDetails                  | The Pan number of the credit applicant.                                                                                                                                                                |
| result.matchResult                          | If the details being searched are a match, then the information is displayed here about the match.                                                                                                     |
| result.totalCapsSummary                     | The total interest rate accumulated over varying periods of time.                                                                                                                                      |
| result.capsSummary                          | The interest rate to be applied over varying periods of time to the creditor.                                                                                                                          |
| result.capsApplicationDetails               | The applicant details to whom caps are being applied.                                                                                                                                                  |
| result.capsOtherDetails                     | This contains the address details of the applicant.                                                                                                                                                    |
| result.nonCreditCaps                        | This contains the information about caps accrued outside the credit.                                                                                                                                   |
| result.score                                | This parameter contains the consumer bureau score along with the confidence level and credit score of the applicant, based on all details.                                                             |
{% endtab %}

{% tab title="Sample API Response" %}
```
```
{% endtab %}
{% endtabs %}

### HTTP Response Codes

| Status Code | Error Message               | Possible Fix                   |
| ----------- | --------------------------- | ------------------------------ |
| 200         | Successful                  | Nothing to fix                 |
| 400         | Missing or Invalid data     | Check all the input parameters |
| 401         | Authorization Required      | Check Authorization Header     |
| 404         | No method to handle request | Check URL endpoint of API      |
| 422         | Unprocessable Entity        | Notify our support team        |
