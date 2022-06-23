# Reprocess Verification Data

## Introduction

This API is used when one of the verification engine API calls have some unprocessed data and you want to reprocess it. This might happen in cases where the data provided by the user has expired or is invalid due to some discrepancy.

## API Usecase

This API is used when one of the verification engine API calls has some unprocessed data and you want to reprocess it.

How to use the API


You will need to login before sending request. You are required to pass the access token received from the login call, as authorization header in the Individual Onboarding Reprocess Output Request along with essentials and task

Use the following exchange parameters for Individual Onboarding Reprocess Output Request

## Input Parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters           | Description                        |
| -------------------- | ---------------------------------- |
| task                 | to reprocess the verification data |
| essentials           | contains the essential data        |
| essentials.requestId | gets the request id                |

]
{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl https://signzy.tech/api/v2/patrons/....patronid.../individualonboardings \
  --header 'authorization: <Access-Token>' \
  --header 'content-type: application/json' \
 '{
    "task": "reprocessOutput",
    "essentials": {
        "requestId": "...requestId.."
    }
}'
```
{% endtab %}
{% endtabs %}

## Output Parameters and Sample API Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameters | Description |
| ---------- | ----------- |
|            |             |
|            |             |
|            |             |


{% endtab %}

{% tab title="Sample API Response" %}
```
// Some code
```


{% endtab %}
{% endtabs %}



{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../individualonboardings" method="post" summary="Reprocess Verification data" %}
{% swagger-description %}
This method is used for individual onboarding reprocess output request..
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task performed - reprocess Output
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.requestID" type="string" %}
Contains the unique reprocess request ID	
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "result": {
        "idCards": [
            {
                "type": "pan",
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
                
            },
            {
                    "type": "aadhaar",
                    "images": [..images..],
                    "idNo":..idNo..",
                    "name":..name..",
                    "dob":..dob..",
                    "address":..address..",
                    "gender":..gender..",
                    "age":..age..",
                    "nationality":..nationality..",
                    "issueDate":..issueDate..",
                    "state":..state..",
                    "purpose": [
                        ..purpose(POI/POA/POI,POA)..
                    ],
                    "verify":..true/false..",
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
                    
                },
                {
                        "type": "passport",
                        "images": [..images..],
                        "idNo": "..idNo..",
                        "name": "..name..",
                        "dob": "..dob..",
                        "address": "..address..",
                        "gender": "..gender..",
                        "age": "..age..",
                        "nationality": "..nationality..",
                        "issueDate": "..issueDate..",
                        "state": "..state..",
                        "purpose": [
                            ..purpose(POI/POA/POI,POA)..
                        ],
                        "verify":..true/false.."
                    },
                    "forgery": {
                        "forgery": "FORGED/NO",
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
                    "forgery": "YES/NO",
                    "fields": {
                        "name": "..No Match / Match..",
                        "pincode": "..Not Match / Match..",
                        "dateOfBirth": "..Not Match / Match ..",
                        "idNo": "..Not Match / Match ..",
                        "dob": "..Not Match / Match .."
                    },
                    "forgeryScore": "..forgeryScore..",
                },
                "faceExtraction": {
                    "cropped": "..cropped url..",
                },
                
            },
            {
                    "type": "dl",
                    "images": [..images..],
                    "idNo": "..idNo..",
                    "name": "..name..",
                    "dob": "..dob..",
                    "address": "..address..",
                    "gender": "..gender..",
                    "age": "..age..",
                    "nationality": "..nationality..",
                    "issueDate": "..issueDate..",
                    "state": "..state..",
                    "purpose": [
                        ..purpose(POI/POA/POI,POA)..
                    ],
                    "verify":..true/false..",
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
                    
                },
                {
                        "type": "voterid",
                        "images": [..images..],
                        "idNo": "..idNo..",
                        "name": "..name..",
                        "dob": "..dob..",
                        "address": "..address..",
                        "gender": "..gender..",
                        "age": "..age..",
                        "nationality": "..nationality..",
                        "issueDate": "..issueDate..",
                        "state": "..state..",
                        "purpose": [
                            ..purpose(POI/POA/POI,POA)..
                        ],
                        "verify": "true"

                "verificationStatus": {},
                "forgery": {
                },
                "inputMatcher": {
                    "fields": {
                        "name": "..Not Match/Match..",
                        "dob": "..Not Match/Match..",
                        "pincode": "..Not Match/Match..",
                        "idNo": "..Not Match/Match.."
                    },

                },
                "faceExtraction": {

                },
                
            }
        ],
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
        },
        "documents": [
                {
                    "type": "bankAccountVerification",
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

                },
                {
                    "type": "cheque",
                    "beneficiaryMobile": "",
                    "beneficiaryAccount": "..beneficiaryAccount..",
                    "beneficiaryIFSC": "..beneficiaryIFSC..",
                    "beneficiaryName": "..beneficiaryName..",
                    "bankName": "..bankName..",
                    "branchName": "..bankName..",
                    "verify": "true/false",
                    "verificationData": {},
                    

                }
        ],
        "info": {
            "name": "..name..",
            "emailId": "..emailId..",
            "phone": "..phone..",
            "permanentAddress": "",
            "dob": "",
            "communicationAddress": ""
        },
        "contract": {
            "url": "..contract url..",
            "name": "",
            "aadhaarNumber": ""
        },
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
            }
        ],
        "email": {
            "emailId": "..emailId.."
        },
        "crossChecks": {
            "pan__aadhaar__nameMatchResult": "no match/ exact match/ partial match",
            "pan__aadhaar__dobMatchResult": "no match/ match",
            "pan__passport__nameMatchResult": "no match/ exact match/ partial match",
            "pan__passport__dobMatchResult": "no match/ match",
            ..cross check results..

        },// Name and Dob match result across all combinations of idcards
        "isCompleted": 1,

    }
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
	"task": "reprocessOutput",
	"essentials": {
        "requestId": "..requestId...."
    }
}
```
{% endtab %}

{% tab title="Response Parameters" %}

{% endtab %}
{% endtabs %}

