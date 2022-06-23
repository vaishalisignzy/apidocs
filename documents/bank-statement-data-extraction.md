# Bank Statement Data Extraction

### Auto reading pdf

The Bank Statement Extraction API, as suggestive from the name, extracts the information that can be found in the bank statement pdf file. The bank statement should be in pdf format and in case only image/image URL is available, users can make use of our image to pdf converter for convenience.

To make any calls you need to be logged in. Learn more [login.](../)

Each **pdf** should be less than **2MB**.

#### Auto-reading Bank Statement Forms <a href="#reading-aadhaar-card-extraction" id="reading-aadhaar-card-extraction"></a>

Bank Statement auto-reading system accepts direct URL to the Bank Statement pdfs.

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../bankstatements" method="post" summary="Bank Statement Extraction" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your-patron-id../bankstatements`



\




\


This method is used to retrieve the bank statement details.
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

{% swagger-parameter in="body" name="essentials.url" type="string" %}
The URL of the bank statement image
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.bankname" type="string" %}
Bank Name for the issued statement
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.accountType" type="string" %}
Bank Account type
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    	"result": {
    		"bankName": "..bankName...",
    		"accountType": "..accountType..",
    		"accountHolder": "..accountHolder..",
    		"address": "..address..",
    		"accountLimit": "..accountLimit..",
    		"accountNo": "..accountNo..",
    		"availableCashLimit": "..availableCashLimit..",
    		"availableCreditLimit": "..availableCreditLimit..",
    		"bankAddress": "..bankAddress..",
    		"bankCredentialCO": "..bankCredentialCO..",
    		"bankTransactionList": ["..bankTransactionList..."],
    		"branchAddress": "..branchAddress..",
    		"cifNumber": "..cifNumber..",
    		"client": "..client..",
    		"creditCardNo": "..creditCardNo..",
    		"creditLimit": "..creditLimit..",
    		"crnNo": "..crnNo...",
    		"currentCashAdvance": "..currentCashAdvance..",
    		"currentPurchaseCharges": "..currentPurchaseCharges..",
    		"customer": "..customer..",
    		"customerID": "..customerID..",
    		"customerPhoneNo": "..customerPhoneNo..",
    		"dueDate": "..dueDate..",
    		"email": "..email..",
    		"fromDate": "..fromDate..",
    		"ifsCode": "..ifsCode..",
    		"lastPaymentReceived": "..lastPaymentReceived..",
    		"micrCode": "..micrCode..",
    		"minAmountDue": "..minAmountDue..",
    		"openingBalance": "..openingBalance..",
    		"pan": "..pan..",
    		"pointsEarned": "..pointsEarned..",
    		"prevBalance": "..prevBalance..",
    		"relationshipWithBank": "..relationshipWithBank..",
    		"toDate": "..toDate..",
    		"totalAmountDue": "..totalAmountDue..",
    		"allTransactions": [{
    			"amount": "..amount..",
    			"balanceAfterTransaction": "..balanceAfterTransaction...",
    			"date": "..date..",
    			"description": "..description..",
    			"firstLevelCategory": "..firstLevelCategory..",
    			"remark": "..remark..",
    			"secondLevelCategory": "..secondLevelCategory..",
    			"transactionNumber": "..transactionNumber..",
    			"type": "..type..",
    			"valueDate": "..valueDate.."
    		}],
    		"transactionDistribution": {
    			"atmWithdrawls": [{
    				"amount": "..amount..",
    				"bank": "..bank..",
    				"date": "..date..",
    				"time": "..time..",
    				"description": "..description.."
    			}],
    			"averageMonthlyBalance": [{
    				"netAverageBalance": "..netAverageBalance..",
    				"monthAndYear": "..monthAndYear..",
    				"dayBalanceMap": {
    					"1": "..amount..",
    					"5": "..amount..",
    					"10": "..amount..",
    					"15": "..amount..",
    					"20": "..amount..",
    					"25": "..amount..",
    					"30": "..amount.."
    				}
    			}],
    			"averageQuarterlyBalance": [{
    				"netAverageBalance": "..netAverageBalance..",
    				"monthAndYear": "..monthAndYear.."
    			}],
    			"expenses": [{
    				"amount": "..amount..",
    				"bank": "..bank..",
    				"category": "..category..",
    				"date": "..date..",
    				"time": "..time..",
    				"description": "..description.."
    			}],
    			"highValueTransactions": [{
    				"amount": "..amount..",
    				"bank": "..bank..",
    				"category": "..category..",
    				"balanceAfterTransaction": "..balanceAfterTransaction..",
    				"date": "..date..",
    				"time": "..time..",
    				"type": "..type..",
    				"description": "..description.."
    			}],
    			"incomes": [{
    				"amount": "..amount..",
    				"bank": "..bank..",
    				"category": "..category..",
    				"balanceAfterTransaction": "..balanceAfterTransaction..",
    				"date": "..date..",
    				"time": "..time..",
    				"transactionType": "..transactionType..",
    				"isSalary": "..isSalary..",
    				"isSalaryCheck": "..isSalaryCheck..",
    				"description": "..description..",
    				"total": "..total.."
    			}],
    			"internalTransactionList": [{
    				"amount": "..amount..",
    				"bank": "..bank..",
    				"category": "..category..",
    				"balanceAfterTransaction": "..balanceAfterTransaction..",
    				"date": "..date..",
    				"time": "..time..",
    				"transactionType": "..transactionType..",
    				"description": "..description.."
    			}],
    			"investments": [{
    				"amount": "..amount..",
    				"bank": "..bank..",
    				"category": "..category..",
    				"balanceAfterTransaction": "..balanceAfterTransaction..",
    				"date": "..date..",
    				"time": "..time..",
    				"type": "..type..",
    				"description": "..description.."
    			}],
    			"minimumBalances": [{
    				"amount": "..amount..",
    				"bank": "..bank..",
    				"category": "..category..",
    				"balanceAfterTransaction": "..balanceAfterTransaction..",
    				"date": "..date..",
    				"time": "..time..",
    				"transactionType": "..transactionType..",
    				"description": "..description.."
    			}],
    			"missingMonths": ["..missingMonths.."],
    			"moneyReceivedTransactions": [{
    				"amount": "..amount..",
    				"bank": "..bank..",
    				"category": "..category..",
    				"balanceAfterTransaction": "..balanceAfterTransaction..",
    				"date": "..date..",
    				"time": "..time..",
    				"transactionType": "..transactionType..",
    				"description": "..description..",
    				"total": "..total.."
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
      "essentials":{
      "url": "...url...",
      "bankName": "...bankName...",
      "accountType": "...accountType..."
     }
  }
```

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/5f0189ae5a5e27a78085)
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME                                  | DESCRIPTION                                                                                                                                                                                                                                                               |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                                          | This contains the final response parameters.                                                                                                                                                                                                                              |
| result.bankName                                 | The name of the bank for which bank statement is being retrieved.                                                                                                                                                                                                         |
| result.accountType                              | The type of bank account is displayed here.                                                                                                                                                                                                                               |
| result.accountHolder                            | The name of the account holder is displayed here.                                                                                                                                                                                                                         |
| result.address                                  | The address of the account holder.                                                                                                                                                                                                                                        |
| result.accountLimit                             | The maximum limit of the account is displayed here.                                                                                                                                                                                                                       |
| result.accountNo                                | The account number for which bank statement is being extracted.                                                                                                                                                                                                           |
| result.availableCashLimit                       | The maximum cash limit associated with the account is shown here.                                                                                                                                                                                                         |
| result.availableCreditLimit                     | The maximum credit limit associated with the account is shown here.                                                                                                                                                                                                       |
| result.bankAddress                              | The address of the bank for which records are being extracted.                                                                                                                                                                                                            |
| result.bankCredentialCO                         |                                                                                                                                                                                                                                                                           |
| result.bankTransactionList                      | This parameter contains the list (array) of transactions carried out by the bank.                                                                                                                                                                                         |
| result.branchAddress                            | The address of the bank branch where the savings account is being held.                                                                                                                                                                                                   |
| result.cifNumber                                | The cif number of the bank is shown here.                                                                                                                                                                                                                                 |
| result.client                                   | The client information of the bank account holder is shown here.                                                                                                                                                                                                          |
| result.CreditCardNo                             | This parameter contains the credit card number, if any, for the bank account holder.                                                                                                                                                                                      |
| result.creditLimit                              | The credit limit for the bank account holder, if any, is displayed here.                                                                                                                                                                                                  |
| result.crnNo                                    | The Customer Relationship Number for the bank account holder is displayed here.                                                                                                                                                                                           |
| result.currentCashAdvance                       | The current cash advance information for the credit card, if any, is displayed here.                                                                                                                                                                                      |
| result.currentpurchaseCharges                   | The current purchase charges accumulated on the credit card, if any, is displayed here.                                                                                                                                                                                   |
| result.customer                                 | The customer name is displayed here.                                                                                                                                                                                                                                      |
| result.customerId                               | The customer ID number is displayed here.                                                                                                                                                                                                                                 |
| result.customerPhoneNo                          | The customer phone number is displayed here.                                                                                                                                                                                                                              |
| result.dueDate                                  | The payment due date is displayed by this parameter.                                                                                                                                                                                                                      |
| result.email                                    | The email information of the customer is displayed here.                                                                                                                                                                                                                  |
| result.fromDate                                 | The date from which billing started is shown by this parameter.                                                                                                                                                                                                           |
| result.ifsCode                                  | The IFSC code for the bank of the account holder.                                                                                                                                                                                                                         |
| result.lastPaymentReceived                      | The information on the last received payment is displayed here.                                                                                                                                                                                                           |
| result.micrCode                                 | The MICR code for the bank of the account holder.                                                                                                                                                                                                                         |
| result.minAmountDue                             | The minimum due amount for the customer is displayed here.                                                                                                                                                                                                                |
| result.openingBalance                           | The opening balance amount for the bank account holder is displayed by this parameter.                                                                                                                                                                                    |
| result.pan                                      | The PAN card information for the account holder                                                                                                                                                                                                                           |
| result.pointsEarned                             | The number of points earned on the bank account.                                                                                                                                                                                                                          |
| result.prevBalance                              | The previous balance amount is displayed here.                                                                                                                                                                                                                            |
| result.relationshipWithBank                     | The bank relationship information is displayed here if available.                                                                                                                                                                                                         |
| result.toDate                                   |                                                                                                                                                                                                                                                                           |
| result.totalAmountDue                           | The total amount due for the particular customer is displayed here.                                                                                                                                                                                                       |
| result.allTransactions                          | This parameter displays the details of all the transactions and relevant information.                                                                                                                                                                                     |
| allTransactions.amount                          | The transaction amount is shown here.                                                                                                                                                                                                                                     |
| allTransactions.balanceAfterTransaction         | The remaining balance after the transaction.                                                                                                                                                                                                                              |
| allTransactions.date                            | The date of the transaction.                                                                                                                                                                                                                                              |
| allTransactions.description                     | This denotes the description of the type of transaction that is carried out.                                                                                                                                                                                              |
| allTransactions.firstLevelCategory              | This parameter describes the first level category information about the type of transaction performed.                                                                                                                                                                    |
| allTransactions.remark                          | This parameter contains the remarks/comments about the transaction.                                                                                                                                                                                                       |
| allTransactions.secondLevelCategory             | This parameter describes the second level category information about the type of transaction performed.                                                                                                                                                                   |
| allTransactions.transactionNumber               | The transaction number for the given transaction is shown here.                                                                                                                                                                                                           |
| allTransactions.type                            | The type of transaction being performed.                                                                                                                                                                                                                                  |
| allTransactions.valueDate                       | The value date of the transaction that is being carried out.                                                                                                                                                                                                              |
| result.transactionDistribution                  | The different kinds of transactions carried out for the bank account are displayed here.                                                                                                                                                                                  |
| transactionDistribution.atmWithdrawls           | The details about the transactions that occurred as ATM Withdrawals are displayed here.                                                                                                                                                                                   |
| atmWithdrawls.amount                            | The amount withdrawn from the ATM for each transaction.                                                                                                                                                                                                                   |
| atmWithdrawls.bank                              | The bank ATM information from which withdrawal was made.                                                                                                                                                                                                                  |
| atmWithdrawls.date                              | The date of the transaction.                                                                                                                                                                                                                                              |
| atmWithdrawls.time                              | The time of the transaction.                                                                                                                                                                                                                                              |
| atmWithdrawls.description                       | The description about the ATM from which withdrawal was made.                                                                                                                                                                                                             |
| result.averageMonthlyBalance                    | This shows the details about the average monthly balance.                                                                                                                                                                                                                 |
| averageMonthlyBalance.netAverageBalance         | This parameter displays the net average balance for a given month.                                                                                                                                                                                                        |
| averageMonthlyBalance.monthAndYear              | The month and year for which average monthly balance is being retrieved.                                                                                                                                                                                                  |
| averageMonthlyBalance.dayBalanceMap             | This parameter displays the balance amount for the different days of the month, namely 1st,5th,10th,15th,20th,25th and 30th day of the month.                                                                                                                             |
| result.averageQuarterlyBalance                  | This parameter shows the net average balance and the month and year for the average quarterly balance in a given quarter.                                                                                                                                                 |
| result.expenses                                 | The expense information of the account holder is displayed here.                                                                                                                                                                                                          |
| expenses.amount                                 | The amount expense for a particular transaction.                                                                                                                                                                                                                          |
| expenses.bank                                   | The bank information for the particular transaction.                                                                                                                                                                                                                      |
| expenses.category                               | The category of transaction that has been carried out as expense.                                                                                                                                                                                                         |
| expenses.date                                   | The date of the transaction.                                                                                                                                                                                                                                              |
| expenses.time                                   | The time of the transaction.                                                                                                                                                                                                                                              |
| expenses.description                            | The description of the expense transaction.                                                                                                                                                                                                                               |
| result.highValueTransactions                    | This parameter contains the details of the transactions with higher amounts.                                                                                                                                                                                              |
| highValueTransactions.amount                    | The amount for a particular transaction.                                                                                                                                                                                                                                  |
| highValueTransactions.bank                      | The bank information for the particular transaction.                                                                                                                                                                                                                      |
| highValueTransactions.category                  | The category of transaction that has been carried out as expense.                                                                                                                                                                                                         |
| highValueTransactions.balanceAfterTransaction   | This displays the remaining balance after the transaction.                                                                                                                                                                                                                |
| highValueTransactions.date                      | The date of the transaction.                                                                                                                                                                                                                                              |
| highValueTransactions.time                      | The time of the transaction.                                                                                                                                                                                                                                              |
| highValueTransactions.type                      | The type of the transaction carried out.                                                                                                                                                                                                                                  |
| highValueTransactions.description               | The description of the transaction is listed here.                                                                                                                                                                                                                        |
| result.incomes                                  | This parameter displays the relevant income information for the particular bank account.                                                                                                                                                                                  |
| incomes.amount                                  | The amount for the bank transaction.                                                                                                                                                                                                                                      |
| incomes.bank                                    | The bank information for the transaction.                                                                                                                                                                                                                                 |
| incomes.category                                | The category of transaction for the particular income.                                                                                                                                                                                                                    |
| incomes.balanceAfterTransaction                 | The available balance in the account after the transaction is concluded.                                                                                                                                                                                                  |
| incomes.date                                    | The date of the transaction.                                                                                                                                                                                                                                              |
| incomes.time                                    | The time of the transaction.                                                                                                                                                                                                                                              |
| incomes.transactionType                         | The type of transaction that occured for the particular income.                                                                                                                                                                                                           |
| incomes.isSalary                                | This parameter is used to check whether the particular income transaction is salary or not. Returns True/False.                                                                                                                                                           |
| incomes.isSalaryCheck                           | The parameter is used to confirm whether salary check has been performed for the particular transaction.                                                                                                                                                                  |
| incomes.description                             | The description for the transaction is displayed here.                                                                                                                                                                                                                    |
| incomes.total                                   | The total income for a particular time period for the given account.                                                                                                                                                                                                      |
| result.internalTransactionList                  | This parameter contains the details of internal transactions carried out for the bank account holder.                                                                                                                                                                     |
| internalTransactionList.amount                  | The amount for the transaction.                                                                                                                                                                                                                                           |
| internalTransactionList.bank                    | The bank information for the transaction.                                                                                                                                                                                                                                 |
| internalTransactionList. category               | This contains the category information for the transaction.                                                                                                                                                                                                               |
| internalTransactionList.balanceAfterTransaction | This parameter displays the available balance after the transaction is concluded.                                                                                                                                                                                         |
| internalTransactionList.date                    | The date of the transaction.                                                                                                                                                                                                                                              |
| internalTransactionList.time                    | The time of the transaction.                                                                                                                                                                                                                                              |
| internalTransactionList.transactionType         | The type of transaction being carried out.                                                                                                                                                                                                                                |
| internalTransactionList.description             | The description of the transaction.                                                                                                                                                                                                                                       |
| result.investments                              | This parameter contains the details of the investments made by the account holder.The details consist of transaction amount, bank information, transaction category, available balance after transaction, date, time, type of transaction and description.                |
| result.minimumbalances                          | This parameter contains the details of the minimum balances available for the account.The details consist of transaction amount, bank information, transaction category, available balance after transaction, date, time, type of transaction and description.            |
| result.missingMonths                            | This parameter contains the description of the number of months for which transactions are missing.                                                                                                                                                                       |
| result.moneyReceivedTransactions                | This parameter contains the details of money received in the account through transactions.The details consist of transaction amount, bank information, transaction category, available balance after transaction, date, time, type of transaction, description and total. |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/5f0189ae5a5e27a78085)

**Valid Account Type List**

1 ) SAVING\
2 ) CURRENT\
3 ) CREDIT\_CARD

**Valid Bank Name List**

1 ) ICICI \
2 ) SBI \
3 ) KOTAK \
4 ) YES \
5 ) HDFC \
6 ) AXIS \
7 ) SYNDICATE \
8 ) CORPORATION \
9 ) PNB\
10 ) UNITED\_BANK\
11 ) INDUSIND\
12 ) CENTRAL\_BANK\
13 ) CITI\
14 ) DBS\
15 ) CANARA\
16 ) STANDARD\_CHARTERED\
17 ) RBL\
18 ) UNION\_BANK\
19 ) ALLAHABAD\
20 ) BANK\_OF\_BARODA\
21 ) STATE\_BANK\_PATIALA\
22 ) STATE\_BANK\_MYSORE\
23 ) STATE\_BANK\_TRAVANCORE\
24 ) TAMILNAD\_MERCANTILE\
25 ) STATE\_BANK\_BIKANER\_JAIPUR\
26 ) STATE\_BANK\_HYDERABAD\
27 ) BANK\_OF\_INDIA\
28 ) BANK\_OF\_MAHARASHTRA\
29 ) DENA\_BANK\
30 ) INDIAN\_BANK\
31 ) INDIAN\_OVERSEAS\
32 ) ORIENTAL\_BANK\
33 ) PUNJAB\_SIND\
34 ) UCO\
35 ) VIJAYA36 ) IDBI\
37 ) BANDHAN\
38 ) CATHOLIC\_SYRIAN\
39 ) CITY\_UNION\
40 ) DHANLAXMI\
41 ) DCB\
42 ) FEDERAL\
43 ) IDFC\
44 ) KARNATAKA\
45 ) JAMMU\_KASHMIR\
46 ) KARUR\_VYASA\
47 ) LAKSHMI\_VILAS\
48 ) NAINITAL\
49 ) SOUTH\_INDIAN\
50 ) RBS\
51 ) SARASWAT\_BANK\
52 ) TJSB\
53 ) DNB\
54 ) DNS\
55 ) DEUTSCHE\_BANK\
56 ) GREATER\_BOMBAY\
57 ) APNA\_SAHAKARI\_BANK\
58 ) AKHAND\_ANAND\
59 ) ADARSH\_CO\_OPERATIVE\_URBAN\_BANK\
60 ) BASSEIN\_CATHOLIC\
61 ) ANDHRA\_BANK

**More Banks:**

62 ) AMBERNATH\_JAI\_HIND\_CO\_OP\_BANK63 ) PUNJAB\_MAHARASHTRA\_CO\_OP\_BANK64 ) HSBC65 ) BHARAT66 ) SVC\_BANK67 ) SDC68 ) SREENIDHI\_SOUHARDA\_SAHAKARI\_BANK69 ) OCEAN\_FIRST70 ) CAPITAL\_SMALL\_FINANCE\_BANK\_LTD71 ) KALUPUR\_COMMERCIAL\_CO\_OP\_BANK72 ) KANGRA\_CO\_OP\_BANK73 ) BHARTIYA\_MAHILA\_BANK74 ) SARDAR\_BHILADWALA\_PARDI\_PEOPLES\_CO\_OP\_BANK75 ) MODEL\_CO\_OPERATIVE\_BANK76 ) MEHSANA\_URBAN\_CO\_OP\_BANK77 ) NEW\_INDIA\_CO\_OP\_BANK78 ) THE\_NARODA\_NAGRIK\_CO\_OP\_BANK79 ) COSMOS\_BANK80 ) JANAKALYAN\_SAHAKARI\_BANK81 ) JANATA\_SAHAKARI\_BANK82 ) MJALGAON\_JANATA\_SAHAKARI\_BANK83 ) MANVI\_PATTANA\_SOUHARADA\_SAHAKARI\_BANK84 ) CENTRAL\_CO\_OPERATIVE\_BANK85 ) NUTAN\_NAGARIK\_SAHAKARI\_BANK86 ) KALYAN\_JANATA\_SAHAKARI\_BANK87 ) ABHYUDAYA\_CO\_OP\_BANK88 ) AIRTEL\_BANK89 ) EQUITAS\_SMALL\_FINANCE\_BANK90 ) AU\_SMALL\_FINANCE\_BANK91 ) NAGPUR\_NAGARIK\_SAHAKARI\_BANK92 ) TEXTILE\_CO\_OPERATIVE\_BANK93 ) JANASEVA\_SAHAKARI\_BANK94 ) SARASPUR\_NAGARIK\_CO\_OP\_BANK95 ) GP\_PARSIK\_BANK96 ) TGMC\_BANK97 ) SARVODAYA\_SAHAKARI\_BANK98 ) SHREE\_KADI\_NAGARIK\_SAHAKARI\_BANK99 ) SAURASHTRA\_GRAMIN\_BANK100 ) ASSOCIATE\_CO\_OP\_BANK101 ) SOLAPUR\_JANATA\_SAHAKARI\_BANK102 ) INDRAPRASTHA\_SEHKARI\_BANK103 ) MAHESH\_SAHAKARI\_BANK\_LTD104 ) PUNE\_PEOPLES\_CO\_OP\_BANK105 ) VASAI\_VIKAS\_SAH\_BANK\_LTD106 ) MAHESH\_BANK107 ) UNION\_CO\_OP\_BANK\_LTD108 ) JANATHA\_SEVA\_CO\_OP\_BANK109 ) The\_Wai\_Urban\_Co\_Operative\_Bank\_Limited110 ) The\_Vallabh\_VidyaNagar\_Commercial\_Co\_Operative\_Bank\_Ltd111 ) THE\_VIJAY\_CO\_OP\_BANK112 ) ZOROASTRIAN\_CO\_OP\_BANK113 ) VAIJAPUR\_MARCHANTS\_CO\_OP\_BANK114 ) NKGSB\_CO\_OP\_BANK115 ) THE\_SUTEX\_CO\_OP\_BANK116 ) THE\_SURAT\_PEOPLE\_CO\_OP\_BANK\_LTD117 ) GUJARAT\_AMBUJA\_CO\_OP\_BANK\_LTD118 ) KANKARIAA\_MANINAGAR\_NAG\_SAH\_BANK\_LTD119 ) UJJIVAN\_SMALL\_FINANCE\_BANK120 ) CITIZEN\_CREDIT\_CO\_OP\_BANK121 ) PADMAVATHI\_CO\_OP\_URBAN\_BANK122 ) THE\_SATARA\_SAHAKARI\_BANK\_LTD123 ) MAHANAGAR\_CO\_OP\_BANK\_LTD124 ) SURYODAY\_SMALL\_FINANCE\_BANK\_LTD125 ) SHREE\_CO\_OP\_BANK\_LTD126 ) MANINAGAR\_CO\_OP\_BANK\_LTD127 ) THE\_VARACHHA\_CO\_OP\_BANK\_LTD128 ) SURAT\_NATIONAL\_CO\_OP\_BANK\_LTD129 ) VIDYA\_SAHKARI\_BANK\_LTD130 ) THE\_KARAD\_URBAN\_CO\_OP\_BANK\_LTD131 ) THE\_PANCHSHEEL\_MERCANTILE\_CO\_OP\_BANK\_LTD132 ) MAGAVEERA\_CO\_OP\_BANK\_LTD133 ) THANE\_BHARAT\_SAHAKARI\_BANK\_LTD134 ) SREE\_MAHAYOGI\_LAKSHMAMMA\_CO\_OP\_BANK\_LTD135 ) VIDARBHA\_MERCHANTS\_URBAN\_CO\_OP\_BANK\_LTD136 ) PRATHAMA\_BANK137 ) PRIME\_BANK138 ) DR\_BABASAHEB\_AMBEDKAR\_MULTISTATE\_CO\_OP\_BANK139 ) The\_Hindusthan\_Co\_Op\_Bank\_Ltd140 ) KARNAVATI\_CO\_OP\_BANK141 ) The\_Ahmednagar\_Merchant\_Co\_Op\_Bank\_Ltd142 ) THE\_KANAKAMAHALAKSHMI\_CO\_OP\_BANK\_LTD143 ) KURMANCHAL\_BANK144 ) The\_Gandhidham\_CoOperative\_Bank\_Ltd145 ) SHRI\_ARIHANT\_COOP\_BANK146 ) Kallappanna\_Awade\_Bank147 ) Shivalik\_Mercantile\_Bank148 ) SAHYDRI\_SAHAKARI\_BANK149 ) Bihar\_Gramin\_Bank150 ) The\_Vishweshwar\_Sahakari\_Bank\_Ltd151 ) PURVANCHAL\_BANK152 ) THE\_RAJKOT\_COMMERCIAL\_COOP\_BANK153 ) The\_Jalgaon\_Peoples\_CoOp\_Bank154 ) AHMEDABAD\_DISTRICT\_CO\_OP\_BANK155 ) SHIVALIK\_MERCANTILE\_BANK156 ) The\_Akola\_District\_Central\_Co\_Op\_Bank157 ) The\_Panipat\_Urban\_Co\_Op\_Bank158 ) SHRI\_RAJKOT\_DISTRICT\_CO\_OP\_BANK159 ) NEELKANT\_CO\_OP\_BANK160 ) The\_Eenadu\_Co\_Op\_Urban\_Bank161 ) The\_Ahmedabad\_Mercantile\_Co\_Op\_Bank162 ) Adarsh\_Co\_Operative\_Bank\_Ltd163 ) Noida\_Commercial\_Co\_Op\_Bank164 ) Jai\_Tuljabhavani\_Urban\_Co\_Op\_Bank165 ) The\_Bardoli\_Nagarik\_Sahakari\_Bank166 ) RMGB167 ) Sterling\_Urban\_Co\_Op\_Bank168 ) Smriti\_Nagrik\_Sahakari\_Bank169 ) Fino\_Payments\_Bank170 ) Vaishya\_Nagari\_Sahakari\_Bank171 ) Vananchal\_Gramin\_Bank172 ) Utkarsh\_Small\_Finance\_Bank173 ) Maharashtra\_Gramin\_Bank174 ) Uttarakhand\_Gramin\_Bank175 ) Bhagyodaya\_Co\_Op\_Bank176 ) SANGOLA\_URBAN\_CO\_OPERATIVE\_BANK\_LTD177 ) Gujarat\_State\_Co\_Op\_Bank
