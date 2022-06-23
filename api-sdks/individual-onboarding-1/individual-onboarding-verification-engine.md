# Individual Onboarding Verification Engine

**Introduction**

The Individual Onboarding Verification Engine is a Signzy product that is designed for a safe and secure process of incorporating a new application for a new client into the existing system. The purpose of this service is to ensure that the individual client faces minimum concern and a hassle-free use of our services in the future.



Before going to use our Verification Engine of Individual Onboarding you will require the customer’s demographic, ID and other data. You might have already used our extraction APIs to make that data collection simpler at the front end. If you haven’t , you should surely check out Extraction Section, this will surely make the customer journey simpler.

Now once we get the required data, we can pass this into our verification engine. The goal of this engine is to allow a complete customer data to be submitted at one end point and response received against various checks such as ID checks, Image forgery, Due diligence etc. Each of these functionalities has been described in detail in the following section :

#### Product Flow

1. A front end application (Web or Mobile) collects customer data in form of ID Images, Video and demographic data
2. This complete application with several input parameters is taken as JSON into the verification engine, the engine after making verifications and intelligent checks returns back an output in JSON form.
3. This output JSON is made available to a dashboard. This dashboard can based on internal rules either approve users or allow operations personnel to manually accept or reject new users.
4. For the application there are two more options of updating the request and deleting the request data.
   * You may want to use an update request when some extra data is required from the end customer later.
   * You may choose to delete the data once your onboarding workflow with the end-user is completed.

#### Integration Flow

**Logging in**

You would have understood logging in by now if you would have used our other APIs. In case you are only integrating Individual Onboarding Verification Engine you can understand logging in from [Authentication ](https://docs-staging.signzy.tech/)section

**Sending a request**

Both Input request and Output JSON have lot of fields and parameters, which can be confusing. The way this has been structured is in blocks. If you are integrating only one or two of the functionality you can only focus on your block and comment out or delete other blocks.

We have put the complete request and response JSON, in two separate sections - Input Verification data and Get data. You can use them.

But let us first explain the different blocks and how they can help you achieve your goal of faster digital onboarding for customer

**Basic Information Block**

This block contains basic information of the customer that you might have gathered through forms or earlier customer interaction such as name, email etc. This data is useful when you are using Signzy’s backops workflow system ( To know more about our workflow product contact your sales executive ).

**JSON Request**

```
"info": {
		"name ": "",
		"permanentAddress": "",
		"emailId": "",
		"phone": "",
		"dob": "",
		"communicationAddress": ""
	}
```

_JSON Response_

```
"info": {
        "name": "..name..",
        "emailId": "..emailId..",
        "phone": "..phone..",
        "permanentAddress": "",
        "dob": "",
        "communicationAddress": ""
    }
```

**IDcard Block**

This block is used to verify ID data against Govt/Agency APIs and also gives back a forgery score for the ID images (if they are passed).

ID Data Verification- The demographic data is verified against the ID from a govt or agency at the background.

Forgery - The goal is to be able to verify that the ID image is of a genuine ID card. This prevents random images, forged IDs or bad quality images.

This block basically needs to pass ID data, ID Image and whether its just for Proof of Identity (PoI) or Proof of Address (PoA). In case of PoA, the address also gets verified. In case you are not sure just pass both(POA/POI) in the purpose parameter.

**JSON Request**

```
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
			]
 
```

In response if both ID data check and forgery have been requested then you will get multiple pieces of data

1. You wil get back the results from data check and if the demographics such as Name, DoB, Address matched against the ID.
2. You will get a detailed response back on Forgery. This has two parts.
   * Text Match Score - The variable inputmatcher , gives you data which tells you if the data submitted by the user as his demographic matches with the data on the ID card
   * Digi Eyes Score - This is a comprehensive score on the ID and replicates human like intelligence making use of logos, position of text, face image and colors to judge if the ID is genuinely as claimed
3. You also get an additional response on Image Forensics if that is enabled in your package. It has two types
   * Image meta-data - This data is interesting as it helps you find out if the user had used some software or mobile as its last modification. While this may not guarantee that the image has been manipulated but might along with other data act as a powerful indicator for fraud
   * Image Manipulation - This gives an image as output. The image is based on an algorithm which finds aberration whenever there is photoshop or image changes of any kind. You can talk to our expert to understand this better, if you really want to see how this works.

**JSON Response**

```
{
    "idCards": [
         {
             "type": "aadhaar/passport/dl/pan/voterid",
             "name": "..name..",
             "fatherName": "..fatherName..",
             "dob": "..dob..",
             "address": "..address..",
             "images": [
                 ..images..
             ],
             "verify": "true/false",
             "purpose": [
                 "POI/POA"
             ],
             "idNo": "..idNo..",
             "verificationStatus": {
                 "verified": true/false,
                 "message": "..message..",
             },
             "forgery": {
                 "forgery": "FORGED/NOT FORGED",
                 "message": "..message..",
                 "face": {
                     "found": "true/false",
                     "message": "..message.."
                 },
                 "qrCode": {
                     "found": "",
                     "match": "",
                     "message": ""
                 },
                 "colors": {
                     "found": "",
                "message": ""
                 },
                 "imageRelatedData": {
                     "found": "",
                     "message": ""
                 },
                 "imageMetadata": {},

             },
             "inputMatcher": {
                 "forgery": "NO/YES",
                 "fields": {
                     "name": "Direct Match/No Match",
                     "dob": "Match/No Match",
                     "idNo": "Match/No Match"
                 },
                 "forgeryScore": ..forgeryScore..,
             },
             "faceExtraction": {
             },

         }]
     }
```

**Bank Account Verification Block**

This block is used to verify a bank account data. There are 3 goals

1. to verify if the Bank Account is Active
2. If the account belongs to a person by same name
3. To verify if the current end-user actually has control over the account. This allows you to not only make sure you are onboarding a user with genuine bank account but also is a double proof that its not owned by someone else.

**JSON Request**

```
    {

    "documents": [{
    				"type": "bankAccountVerification/cheque",
    				"beneficiaryMobile": "",
    				"beneficiaryAccount": "",
    				"beneficiaryName": "",
    				"beneficiaryIFSC": "",
    				"bankName": "",
    				"branchName": "",
    				"images": [],
    				"verify": "true / false"
    			}]
    }

```

**JSON Response**

```
{

          "documents": [{
                    "type": "bankAccountVerification/cheque",
                    "beneficiaryMobile": "",
                    "beneficiaryAccount": "..beneficiaryAccount..",
                    "beneficiaryIFSC": "..beneficiaryIFSC..",
                    "beneficiaryName": "..beneficiaryName..",
                    "bankName": "",
                    "branchName": "",
                    "verify": "true/false",
                    "verificationData": {
                        "actCode": "..actCode..",
                        "response": "..response..",
                        "bankRRN": "..bankRRN..",
                        "beneName": "..beneName..",
                        "tranRefNo": "..tranRefNo..",
                        "paymentRef": "..paymentRef..",
                        "tranDateTime": "..tranDateTime..",
                        "amount": "..amount..",
                        "beneMMID": "..beneMMID..",
                        "beneMobile": "",
                        "beneIFSC": "..beneIFSC..",

                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "mobileVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    }

                }
            }

```

**Note :**

This feature is currently only available in India.

**Video Verification Block**

Video Verification is meant to make sure that the user that is onboarding is the same as in the ID and also judge the liveliness of the person. As a starter for doing video analysis you need to have a randomized video and image collected. This can be achieved by initiating a session for the user as described in Video Verification Iframe section

**JSON Request**

```

{
    "video": {
        "url": "",
        "matchImage": "",
        "signzyVerifiableString": ""
    }
}
```

Response data allows you to see scores and ensure a live person onboarding.

Face match score - User present in the video is same as the one in ID proof Liveliness Scores - Ensure that the a live person was present in front of the camera. Static photo risk and Pre-recorded video risk scores indicate chances of fraud.Pre-recorded video risk- This score further checks for few advanced features in the video to ensure it was captured live. Audio match score is also an indicator if the customer had captured this live

Pre-recorded video risk- This score further checks for few advanced features in the video to ensure it was captured live. Audio match score is also an indicator if the customer had captured this live

**JSON Response**

```
{
    "video": {
        "url": "..url..",
        "matchImage": "..matchImage..",
        "signzyVerifiableString": "..signzyVerifiableString..",
        "seconds": [
        "..seconds.."
        ],
        "videoMatch": {
            "matchAudioScore": "..matchAudioScore..",

        },

        "forensics": {
            "staticRisk": {
                "staticPhoto": ..true/false..,
                "ageGroup": "..ageGroup..",

            },
            "videoLandMarks": {
                "result": "..result..",

            },
            "videoFaceMatch": {
                "videoImages": [
                "..videoImages.."
                ],
                "finalMatchImage": "..finalMatchImage.."
                "matchStatistics": {
                    "coVariance": "..coVariance..",
                    "matchPercentage": "..matchPercentage.."
                },

            },

        },
        "faceLandmarks": "..faceLandmarks.."
    }
}
```

**Digital Contract Block**

This block allows you to pass a final executed contract document from the end-consumer to back-operations.

**JSON Request**

```
 {
              "contract": {
                  "url ": "",
                  "name": "",
                  "aadhaarNumber": ""
              }
          }
```

**JSON Response**

```
 {
              "contract": {
                  "url ": "",
                  "name": "",
                  "aadhaarNumber": ""
              }
          }

```

**Others Block**

It is basically customizable block, which contains the id proof which is not supported by us.(for example:electricity bill, phone bill)

**JSON Request**

```
 {
              "others": [{
				"images": [],
				"fields": {}
			}]
        }
```

**JSON Response**

```
  {
          "others": [
            {
                "images": [
                    ..images..
                ],
                "fields": {
                    "fields1": "..fields1..",
                    "fields2": "..fields2..",
                    "fields3": "..fields3..",
                    "fields4": "..fields4.."
                }
            }]
        }
```



**Parameters**

Whenever a parameter says ‘compulsory’ it means that its compulsory within the context of that block.

### Input Field Description

#### IDcard Block

| SL NO | FIELD NAME  | DESCRIPTION                                                                                             | VALUE (COMPULSORY OR OPTIONAL)   |
| ----- | ----------- | ------------------------------------------------------------------------------------------------------- | -------------------------------- |
| 1     | type        | Type of ID proof (aadhaar/passport/dl/pan/voterid)                                                      | Compulsory                       |
| 2     | idNo        | ID number for all IDcard of individual (aadhaar/passport/dl/pan/voterid)                                | Compulsory                       |
| 3     | images      | Image url of IDcard (aadhaar/passport/dl/pan/voterid)                                                   | Optional                         |
| 4     | name        | Name of the individual (aadhaar/passport/dl/pan/voterid)                                                | Compulsory                       |
| 5     | dob         | Value for DOB(dd/mm/yyyy)                                                                               | Compulsory                       |
| 6     | address     | Address of individual                                                                                   | Optional                         |
| 7     | gender      | Gender of individual (Male/Female/Transgender)                                                          | Optional                         |
| 8     | age         | Age of individual                                                                                       | Optional                         |
| 9     | nationality | Nationality of individual                                                                               | Optional                         |
| 10    | issueDate   | IssueDate of IDcard                                                                                     | Optional(only compulsory for DL) |
| 11    | purpose     | Uploaded documents purpose \[POA/POI/POA & POI]                                                         | Compulsory                       |
| 12    | verify      | Records to be verified by verification engine or not (true/false) as string value Ex: "true" or "false" | Compulsory                       |
| 13    | callbackUrl | If the Callback URL is provided then whole response in JSON format will be posted to that URL.          | Optional                         |

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
| 2     | beneficiaryMobile  | Mobile no of individual which is connected to bank account                                              | Compulsory                     |
| 3     | beneficiaryAccount | Account no of individual                                                                                | Compulsory                     |
| 4     | beneficiaryName    | Name of the individual registered to that account                                                       | Compulsory                     |
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
| 1     | url           | url of contract                       | Optional                       |
| 2     | name          | Name of the contract holder           | Optional                       |
| 3     | aadhaarNumber | Aadhaar number of the contract holder | Optional                       |

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
