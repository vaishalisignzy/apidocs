# Negative Due Diligence Check

### **Introduction**

In addition to counterfeit and fraud detection in terms of financial software, Signzy also provides APIs that can check fraudulent or bogus information that is used for malpractice. The Negative Due Diligence Negative Check is used for finding or eliminating people who have provided false information or have been responsible for the same in the past for the purpose of malpractice in terms of banking and financial software.

### API Usecase

Whenever a name entered in the API matches any of the blacklisted names in the database, a match is returned with the details of the perpetrator.

### How to call the API

You are required to pass the access token received from the login call, an authorization header in the Negative Due Diligence Negative Check request along with other parameters.



### API Input Guidelines

We have to give name of any person/organization to check negative due diligence.

### Input Parameters & CURL Requests

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name             | Required/ optional | Description                                                                        |
| -------------------------- | ------------------ | ---------------------------------------------------------------------------------- |
| essentials                 | Required           | Contains request data as JSON object.                                              |
| name                       | Required           | Name of the individual/entity whose background check has to be done.               |
| type                       | Required           | Whether it is an indivdual or an entity.                                           |
| category                   | optional           | Negative Categories List on which search has to be done for the individual/entity. |
| matchScoreThreshold        | optional           | Threshold Score upto which search has to be done for the individual/entity         |
| dateOfBirthOrIncorporation | optional           | Date of Birth/Date of Incorporation of the individual/entity                       |
| identificationNumber       | optional           | Identification Number of the individual/entity                                     |
| zipcode                    | optional           | zipcode of the place where individual/entity resides                               |
| country                    | optional           | Name of the country where individual/entity resides                                |
| aliasArray                 | optional           | Alternate names of the individual/entity                                           |
| searchText                 | optional           | Specific Words on which search has to be done for the individual/entity            |


{% endtab %}

{% tab title="Sample CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<patron id>/negativeduediligences' \
--header 'Content-Type: application/json' \
--header 'Authorization: <Authorization token>' \
--data-raw '{"task":"negativeCheck","essentials":{"name":"signzy","type":"entity","matchScoreThreshold":"0.50","category":["AML","CFT","NONCOMPLIANCE","LENDING"]}}'
```
{% endtab %}
{% endtabs %}

### Output Parameters & API Response

{% tabs %}
{% tab title="Response Parameters" %}
The following parameters are checked for negative due diligence check against several databases like Blacklisted Entities, UN sanction list, NBFC, MCA etc

| Parameter Name                   | Description                                                                                                                    |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| result                           | This contains the final response parameters to be displayed for output.                                                        |
| scores                           | This parameter assigns scores on the basis of match against each parameter searched in the database.                           |
| scores.nameMatch                 | This parameter checks whether the name of an individual/organization matches with any entry in the database.                   |
| scores.dobMatch                  | This parameter checks whether the dob of an individual matches with any entry in the database.                                 |
| scores.countryMatch              | This parameter checks whether the country of an individual/organization matches with any entry in the database.                |
| scores.zipcodeMatch              | This parameter checks whether the zipcode in the address of an individual/organization matches with any entry in the database. |
| scores.aliasArrayMatch           | This parameter checks whether the list of aliases of an individual/organization matches with any entry in the database.        |
| scores.identificationNumberMatch | This parameter checks whether the identification number of an individual/organization matches with any entry in the database.  |
| scores.searchTextMatch           | This parameter checks for any text match in the database.                                                                      |
| details                          | This parameter displays any particular details in the database.                                                                |
| relevance                        | This parameter verifies for relevance against the individual/entity being searched in the database.                            |
| overallScore                     | The overall score against an individual/entity match that was being searched in the database.                                  |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "essentials": {
        "name": "signzy",
        "type": "entity",
        "matchScoreThreshold": "0.50",
        "category": [
            "AML",
            "CFT",
            "NONCOMPLIANCE",
            "LENDING"
        ]
    },
    "id": "61447fbbf6d4030eae05425a",
    "patronId": "614097a1f6d4030eae049781",
    "task": "negativeCheck",
    "result": {
        "blacklistedEntities": [
            {
                "scores": {
                    "nameMatch": "60.89",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "code": "C0204090",
                    "name": "SIGNUP EDUCATION PVT.LTD.",
                    "history": [
                        {
                            "regulatoryAction": "PERSONS DISQUALIFIED FROM DIRECTORSHIP FOR THE PERIOD 01-NOV-2016 TO 31-OCT-2021 15-SEP-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "SIGNUP EDUCATION PVT.LTD.",
                            "regulatoryCharges": "DID NOT FILE FINANCIAL STATEMENTS OR ANNUAL RETURNS FOR ANY CONTINUOUS PERIOD OF 3 FINANCIAL YEARS"
                        }
                    ],
                    "persons": [
                        {
                            "regulatoryAction": "PERSONS DISQUALIFIED FROM DIRECTORSHIP FOR THE PERIOD 01-NOV-2016 TO 31-OCT-2021 15-SEP-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "GAGAN GUJRAL",
                            "regulatoryCharges": "DID NOT FILE FINANCIAL STATEMENTS OR ANNUAL RETURNS FOR ANY CONTINUOUS PERIOD OF 3 FINANCIAL YEARS"
                        },
                        {
                            "regulatoryAction": "PERSONS DISQUALIFIED FROM DIRECTORSHIP FOR THE PERIOD 01-NOV-2016 TO 31-OCT-2021 15-SEP-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "SHALINI GUJRAL",
                            "regulatoryCharges": "DID NOT FILE FINANCIAL STATEMENTS OR ANNUAL RETURNS FOR ANY CONTINUOUS PERIOD OF 3 FINANCIAL YEARS"
                        }
                    ]
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "60.89"
            },
            {
                "scores": {
                    "nameMatch": "62.22",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "code": "C0069720",
                    "name": "SIGNET OVERSEAS LTD.",
                    "history": [
                        {
                            "regulatoryAction": "PUT UP ON BSE WEBSITE FOR PUBLIC NOTICE 30-JUN-2008",
                            "furtherDevelopments": "NOT APPEARING IN THE LIST FOR THE QUARTER ENDED 30-SEPTEMBER-2008",
                            "competentAuthority": "BSE",
                            "name": "SIGNET OVERSEAS LTD.",
                            "regulatoryCharges": "DID NOT SUBMIT SHAREHOLDING PATTERN UNDER PROVISIONS OF CLAUSE 35 FOR THE QUARTER ENDED 30-JUNE-2008"
                        },
                        {
                            "regulatoryAction": "SUSPENDED FOR TRADING 30-NOV-2007",
                            "furtherDevelopments": "REVOCATION OF SUSPENSION IN TRADING",
                            "competentAuthority": "BSE",
                            "name": "SIGNET OVERSEAS LTD.",
                            "regulatoryCharges": "DID NOT COMPLY WITH LISTING AGREEMENT"
                        }
                    ],
                    "persons": []
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "62.22"
            },
            {
                "scores": {
                    "nameMatch": "68.89",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "code": "C0091506",
                    "name": "SIGN WORLD",
                    "history": [
                        {
                            "regulatoryAction": "NOTICE ISSUED UNDER SECTION 142 OF CUSTOMS ACT, 1962 17-FEB-2010",
                            "furtherDevelopments": "",
                            "competentAuthority": "CBEC",
                            "name": "SIGN WORLD",
                            "regulatoryCharges": "DEFAULTED IN PAYMENT OF CUSTOMS/EXCISE DUTIES"
                        }
                    ],
                    "persons": [
                        {
                            "regulatoryAction": "NOTICE ISSUED UNDER SECTION 142 OF CUSTOMS ACT, 1962 17-FEB-2010",
                            "furtherDevelopments": "",
                            "competentAuthority": "CBEC",
                            "name": "SESACHALAM.G",
                            "regulatoryCharges": "DEFAULTED IN PAYMENT OF CUSTOMS/EXCISE DUTIES"
                        }
                    ]
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "68.89"
            },
            {
                "scores": {
                    "nameMatch": "61.90",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "code": "C0217599",
                    "name": "SIGNAL CHITS PVT.LTD.",
                    "history": [
                        {
                            "regulatoryAction": "PERSONS DISQUALIFIED FROM DIRECTORSHIP FOR THE PERIOD 01-NOV-2016 TO 31-OCT-2021 08-SEP-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "SIGNAL CHITS PVT.LTD.",
                            "regulatoryCharges": "DID NOT FILE FINANCIAL STATEMENTS OR ANNUAL RETURNS FOR ANY CONTINUOUS PERIOD OF 3 FINANCIAL YEARS"
                        }
                    ],
                    "persons": [
                        {
                            "regulatoryAction": "PERSONS DISQUALIFIED FROM DIRECTORSHIP FOR THE PERIOD 01-NOV-2016 TO 31-OCT-2021 08-SEP-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "FESTO KOODALY RAPPAI",
                            "regulatoryCharges": "DID NOT FILE FINANCIAL STATEMENTS OR ANNUAL RETURNS FOR ANY CONTINUOUS PERIOD OF 3 FINANCIAL YEARS"
                        },
                        {
                            "regulatoryAction": "PERSONS DISQUALIFIED FROM DIRECTORSHIP FOR THE PERIOD 01-NOV-2016 TO 31-OCT-2021 08-SEP-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "URUVATH SHAJU",
                            "regulatoryCharges": "DID NOT FILE FINANCIAL STATEMENTS OR ANNUAL RETURNS FOR ANY CONTINUOUS PERIOD OF 3 FINANCIAL YEARS"
                        },
                        {
                            "regulatoryAction": "PERSONS DISQUALIFIED FROM DIRECTORSHIP FOR THE PERIOD 01-NOV-2016 TO 31-OCT-2021 08-SEP-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "URUVATH SHAJU",
                            "regulatoryCharges": "DID NOT FILE FINANCIAL STATEMENTS OR ANNUAL RETURNS FOR ANY CONTINUOUS PERIOD OF 3 FINANCIAL YEARS"
                        }
                    ]
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "61.90"
            },
            {
                "scores": {
                    "nameMatch": "60.49",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "code": "C0077730",
                    "name": "SIGNAL PROCCESSING PVT.LTD.",
                    "history": [
                        {
                            "regulatoryAction": "PROSECUTION UNDER SECTION 220(3) & SECTION 162 OF COMPANIES ACT: PROCEEDINGS STOPPED FOR WANT OF CORRECT ADDRESS 30-JUL-2008",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "SIGNAL PROCCESSING PVT.LTD.",
                            "regulatoryCharges": "DEFAULT IN FILING OF COPIES OF BALANCE SHEET, ETC. WITH THE REGISTRAR (SECTION 220) DEFAULT IN FILING ANNUAL RETURNS (SECTION 159) DID NOT COMPLY WITH PROVISIONS REGARDING CERTIFICATE TO BE ANNEXED WITH ANNUAL RETURN (SECTION 161)"
                        }
                    ],
                    "persons": [
                        {
                            "regulatoryAction": "PROSECUTION UNDER SECTION 220(3) & SECTION 162 OF COMPANIES ACT: PROCEEDINGS STOPPED FOR WANT OF CORRECT ADDRESS 30-JUL-2008",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "K.KRISHNA MOHAN",
                            "regulatoryCharges": "DEFAULT IN FILING OF COPIES OF BALANCE SHEET, ETC. WITH THE REGISTRAR (SECTION 220) DEFAULT IN FILING ANNUAL RETURNS (SECTION 159) DID NOT COMPLY WITH PROVISIONS REGARDING CERTIFICATE TO BE ANNEXED WITH ANNUAL RETURN (SECTION 161)"
                        },
                        {
                            "regulatoryAction": "PROSECUTION UNDER SECTION 220(3) & SECTION 162 OF COMPANIES ACT: PROCEEDINGS STOPPED FOR WANT OF CORRECT ADDRESS 30-JUL-2008",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "K.SANTHA KUMARI",
                            "regulatoryCharges": "DEFAULT IN FILING OF COPIES OF BALANCE SHEET, ETC. WITH THE REGISTRAR (SECTION 220) DEFAULT IN FILING ANNUAL RETURNS (SECTION 159) DID NOT COMPLY WITH PROVISIONS REGARDING CERTIFICATE TO BE ANNEXED WITH ANNUAL RETURN (SECTION 161)"
                        }
                    ]
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "60.49"
            },
            {
                "scores": {
                    "nameMatch": "68.36",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "code": "C0130253",
                    "name": "SIGNET VINIMAY PVT.LTD.",
                    "history": [
                        {
                            "regulatoryAction": "DEBARRED / RESTRAINED FROM ASSOCIATING WITH / ACCESSING CAPITAL MARKET / INTERMEDIARIES FROM 19-DEC-2014 TILL FURTHER ORDERS DEBARRED/RESTRAINED FROM BUYING/SELLING/DEALING/IPOS IN SECURITIES/SPECIFIED SCRIPS DIRECTLY/INDIRECTLY FROM 19-DEC-2014 TILL FURTHER ORDERS 19-DEC-2014",
                            "furtherDevelopments": "SEBI VIDE ITS ORDER DATED 26/08/2016 CONFIRMED ITS DIRECTIONS ISSUED VIDE ITS AD INTERIM EX-PARTE ORDER DATED 19/12/2014 EXCEPT THAT NOTICEES CAN: A) ENTER INTO DELIVERY BASED TRANSACTIONS IN CASH SEGMENT IN SECURITIES COVERED IN NSE NIFTY 500 INDEX SCRIPS AND / OR S&P BSE 500 SCRIPS B) SUBSCRIBE TO UNITS OF MUTUAL FUNDS INCLUDING THROUGH SIP AND REDEEM THE UNITS OF MUTUAL FUNDS SO SUBSCRIBED C) DEAL IN DEBT/GOVERNMENT SECURITIES D) INVEST IN ETF E) AVAIL THE BENEFITS OF CORPORATE ACTIONS LIKE RIGHTS ISSUE, BONUS ISSUE, STOCK SPLIT, DIVIDEND, ETC. F) TENDER THE SHARES LYING IN THEIR DEMAT ACCOUNT IN ANY OPEN OFFER/DELISTING OFFER UNDER THE RELEVANT REGULATIONS OF SEBI. SEBI ALLOWED THEM FURTHER RELAXATIONS/RELIEFS A) THEY ARE PERMITTED TO SELL THE SECURITIES LYING IN THEIR DEMAT ACCOUNTS AS ON THE DATE OF THE INTERIM ORDER, OTHER THAN THE SHARES OF THE COMPANIES WHICH ARE SUSPENDED FROM TRADING BY THE CONCERNED STOCK EXCHANGE, IN ORDERLY MANNER UNDER THE SUPERVISION OF THE STOCK EXCHANGES SO AS NOT TO DISTURB THE MARKET EQUILIBRIUM AND DEPOSIT THE SALE PROCEEDS IN INTEREST BEARING ESCROW ACCOUNT WITH A NATIONALIZED BANK B) THEY MAY DEAL WITH OR UTILIZE THE SALE PROCEEDS LYING IN THE ESCROW ACCOUNT UNDER THE SUPERVISION OF THE CONCERNED STOCK EXCHANGE",
                            "competentAuthority": "SEBI",
                            "name": "SIGNET VINIMAY PVT.LTD.",
                            "regulatoryCharges": "INDULGED IN CREATION OF ARTIFICIAL MARKET AND PRICE MANIPULATION THROUGH PREFERENTIAL ALLOTMENT OF EQUITY SHARES AT PREMIUM, ANNOUNCEMENT OF STOCK SPILT IN SCRIP OF RADFORD GLOBAL LTD."
                        },
                        {
                            "regulatoryAction": "DEBARRED / RESTRAINED FROM ASSOCIATING WITH / ACCESSING CAPITAL MARKET / INTERMEDIARIES FROM 17-APR-2015 TILL FURTHER ORDERS DEBARRED/RESTRAINED FROM BUYING/SELLING/DEALING/IPOS IN SECURITIES/SPECIFIED SCRIPS DIRECTLY/INDIRECTLY FROM 17-APR-2015 TILL FURTHER ORDERS 17-APR-2015",
                            "furtherDevelopments": "SEBI VIDE ITS ORDER DATED 05/10/2017 REVOKED ITS DIRECTIONS ISSUED VIDE ITS CONFIRMATORY ORDERS DATED 12/10/2015, 21/10/2015, 13/04/2016, 05/07/2016 AND 26/08/2016 SEBI VIDE ITS ORDER DATED 26/08/2016 CONFIRMED ITS DIRECTIONS ISSUED VIDE ITS AD INTERIM EX-PARTE ORDER DATED 17/04/2015 EXCEPT THAT NOTICEES CAN: A) ENTER INTO DELIVERY BASED TRANSACTIONS IN CASH SEGMENT IN SECURITIES COVERED IN NSE NIFTY 500 INDEX SCRIPS AND / OR S&P BSE 500 SCRIPS B) SUBSCRIBE TO UNITS OF MUTUAL FUNDS INCLUDING THROUGH SIP AND REDEEM THE UNITS OF MUTUAL FUNDS SO SUBSCRIBED C) DEAL IN DEBT/GOVERNMENT SECURITIES D) INVEST IN ETF E) AVAIL THE BENEFITS OF CORPORATE ACTIONS LIKE RIGHTS ISSUE, BONUS ISSUE, STOCK SPLIT, DIVIDEND, ETC. F) TENDER THE SHARES LYING IN THEIR DEMAT ACCOUNT IN ANY OPEN OFFER/DELISTING OFFER UNDER THE RELEVANT REGULATIONS OF SEBI. SEBI ALLOWED THEM FURTHER RELAXATIONS/RELIEFS A) THEY ARE PERMITTED TO SELL THE SECURITIES LYING IN THEIR DEMAT ACCOUNTS AS ON THE DATE OF THE INTERIM ORDER, OTHER THAN THE SHARES OF THE COMPANIES WHICH ARE SUSPENDED FROM TRADING BY THE CONCERNED STOCK EXCHANGE, IN ORDERLY MANNER UNDER THE SUPERVISION OF THE STOCK EXCHANGES SO AS NOT TO DISTURB THE MARKET EQUILIBRIUM AND DEPOSIT THE SALE PROCEEDS IN INTEREST BEARING ESCROW ACCOUNT WITH A NATIONALIZED BANK B) THEY MAY DEAL WITH OR UTILIZE THE SALE PROCEEDS LYING IN THE ESCROW ACCOUNT UNDER THE SUPERVISION OF THE CONCERNED STOCK EXCHANGE",
                            "competentAuthority": "SEBI",
                            "name": "SIGNET VINIMAY PVT.LTD.",
                            "regulatoryCharges": "MISUSED STOCK EXCHANGE SYSTEM TO GENERATE FICTITIOUS LONG-TERM CAPITAL GAINS (LTCG) TO CONVERT UNACCOUNTED INCOME INTO ACCOUNTED ONE WITH NO PAYMENT OF TAXES AS LTCG IS TAX EXEMPT IN MATTER OF MISHKA FINANCE & TRADING LTD."
                        },
                        {
                            "regulatoryAction": "DEBARRED / RESTRAINED FROM ASSOCIATING WITH / ACCESSING CAPITAL MARKET / INTERMEDIARIES FROM 08-MAY-2015 TILL FURTHER ORDERS DEBARRED/RESTRAINED FROM BUYING/SELLING/DEALING/IPOS IN SECURITIES/SPECIFIED SCRIPS DIRECTLY/INDIRECTLY FROM 08-MAY-2015 TILL FURTHER ORDERS 08-MAY-2015",
                            "furtherDevelopments": "SEBI VIDE ITS ORDER DATED 19/09/2017 REVOKED ITS DIRECTIONS ISSUED VIDE ITS CONFIRMATORY ORDERS DATED 02/06/2016, 05/07/2016, 22/08/2016 AND 02/06/2017 SEBI VIDE ITS ORDER DATED 22/08/2016 CONFIRMED ITS DIRECTIONS ISSUED VIDE ITS AD INTERIM EX-PARTE ORDER DATED 08/05/2015 EXCEPT THAT NOTICEES CAN: A) ENTER INTO DELIVERY BASED TRANSACTIONS IN CASH SEGMENT IN SECURITIES COVERED IN NSE NIFTY 500 INDEX SCRIPS AND / OR S&P BSE 500 SCRIPS B) SUBSCRIBE TO UNITS OF MUTUAL FUNDS INCLUDING THROUGH SIP AND REDEEM THE UNITS OF MUTUAL FUNDS SO SUBSCRIBED C) DEAL IN DEBT/GOVERNMENT SECURITIES D) INVEST IN ETF E) AVAIL THE BENEFITS OF CORPORATE ACTIONS LIKE RIGHTS ISSUE, BONUS ISSUE, STOCK SPLIT, DIVIDEND, ETC. F) TENDER THE SHARES LYING IN THEIR DEMAT ACCOUNT IN ANY OPEN OFFER/DELISTING OFFER UNDER THE RELEVANT REGULATIONS OF SEBI. SEBI ALLOWED THEM FURTHER RELAXATIONS/RELIEFS A) THEY ARE PERMITTED TO SELL THE SECURITIES LYING IN THEIR DEMAT ACCOUNTS AS ON THE DATE OF THE INTERIM ORDER, OTHER THAN THE SHARES OF THE COMPANIES WHICH ARE SUSPENDED FROM TRADING BY THE CONCERNED STOCK EXCHANGE, IN ORDERLY MANNER UNDER THE SUPERVISION OF THE STOCK EXCHANGES SO AS NOT TO DISTURB THE MARKET EQUILIBRIUM AND DEPOSIT THE SALE PROCEEDS IN AN INTEREST BEARING ESCROW ACCOUNT WITH A NATIONALIZED BANK B) THEY MAY DEAL WITH OR UTILIZE THE SALE PROCEEDS LYING IN THE ESCROW ACCOUNT UNDER THE SUPERVISION OF THE CONCERNED STOCK EXCHANGE",
                            "competentAuthority": "SEBI",
                            "name": "SIGNET VINIMAY PVT.LTD.",
                            "regulatoryCharges": "MISUSED STOCK EXCHANGE SYSTEM TO GENERATE FICTITIOUS LONG-TERM CAPITAL GAINS (LTCG) TO CONVERT UNACCOUNTED INCOME INTO ACCOUNTED ONE WITH NO PAYMENT OF TAXES AS LTCG IS TAX EXEMPT IN MATTER OF PINE ANIMATION LTD."
                        },
                        {
                            "regulatoryAction": "DEBARRED / RESTRAINED FROM ASSOCIATING WITH / ACCESSING CAPITAL MARKET / INTERMEDIARIES FROM 29-MAR-2016 TILL FURTHER ORDERS DEBARRED/RESTRAINED FROM BUYING/SELLING/DEALING/IPOS IN SECURITIES/SPECIFIED SCRIPS DIRECTLY/INDIRECTLY FROM 29-MAR-2016 TILL FURTHER ORDERS 29-MAR-2016",
                            "furtherDevelopments": "SEBI VIDE ITS ORDER DATED 21/09/2017 REVOKED ITS DIRECTIONS ISSUED VIDE ITS CONFIRMATORY ORDERS DATED 15/06/2016, 30/09/2016, 21/10/2016, 27/10/2016 AND 13/07/2017 SEBI VIDE ITS ORDER DATED 15/06/2016 CONFIRMED THE DIRECTIONS ISSUED VIDE ITS AD-INTERIM EX-PARTE ORDER DATED 29/03/2016",
                            "competentAuthority": "SEBI",
                            "name": "SIGNET VINIMAY PVT.LTD.",
                            "regulatoryCharges": "INDULGED IN CREATION OF ARTIFICIAL MARKET AND PRICE MANIPULATION IN SCRIP OF KAILASH AUTO FINANCE LTD. MISUSED STOCK EXCHANGE SYSTEM TO GENERATE FICTITIOUS LONG-TERM CAPITAL GAINS (LTCG) TO CONVERT UNACCOUNTED INCOME INTO ACCOUNTED ONE WITH NO PAYMENT OF TAXES AS LTCG IS TAX EXEMPT IN MATTER OF KAILASH AUTO FINANCE LTD."
                        },
                        {
                            "regulatoryAction": "IMPOSED PENALTY 06-MAR-2013",
                            "furtherDevelopments": "SEBI VIDE ITS NOTICE DATED 28/10/2014 DIRECTED ALL THE BANKS IN INDIA AND/OR NSDL/CDSL TO 1. ATTACH ALL THE ACCOUNTS BY WHATEVER NAME CALLED INCLUDING LOCKERS EITHER SINGLY OR JOINTLY WITH ANY PERSON/S AND ALL OTHER AMOUNT/PROCEEDS DUE OR MAY BECOME DUE OR ANY MONEY HELD OR MAY SUBSEQUENTLY HOLD FOR ON ACCOUNT OF THE DEFAULTERS AND 2. NOT TO DEBIT ANY AMOUNT IN THE SAID ACCOUNT/S.HOWEVER CREDITS, IF ANY, INTO THE ACCOUNT MAY BE ALLOWED SAT: APPEAL DISMISSED WITH NO ORDER AS TO COSTS. FURTHER DIRECTED APPELLANTS TO DEPOSIT THE MONETARY PENALTY WITHIN A PERIOD OF TWO MONTHS",
                            "competentAuthority": "SEBI",
                            "name": "SIGNET VINIMAY PVT.LTD.",
                            "regulatoryCharges": "INDULGED IN CREATION OF ARTIFICIAL MARKET AND PRICE MANIPULATION THROUGH OFF-MARKET/ CIRCULAR / SYNCHRONIZED AND REVERSAL OF TRADE TRANSACTIONS IN SCRIP OF RICH UNIVERSE NETWORK LTD."
                        }
                    ],
                    "persons": []
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "68.36"
            },
            {
                "scores": {
                    "nameMatch": "62.96",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "code": "C0033014",
                    "name": "SIGNET STEELS LTD.",
                    "history": [
                        {
                            "regulatoryAction": "POSSESSION NOTICE- RS.93848594.46 STATE BANK OF INDIA,VISAKHAPATNAM 10-SEP-2005",
                            "furtherDevelopments": "",
                            "competentAuthority": "BANKS",
                            "name": "SIGNET STEELS LTD.",
                            "regulatoryCharges": "DEFAULT IN REPAYMENT OF LOANS"
                        }
                    ],
                    "persons": []
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "62.96"
            },
            {
                "scores": {
                    "nameMatch": "62.22",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "code": "C0156284",
                    "name": "SIKOZY REALTORS LTD.",
                    "history": [
                        {
                            "regulatoryAction": "PUT UP ON BSE WEBSITE FOR PUBLIC NOTICE 31-MAR-2015",
                            "furtherDevelopments": "NOT APPEARING IN THE LIST FOR THE QUARTER ENDED 30-JUNE-2015",
                            "competentAuthority": "BSE",
                            "name": "SIKOZY REALTORS LTD.",
                            "regulatoryCharges": "DID NOT SUBMIT SHAREHOLDING PATTERN UNDER PROVISIONS OF CLAUSE 35 FOR THE QUARTER ENDED 31-MARCH-2015"
                        },
                        {
                            "regulatoryAction": "PUT UP ON BSE WEBSITE FOR PUBLIC NOTICE 30-JUN-2015",
                            "furtherDevelopments": "NOT APPEARING IN THE LIST FOR THE QUARTER ENDED 30-SEP-2015",
                            "competentAuthority": "BSE",
                            "name": "SIKOZY REALTORS LTD.",
                            "regulatoryCharges": "DID NOT SUBMIT CORPORATE GOVERNANCE REPORT FOR THE QUARTER ENDED 30-JUNE-2015"
                        },
                        {
                            "regulatoryAction": "DIRECTED TRADING MEMBERS TO DO THE DUE DILIGENCE ON THE BASIS OF AUDITORS CERTIFICATE ALONG WITH THE DOCUMENTS, AS MENTIONED IN THE ORDER AND SUBMIT A REPORT TO THE EXCHANGE BY AUGUST 31, 2017 DIRECTED THAT THE TRADING IN ALL SUCH LISTED SECURITIES SHALL BE PLACED IN STAGE VI OF THE GRADED SURVEILLANCE MEASURE (GSM) WITH IMMEDIATE EFFECT. IF ANY LISTED COMPANY OUT OF THE SAID LIST IS ALREADY IDENTIFIED UNDER ANY STAGE OF GSM, IT SHALL ALSO BE MOVED TO GSM STAGE VI DIRECTLY DIRECTED THAT THE SHARES HELD BY THE PROMOTERS AND DIRECTORS IN SUCH LISTED COMPANIES SHALL BE ALLOWED TO BE TRANSFERRED BY DEPOSITORIES ONLY UPON VERIFICATION BY CONCERNED EXCHANGES AND THEY SHALL NOT BE ALLOWED TO TRANSACT IN THE SECURITY EXCEPT TO BUY SECURITIES IN THE SAID LISTED COMPANY UNTIL VERIFICATION OF CREDENTIAL / FUNDAMENTAL BY EXCHANGES IS COMPLETED DIRECTED EXCHANGES TO INITIATE A PROCESS OF VERIFYING THE CREDENTIALS/FUNDAMENTALS OF SUCH COMPANIES ON VERIFICATION, IF EXCHANGES DO NOT FIND APPROPRIATE CREDENTIALS / FUNDAMENTALS ABOUT EXISTENCE OF THE COMPANY, EXCHANGES SHALL INITIATE THE PROCEEDING FOR COMPULSORY DELISTING AGAINST THE COMPANY, AND THE SAID COMPANY SHALL NOT BE PERMITTED TO DEAL IN ANY SECURITY ON EXCHANGE PLATFORM AND ITS HOLDING IN ANY DEPOSITORY ACCOUNT SHALL BE FROZEN TILL SUCH DELISTING PROCESS IS COMPLETED 07-AUG-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "SEBI",
                            "name": "SIKOZY REALTORS LTD.",
                            "regulatoryCharges": "DID NOT COMPLY WITH SEBI LAWS / REGULATIONS"
                        }
                    ],
                    "persons": []
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "62.22"
            },
            {
                "scores": {
                    "nameMatch": "60.00",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "code": "C0204998",
                    "name": "SIGNET AUTHENTICATORS PVT.LTD.",
                    "history": [
                        {
                            "regulatoryAction": "PERSONS DISQUALIFIED FROM DIRECTORSHIP FOR THE PERIOD 01-NOV-2016 TO 31-OCT-2021 15-SEP-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "SIGNET AUTHENTICATORS PVT.LTD.",
                            "regulatoryCharges": "DID NOT FILE FINANCIAL STATEMENTS OR ANNUAL RETURNS FOR ANY CONTINUOUS PERIOD OF 3 FINANCIAL YEARS"
                        }
                    ],
                    "persons": [
                        {
                            "regulatoryAction": "PERSONS DISQUALIFIED FROM DIRECTORSHIP FOR THE PERIOD 01-NOV-2016 TO 31-OCT-2021 15-SEP-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "KUNAL KHATRI",
                            "regulatoryCharges": "DID NOT FILE FINANCIAL STATEMENTS OR ANNUAL RETURNS FOR ANY CONTINUOUS PERIOD OF 3 FINANCIAL YEARS"
                        },
                        {
                            "regulatoryAction": "PERSONS DISQUALIFIED FROM DIRECTORSHIP FOR THE PERIOD 01-NOV-2016 TO 31-OCT-2021 15-SEP-2017",
                            "furtherDevelopments": "",
                            "competentAuthority": "MCA",
                            "name": "SURINDER SINGH",
                            "regulatoryCharges": "DID NOT FILE FINANCIAL STATEMENTS OR ANNUAL RETURNS FOR ANY CONTINUOUS PERIOD OF 3 FINANCIAL YEARS"
                        }
                    ]
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "60.00"
            }
        ],
        "nbfcBlacklisted": [
            {
                "scores": {
                    "nameMatch": "61.11",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "companyName": "SIGNET SUPPLIERS PVT.LTD",
                    "address": "SCO 140-141 SECTOR-34A CHANDIGARH CHANDIGARH 160034",
                    "city": "CHANDIGARH",
                    "state": "CHANDIGARH",
                    "pincode": "160034",
                    "email": "",
                    "fax": ""
                },
                "relevance": [
                    "AML"
                ],
                "overallScore": "61.11"
            }
        ],
        "MCAdefaulterEntities": [
            {
                "scores": {
                    "nameMatch": "58.89",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "companyName": "SIGNIN SIGN TECHNOLOGIES PRIVATE LIMITED",
                    "cin": "U72200TN2007PTC061914",
                    "dateOfRejection": "23/04/2016"
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "58.89"
            },
            {
                "scores": {
                    "nameMatch": "59.06",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "companyName": "SIGNET INFRATECH INDIA PRIVATE LIMITED",
                    "cin": "U45200DL2008FTC179441",
                    "dateOfRejection": "23/04/2016"
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "59.06"
            },
            {
                "scores": {
                    "nameMatch": "59.06",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "companyName": "SAKET SIGNAL SOLUTIONS PRIVATE LIMITED",
                    "cin": "U72200TG2007PTC052812",
                    "dateOfRejection": "23/04/2016"
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "59.06"
            },
            {
                "scores": {
                    "nameMatch": "58.39",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "companyName": "SIGNAL TECHNICAL SERVICES INDIA PRIVATE LIMITED",
                    "cin": "U74200AP2008PTC057644",
                    "dateOfRejection": "23/04/2016"
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "58.39"
            },
            {
                "scores": {
                    "nameMatch": "60.89",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "companyName": "M K SIGNS PRIVATE LIMITED",
                    "cin": "U25209DL2006PTC151120",
                    "dateOfRejection": "23/04/2016"
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "60.89"
            },
            {
                "scores": {
                    "nameMatch": "58.89",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "companyName": "SIGNE SOFTWARE SOLUTIONS PRIVATE LIMITED",
                    "cin": "U72300TG2008PTC058034",
                    "dateOfRejection": "23/04/2016"
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "58.89"
            },
            {
                "scores": {
                    "nameMatch": "59.60",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "companyName": "SHIVAM SIGN-TECH PRIVATE LIMITED.",
                    "cin": "U74130DL2006PTC148379",
                    "dateOfRejection": "23/04/2016"
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "59.60"
            },
            {
                "scores": {
                    "nameMatch": "50.56",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "companyName": "BALAJI SIGN AND GRAPHICS PRIVATE LIMITED",
                    "cin": "U74899DL2006PTC146839",
                    "dateOfRejection": "23/04/2016"
                },
                "relevance": [
                    "AML",
                    "CFT"
                ],
                "overallScore": "50.56"
            }
        ],
        "UNSanctionsListEntities": [],
        "financialIntelligenceUnitDefaulters": [],
        "dvatDefaulterDealers": [],
        "ofacSDNCriminalEntities": [],
        "usSanctionList": [],
        "nseDefaulters": [],
        "blacklistedNgos": [],
        "fcraCancelled": [],
        "fcraSuspended": [],
        "irdaDefaulters": [],
        "mcxDefaulters": [],
        "cibilDefaulters": [
            {
                "scores": {
                    "nameMatch": "61.35",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "rejected": "0",
                    "title": "",
                    "city": "",
                    "costAmount": "",
                    "rejectComments": "",
                    "borrowerName": "SIGNET PRODUCTS PVT LTD",
                    "stateName": "MAHARASHTRA",
                    "directors": [
                        "NARENDRA ACHYUTRAO KORDE",
                        "ACHYUT NAGORAO KORDE",
                        "VAIDEHI NARENDRA KORDE"
                    ],
                    "registeredAddress": "PLOT NO 16/16A, N-5, SOUTH SECTOR, CIDCO, AURANGABAD, MAHARASHTRA-431003",
                    "bankDefaults": [
                        {
                            "active": "0",
                            "bankNoRecords": "0",
                            "bankName": "ANDHRA BANK",
                            "bankId": "0",
                            "bankTotalAmount": "4147.00",
                            "branchId": "13891",
                            "branchName": "ANDHERI",
                            "branchcode": "",
                            "quarterDateStr": "30/06/2018"
                        },
                        {
                            "active": "0",
                            "bankNoRecords": "0",
                            "bankName": "ANDHRA BANK",
                            "bankId": "0",
                            "bankTotalAmount": "4147.00",
                            "branchId": "13891",
                            "branchName": "ANDHERI",
                            "branchcode": "",
                            "quarterDateStr": "31/12/2018"
                        }
                    ]
                },
                "relevance": [
                    "LENDING",
                    "NONCOMPLIANCE"
                ],
                "overallScore": "61.35"
            },
            {
                "scores": {
                    "nameMatch": "59.26",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "rejected": "0",
                    "title": "",
                    "city": "",
                    "costAmount": "",
                    "rejectComments": "",
                    "borrowerName": "SIGNET CROP SCIENCES INDIA PVT. LTD.",
                    "stateName": "HARYANA",
                    "directors": [
                        "SANDEEP KUMAR KAUSHIK",
                        "PRIYA ANURADHA KAUSHIK"
                    ],
                    "registeredAddress": "522, 1ST FLOOR, NEW GRAIN MARKET, GT ROAD, DELHI",
                    "bankDefaults": [
                        {
                            "active": "0",
                            "bankNoRecords": "0",
                            "bankName": "CANARA BANK",
                            "bankId": "0",
                            "bankTotalAmount": "120.86",
                            "branchId": "23208",
                            "branchName": "KARNAL SPECIALISED ARM BRANCH",
                            "branchcode": "",
                            "quarterDateStr": "31/03/2018"
                        },
                        {
                            "active": "0",
                            "bankNoRecords": "0",
                            "bankName": "CANARA BANK",
                            "bankId": "0",
                            "bankTotalAmount": "120.86",
                            "branchId": "23208",
                            "branchName": "KARNAL SPECIALISED ARM BRANCH",
                            "branchcode": "",
                            "quarterDateStr": "30/06/2018"
                        },
                        {
                            "active": "0",
                            "bankNoRecords": "0",
                            "bankName": "CANARA BANK",
                            "bankId": "0",
                            "bankTotalAmount": "120.86",
                            "branchId": "23208",
                            "branchName": "KARNAL SPECIALISED ARM BRANCH",
                            "branchcode": "",
                            "quarterDateStr": "30/09/2018"
                        },
                        {
                            "active": "0",
                            "bankNoRecords": "0",
                            "bankName": "CANARA BANK",
                            "bankId": "0",
                            "bankTotalAmount": "120.86",
                            "branchId": "23208",
                            "branchName": "KARNAL SPECIALISED ARM BRANCH",
                            "branchcode": "",
                            "quarterDateStr": "31/12/2018"
                        }
                    ]
                },
                "relevance": [
                    "LENDING",
                    "NONCOMPLIANCE"
                ],
                "overallScore": "59.26"
            },
            {
                "scores": {
                    "nameMatch": "53.57",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "rejected": "0",
                    "title": "",
                    "city": "",
                    "costAmount": "",
                    "rejectComments": "",
                    "borrowerName": "DIGITAL SIGN NETWORKS",
                    "stateName": "KERALA",
                    "directors": [
                        "KIRAN P P",
                        "PROPRIETOR",
                        "BABU. K V",
                        "GUARANTOR",
                        "GOWRI.K C",
                        "GUARANTOR",
                        "SAJIK V",
                        "GUARANTOR",
                        "SUMA K. G.",
                        "GUARANTOR",
                        "SABU K.V",
                        "GUARANTOR"
                    ],
                    "registeredAddress": "NO:4/28, 1ST FLOOR, PADINJAREKKARA, PADIYUR, THRISSUR-680122, KERALA",
                    "bankDefaults": [
                        {
                            "active": "0",
                            "bankNoRecords": "0",
                            "bankName": "DHANLAXMI BANK LIMITED",
                            "bankId": "0",
                            "bankTotalAmount": "145.00",
                            "branchId": "17557",
                            "branchName": "THRISSUR MAIN",
                            "branchcode": "",
                            "quarterDateStr": "31/12/2018"
                        }
                    ]
                },
                "relevance": [
                    "LENDING",
                    "NONCOMPLIANCE"
                ],
                "overallScore": "53.57"
            },
            {
                "scores": {
                    "nameMatch": "58.89",
                    "dobMatch": "",
                    "countryMatch": "",
                    "zipcodeMatch": "",
                    "aliasArrayMatch": [],
                    "identificationNumberMatch": "",
                    "searchTextMatch": []
                },
                "details": {
                    "rejected": "0",
                    "title": "",
                    "city": "",
                    "costAmount": "",
                    "rejectComments": "",
                    "borrowerName": "M/S SIGNET CROP SCIENCES INDIA PVT. LTD.",
                    "stateName": "HARYANA",
                    "directors": [
                        "SUDESH KUMAR SHARMA",
                        "PRIYA ANURADHA KAUSHIK"
                    ],
                    "registeredAddress": "522, 1ST FLOOR, NEW GRAIN MARKET, GT ROAD, DELHI",
                    "bankDefaults": [
                        {
                            "active": "0",
                            "bankNoRecords": "0",
                            "bankName": "CANARA BANK",
                            "bankId": "0",
                            "bankTotalAmount": "175.51",
                            "branchId": "25069",
                            "branchName": "KARNAL ANAJMANDI",
                            "branchcode": "",
                            "quarterDateStr": "31/12/2017"
                        }
                    ]
                },
                "relevance": [
                    "LENDING",
                    "NONCOMPLIANCE"
                ],
                "overallScore": "58.89"
            }
        ],
        "sebiIlegalMoneyList": []
    }
}
```
{% endtab %}
{% endtabs %}

### **Valid Category/Relevance List**

1 ) AML\
2 ) CFT\
3 ) LENDING\
4 ) NONCOMPLIANCE

### **Negative Databases Present With Us**

**Individual**

1 ) blacklistedIndividuals\
2 ) politicallyExposedPerson\
3 ) MCAdefaulterdirectors\
4 ) MCAdormantdirectors\
5 ) bseDefaulters\
6 ) niaMostWanted\
7 ) missingInterpol\
8 ) blacklistedDoctors\
9 ) abscondingCriminals\
10 ) mseiDefaulters\
11 ) ofacSDNCriminalIndividuals\
12 ) crimeBureauMostWanted

**Entity**

1 ) blacklistedEntities\
2 ) usSanctionList\
3 ) nbfcBlacklisted\
4 ) MCAdefaulterEntities\
5 ) nseDefaulters\
6 ) sebiIlegalMoneyList\
7 ) blacklistedNgos\
8 ) fcraCancelled\
9 ) fcraSuspended\
10 ) irdaDefaulters\
11 ) mcxDefaulters\
12 ) financialIntelligenceUnitDefaulters\
13 ) dvatDefaulterDealers\
14 ) ofacSDNCriminalEntities\
15 ) cibilDefaulters

### HTTP Response Codes

| Status Code | Error Message               | Possible Fix                   |
| ----------- | --------------------------- | ------------------------------ |
| 200         | Successful                  | Nothing to fix                 |
| 400         | Missing or Invalid data     | Check all the input parameters |
| 401         | Authorization Required      | Check Authorization Header     |
| 404         | No method to handle request | Check URL endpoint of API      |
| 422         | Unprocessable Entity        | Notify our support team        |
