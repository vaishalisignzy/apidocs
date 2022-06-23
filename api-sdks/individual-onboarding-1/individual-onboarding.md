# Input Verification Data(t)

This API is used to incorporate the particulars and details of the new client/individual and records the basic details in the system like name, id proof details, address and other demographic information. Upon successful integration, it provides a unique request ID to the user for future use.

You will need to login before sending request. You are required to pass the access token received from the login call, as authorization header in the Individual Onboarding Save Request along with essentials and task. So, in this request you will pass all the data which need to be verified by using signzy verification engine.



Use the following exchange parameters for Individual Onboarding Save Request

```
// Data exchange
For Test Credentials
// POST :: https://preproduction.signzy.tech/api/v2/patrons/..your-patron-id../individualonboardings
For Production Credentials
// POST :: https://signzy.tech/api/v2/patrons/...patronID.../individualonboardings

// patron ID is returned as userId parameter of login request.
// Headers
{
'Authorization': '...access token (returned as id field of login request)...',
'Content-type': 'application/json'
}

// Request data
{
	"task": "save",
	"essentials": {
        "callbackUrl": ".......call back url.....",
		"inputObj": {
			"idCards": [{
					"type": "aadhaar/passport/dl/pan/voterid",
					"images": [],
					"idNo": "",
					"name": "",
					"dob": "",
					"address": "",
					"gender": "",
					"age": "",
					"nationality": "",
					"issueDate": "",
					"state": "",
					"purpose": ["POI", "POA"],
					"verify": "true / false"
				}
			],
			"others": [{
				"images": [],
				"fields": {}
			}],
			"video": {
				"url": "",
				"matchImage": "",
				"signzyVerifiableString": "",
                "seconds" : ["...time at which face was tracked at frontend..."]
                 //Example   "seconds": ["00:00:01","00:00:04","00:00:08"]
			},
			"contract": {
				"url ": "",
				"name": "",
				"aadhaarNumber": ""
			},
			"documents": [{
					"type": "bankAccountVerification",
					"beneficiaryMobile": "",
					"beneficiaryAccount": "",
					"beneficiaryName": "",
					"beneficiaryIFSC": "",
					"bankName": "",
					"branchName": "",
					"images": [],
					"verify": "true / false"
				},
				{
					"type": "cheque",
					"beneficiaryMobile": "",
					"beneficiaryAccount": "",
					"beneficiaryName": "",
					"beneficiaryIFSC": "",
					"bankName": "",
					"branchName": "",
					"images": [],
					"verify ": "true/false"
				}

			],
			"info": {
				"name ": "",
				"permanentAddress": "",
				"emailId": "",
				"phone": "",
				"dob": "",
				"communicationAddress": ""
			}
		}
	}

}
// Output response
{
    "result": {
        "requestId": "..requestId...."
    }
}
```



### Input Field Description

#### IDcard Block

| SL NO | FIELD NAME  | DESCRIPTION                                                                                             | VALUE (COMPULSORY OR OPTIONAL)               |
| ----- | ----------- | ------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| 1     | type        | Type of ID proof (aadhaar/passport/dl/pan/voterid)                                                      | Compulsory                                   |
| 2     | idNo        | ID number for all IDcard of individual (aadhaar/passport/dl/pan/voterid)                                | Compulsory                                   |
| 3     | images      | Image url of IDcard (aadhaar/passport/dl/pan/voterid)                                                   | Optional                                     |
| 4     | name        | Name of the individual (aadhaar/passport/dl/pan/voterid)                                                | Compulsory                                   |
| 5     | dob         | Value for DOB(dd/mm/yyyy)                                                                               | Optional(only compulsory for Aadhaar and DL) |
| 6     | address     | Address of individual                                                                                   | Optional                                     |
| 7     | gender      | Gender of individual                                                                                    | Optional                                     |
| 8     | age         | Age of individual                                                                                       | Optional                                     |
| 9     | nationality | Nationality of individual                                                                               | Optional                                     |
| 10    | issueDate   | IssueDate of IDcard                                                                                     | Optional(only compulsory for DL)             |
| 11    | purpose     | Uploaded documents purpose \[POA/POI/POA & POI]                                                         | Compulsory                                   |
| 12    | verify      | Records to be verified by verification engine or not (true/false) as string value Ex: "true" or "false" | Compulsory                                   |
| 13    | callbackUrl | If the Callback URL is provided then whole response in JSON format will be posted to that URL.          | Optional                                     |

#### Documents Block

**Cheque**

| SL NO | FIELD NAME         | DESCRIPTION                                                                                             | VALUE (COMPULSORY OR OPTIONAL) |
| ----- | ------------------ | ------------------------------------------------------------------------------------------------------- | ------------------------------ |
| 1     | type               | cheque                                                                                                  | Compulsory                     |
| 2     | beneficiaryMobile  | Mobile no of individual which is connected to bank account                                              | Optional                       |
| 3     | beneficiaryAccount | Account no of individual                                                                                | Optional                       |
| 4     | beneficiaryName    | Name of the individual registered to that account                                                       | Optional                       |
| 5     | beneficiaryIFSC    | BankIFSC code in which the account is registered                                                        | Optional                       |
| 6     | bankName           | Bank name in which the account is registered                                                            | Optional                       |
| 7     | branchName         | Branch name of the Bank in which the account is registered                                              | Optional                       |
| 8     | images             | Image of cheque                                                                                         | Optional                       |
| 9     | verify             | Records to be verified by verification engine or not (true/false) as string value Ex: "true" or "false" | Compulsory                     |

**Bank Account Verification**

| SL NO | FIELD NAME         | DESCRIPTION                                                                                             | VALUE (COMPULSORY OR OPTIONAL) |
| ----- | ------------------ | ------------------------------------------------------------------------------------------------------- | ------------------------------ |
| 1     | type               | bankAccountVerification                                                                                 | Compulsory                     |
| 2     | beneficiaryMobile  | Mobile no of individual which is connected to bank account                                              | Optional                       |
| 3     | beneficiaryAccount | Account no of individual                                                                                | Compulsory                     |
| 4     | beneficiaryName    | Name of the individual registered to that account                                                       | Optional                       |
| 5     | beneficiaryIFSC    | BankIFSC code in which the account is registered                                                        | Compulsory                     |
| 6     | bankName           | Bank name in which the account is registered                                                            | Optional                       |
| 7     | branchName         | Branch name of the Bank in which the account is registered                                              | Optional                       |
| 9     | verify             | Records to be verified by verification engine or not (true/false) as string value Ex: "true" or "false" | Compulsory                     |

#### Video Block

| SL NO | FIELD NAME             | DESCRIPTION                                     | VALUE (COMPULSORY OR OPTIONAL) |
| ----- | ---------------------- | ----------------------------------------------- | ------------------------------ |
| 1     | url                    | url of video                                    | Compulsory                     |
| 2     | matchImage             | Matches the image of the person who is in video | Compulsory                     |
| 3     | signzyVerifiableString | Its the string told in video                    | Compulsory                     |
| 4     | seconds                | Time value for extracting image from the video  | Optional                       |

#### Contract

| SL NO | FIELD NAME    | DESCRIPTION                           | VALUE (COMPULSORY OR OPTIONAL) |
| ----- | ------------- | ------------------------------------- | ------------------------------ |
| 1     | url           | url of contract                       | Compulsory                     |
| 2     | name          | Name of the contract holder           | Compulsory                     |
| 3     | aadhaarNumber | Aadhaar number of the contract holder | Compulsory                     |

#### Others Block

| SL NO | FIELD NAME | DESCRIPTION                    | VALUE (COMPULSORY OR OPTIONAL) |
| ----- | ---------- | ------------------------------ | ------------------------------ |
| 1     | images     | Any document of individual     | Optional                       |
| 2     | fields     | Values of fields in this image | Optional                       |

#### Info Block

| SL NO | FIELD NAME           | DESCRIPTION                       | VALUE (COMPULSORY OR OPTIONAL) |
| ----- | -------------------- | --------------------------------- | ------------------------------ |
| 1     | name                 | Name of the user                  | Compulsory                     |
| 2     | permanentAddress     | Permanent Address of the user     | Compulsory                     |
| 3     | emailId              | Email-Id of the user              | Compulsory                     |
| 4     | phone                | Phone of the user                 | Compulsory                     |
| 5     | communicationAddress | Communication Address of the user | Compulsory                     |

#### Cross Check Block

| SL NO | FIELD NAME       | DESCRIPTION                   | VALUE (COMPULSORY OR OPTIONAL) |
| ----- | ---------------- | ----------------------------- | ------------------------------ |
| 1     | name             | Name of the user              | Compulsory                     |
| 2     | permanentAddress | Permanent Address of the user | Compulsory                     |

