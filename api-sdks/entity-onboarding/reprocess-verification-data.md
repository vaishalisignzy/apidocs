# Reprocess Verification Data

## Introduction

This API is used when one of the verification engine API calls has some unprocessed data and you want to reprocess it. This might happen in cases where the data provided by the entity/organization has expired or is invalid due to some discrepancy.

## API Usecase

This API is used when one of the verification engine API calls has some unprocessed data and you want to reprocess it.

## How to use the API

You will need to login before sending a request. You are required to pass the access token received from the login call, as an authorization header in the Entity Onboarding Reprocess Output Request along with essentials and tasks.

Use the following exchange parameters for Entity Onboarding Reprocess Output Request

## Input Parameters and Sample cURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters           | Description                 |
| -------------------- | --------------------------- |
| task                 | to reprocess the output     |
| essentials           | contains the essential data |
| essentials.requestId | contains request Id         |


{% endtab %}

{% tab title="Sample cURL Request" %}
```
curl https://signzy.tech/api/v2/patrons/....patronid.../entityonboardings
--header 'authorization: '
--header 'content-type: application/json'
'{
    "task": "reprocessOutput",
    "essentials": {
        "requestId": "...requestId.."
    }
}
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

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/...patronID.../entityonboardings" method="post" summary="Reprocess Verification data" %}
{% swagger-description %}
This method is used for entitty onboarding reprocess output request..
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
        "fetch": [
            {
                "type": "gstn",
                "idNo": "....idNo..",
                "entityName": "....entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
                "inputFront": {
                    "gstnDetailed": {
                        "constitutionOfBusiness": "....constitutionOfBusiness..",
                        "legalNameOfBusiness": "....legalNameOfBusiness..",
                        "centreJurisdiction": "....centreJurisdiction..",
                        "stateJurisdiction": "....stateJurisdiction..",
                        "registrationDate": "....registrationDate..",
                        "taxPayerDate": "....taxPayerDate..",
                        "gstinStatus": "....gstinStatus..",
                        "cancellationDate": "",
                        "natureOfBusinessActivities": [
                            "Office / Sale Office"
                        ]
                    },
                    "gstnRecords": [
                        {
                            "registrationName": "....registrationName..",
                            "applicationStatus": "....applicationStatus..",
                            "emailId": "....emailId..",
                            "tinNumber": "....tinNumber..",
                            "regType": "....regType..",
                            "gstinRefId": "....gstinRefId..",
                            "mobNum": "....mobNum..",
                            "gstin": "....gstin.."
                        }
                    ],
                    "gstin": "....gstin.."
                },
                "verify": "true/false",
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "centralServiceTax",
                "idNo": "..idNo..",
                "entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
                "inputFront": {
                    "locationCode": "..locationCode..",
                    "nameOfAssessee": "..nameOfAssessee..",
                    "status": "..status..",
                    "divisionCode": "..divisionCode..",
                    "addressOfAssessee": "..addressOfAssessee..",
                    "commissionerateCode": "..commissionerateCode..",
                    "rangeCode": "..rangeCode..",
                    "assesseeBelongsTo": "..assesseeBelongsTo..",
                    "splitAddress": {
						"district": [
							"..district"
						],
						"state": [
							[
								"..state.."
							]
						],
						"city": [
							"..city.."
						],
						"pincode": "..pincode..",
						"country": [
							"..country.."
						],
						"addressLine": "..addressLine.."
					}
                },
                "verify": "true/false",
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {

    				"type": "vat",
    				"idNo": "..idNo..",
    				"entityName": "..entityName..",
                    "entityAddress": "..entityAddress..",
					"dateOfIncorporation": "..dateOfIncorporation..",
    				"inputFront": {
    					"cstStatus": "..cstStatus..",
    					"pan": "..pan..",
    					"status": "",
    					"ownerName": "",
    					"dealer": "..dealer..",
    					"address": "..address..",
    					"regDate": "..regDate..",
    					"cancelDate": "",
                    "splitAddress": {
						"district": [
							"..district"
						],
						"state": [
							[
								"..state.."
							]
						],
						"city": [
							"..city.."
						],
						"pincode": "..pincode..",
						"country": [
							"..country.."
						],
						"addressLine": "..addressLine.."
					}
                },
                "verify": "true/false",
                "result": {
                    "details": {
                        "cstStatus": "..cstStatus..",
                        "pan": "..pan..",
                        "status": "",
                        "ownerName": "",
                        "dealer": "..dealer..",
                        "address": "..address..",
                        "regDate": "..regDate..",
                        "cancelDate": "",
                        "splitAddress": {
    						"district": [
    							"..district"
    						],
    						"state": [
    							[
    								"..state.."
    							]
    						],
    						"city": [
    							"..city.."
    						],
    						"pincode": "..pincode..",
    						"country": [
    							"..country.."
    						],
    						"addressLine": "..addressLine.."
    					}
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "cstStatus": "Match/No Match",
                        "pan": "Match/No Match",
                        "status": "Match/No Match",
                        "ownerName": "Match/No Match",
                        "dealer": "Match/No Match",
                        "regDate": "Match/No Match",
                        "cancelDate": "Match/No Match",
                        "address": "Match/No Match"
                    }
                }
            },
            {
                "type": "fssai",
				"idNo": "..idNo..",
				"entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
				"inputFront": {
					"locationCode": "..locationCode..",
					"nameOfAssessee": "..nameOfAssessee..",
					"status": "..status..",
					"divisionCode": "..divisionCode..",
					"addressOfAssessee": "..addressOfAssessee..",
					"commissionerateCode": "..commissionerateCode..",
					"rangeCode": "..rangeCode..",
					"assesseeBelongsTo": "..assesseeBelongsTo..",
                    "splitAddress": {
						"district": [
							"..district"
						],
						"state": [
							[
								"..state.."
							]
						],
						"city": [
							"..city.."
						],
						"pincode": "..pincode..",
						"country": [
							"..country.."
						],
						"addressLine": "..addressLine.."
					}
                },
                "verify": "true/false",
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "tan",
                "idNo": "..idNo..",
                "entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
                "inputFront": {
                    "verified": true/false,
                    "message": "..message.."
                },
                "verify": "true/false",
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "mci",
                "idNo": "..idNo..",
                "entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
                "qualificationYear": 1..qualificationYear..,
                "state": "..state..",
                "inputFront": {
                    "name": "..name..",
                    "permanent_address": "..permanent_address..",
                    "date_of_reg": "..date_of_reg.."
                },
                "verify": "true/false",
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "icsi",
				"idNo": "..idNo..",
				"memberType": "..memberType..",
				"entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
				"inputFront": {
					"city": "..city..",
					"organization": "..organization..",
					"address": "..address..",
					"type": "ACS",
                    "splitAddress": {
						"district": [
							"..district"
						],
						"state": [
							[
								"..state.."
							]
						],
						"city": [
							"..city.."
						],
						"pincode": "..pincode..",
						"country": [
							"..country.."
						],
						"addressLine": "..addressLine.."
					}
                },
                "verify": "true/false",
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "icai",
                "idNo": "..idNo..",
				"memberType": "..memberType..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
				"dateOfIncorporation": "",
				"inputFront": {
					"city": "..city..",
					"organization": "..organization..",
					"address": "..address..",
					"type": "ACS",
                    "splitAddress": {
                        "district": [
                            "..district.."
                        ],
                        "state": [
                            [
                                "..state.."
                            ]
                        ],
                        "city": [
                            "..city.."
                        ],
                        "pincode": "..pincode..",
                        "country": [
                            "..country.."
                        ],
                        "addressLine": "..addressLine.."
                    }
                },
                "verify": "true/false"
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "icwai",
                "idNo": "..idNo..",
                "memberType": "..memberType..",
                "entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
                "inputFront": {
                    "city": "..city..",
                    "organization": "..organization..",
                    "address": "..address..",
                    "type": "ACS",
                    "splitAddress": {
                        "district": [
                            "..district.."
                        ],
                        "state": [
                            [
                                "..state.."
                            ]
                        ],
                        "city": [
                            "..city.."
                        ],
                        "pincode": "..pincode..",
                        "country": [
                            "..country.."
                        ],
                        "addressLine": "..addressLine.."
                    }
                },
                "verify": "true/false"
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "ua",
				"idNo": "..idNo..",
				"entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
				"inputFront": {
					"nameofEnterprise": "..nameofEnterprise..",
					"dateofCommencement": "..dateofCommencement..",
					"state": "..state..",
					"dicName": "..dicName..",
					"status": "..status.."
				},
				"verify": "true/false"
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "sec",
				"idNo": "..idNo..",
				"state": "..state.. ",
				"entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
				"inputFront": {
					"registrationNumber": "..registrationNumber..",
					"previousRegistrationCertificate": "..previousRegistrationCertificate..",
					"nameOfTheShop": "..nameOfTheShop..",
					"act": "..act.."
				},
				"verify": "true/false"
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "ptr",
                "idNo": "..idNo..",
                "state": "..state..",
                "entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
                "inputFront": {
                    "dealerName": "..dealerName..",
                    "address1": "..address1..",
                    "address2": "..address2..",
                    "address3": "..address3..",
                    "talukaName": "..talukaName..",
                    "streetName": "",
                    "pinCode": "..pinCode..",
                    "districtName": "..districtName..",
                    "cityName": "..cityName..",
                    "effectiveOrCanceledDate": "..effectiveOrCanceledDate..",
                    "address": "..address..",
                    "status": "..status..",
                    "splitAddress": {
                        "district": [
                            "..district.."
                        ],
                        "state": [
                            [
                                "..state.."
                            ]
                        ],
                        "city": [
                            "..city.."
                        ],
                        "pincode": "..pincode..",
                        "country": [
                            "..country.."
                        ],
                        "addressLine": "..addressLine.."
                    }
                },
                "verify": "true/false"
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "iec",
                "idNo": "..idNo..",
                "entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
                "inputFront": {
                    "iec": "..iec..",
                    "iecAllotmentDate": "..iecAllotmentDate..",
                    "fileNumber": "..fileNumber..",
                    "fileDate": "..fileDate..",
                    "partyNameAndAddress": "..partyNameAndAddress..",
                    "partyName": "..partyName..",
                    "partyAddress": "..partyAddress..",
                    "phone": "..phone..",
                    "email": "..email..",
                    "exporterType": "..exporterType..",
                    "dateOfEstablishment": "..dateOfEstablishment..",
                    "bin": "..bin..",
                    "natureOfConcern": "..natureOfConcern..",
                    "bankerDetail": "..bankerDetail..,",
                    "splitPartyAddress": {
                        "district": [
                            "..district.."
                        ],
                        "state": [
                            [
                                "..state.."
                            ]
                        ],
                        "city": [
                            "..city.."
                        ],
                        "pincode": "..pincode..",
                        "country": [
                            "..country.."
                        ],
                        "addressLine": "..addressLine.."
                    },
                    "pan": "..pan..",
                    "branches": [{
                        "1": "..1..",
                        "pin": "..pin..",
                        "branchSerialNumber": "..branchSerialNumber..",
                        "address": "..address..",
                        "splitAddress": {
                            "district": [
                                "..district.."
                            ],
                            "state": [
                                [
                                    "..state.."
                                ]
                            ],
                            "city": [
                                "..city.."
                            ],
                            "pincode": "..pincode..",
                            "country": [
                                "..country.."
                            ],
                            "addressLine": "..addressLine.."
                        }
                    }],
                    "directors": [{
                        "number": "1",
                        "address": "..address..",
                        "directorName": "..directorName..",
                        "parentName": "..parentName..",
                        "splitAddress": {
                            "district": [
                                "..district.."
                            ],
                            "state": [
                                [
                                    "..state.."
                                ]
                            ],
                            "city": [
                                "..city.."
                            ],
                            "pincode": "..pincode..",
                            "country": [
                                "..country.."
                            ],
                            "addressLine": "..addressLine.."
                        }
                    }, {
                        "number": "2",
                        "address": "..address..",
                        "directorName": "..directorName..",
                        "parentName": "..parentName..",
                        "splitAddress": {
                            "district": [
                                "..district.."
                            ],
                            "state": [
                                [
                                    "..state.."
                                ]
                            ],
                            "city": [
                                "..city.."
                            ],
                            "pincode": "..pincode..",
                            "country": [
                                "..country.."
                            ],
                            "addressLine": "..addressLine.."
                        }
                    }]
                },
                "verify": "true/false"
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            {
                "type": "cst",
                "idNo": "..idNo..",
                "entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
                "inputFront": {
                    "cstStatus": "..cstStatus..",
                    "pan": "..pan..",
                    "status": "",
                    "ownerName": "",
                    "dealer": "..dealer..",
                    "address": "..address..",
                    "regDate": "..regDate..",
                    "cancelDate": "",
                    "address": "..address..",
                    "directorName": "..directorName..",
                    "parentName": "..parentName..",
                    "splitAddress": {
                        "district": [
                            "..district.."
                        ],
                        "state": [
                            [
                                "..state.."
                            ]
                        ],
                        "city": [
                            "..city.."
                        ],
                        "pincode": "..pincode..",
                        "country": [
                            "..country.."
                        ],
                        "addressLine": "..addressLine.."
                    }
                },
                "verify": "true/false"
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "tin",
                "idNo": "..idNo..",
                "entityName": "..entityName..",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
                "inputFront": {
                    "cstStatus": "..cstStatus..",
                    "pan": "..pan..",
                    "status": "",
                    "ownerName": "",
                    "dealer": "..dealer..",
                    "address": "..address..",
                    "regDate": "..regDate..",
                    "cancelDate": "",
                    "address": "..address..",
                    "directorName": "..directorName..",
                    "parentName": "..parentName..",
                    "splitAddress": {
                        "district": [
                            "..district.."
                        ],
                        "state": [
                            [
                                "..state.."
                            ]
                        ],
                        "city": [
                            "..city.."
                        ],
                        "pincode": "..pincode..",
                        "country": [
                            "..country.."
                        ],
                        "addressLine": "..addressLine.."
                    }
                },
                "verify": "true/false"
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                }
            },
            {
                "type": "roc",
                "idNo": "..idNo..",
                "entityName": "..entityName.",
                "entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..",
                "inputFront": {
                    "companyName": "..companyName..",
                    "rocOffice": "..rocOffice..",
                    "registrationNumber": "..registrationNumber..",
                    "category": "..category..",
                    "subCategory": "..subCategory..",
                    "class": "..class..",
                    "authorisedCapital": "..authorisedCapital...",
                    "paidUpCapital": "..paidUpCapital...",
                    "numberOfMembers": "..numberOfMembers..",
                    "dateOfIncorporation": "..dateOfIncorporation..",
                    "registeredAddress": "..registeredAddress..",
                    "emailId": "..emailId..",
                    "whetherListed": "..whetherListed..",
                    "lastAgmDate": "..lastAgmDate..",
                    "balanceSheetDate": "..balanceSheetDate..",
                    "statusForEfiling": "..statusForEfiling..",
                    "addressOtherThanRegisteredOffice": "",
                    "suspendedAtStockExchange": "",
                    "cin": "..cin..",
                    "directorDetails": [{
                        "din": "..din..",
                        "designation": "..designation..",
                        "dateOfAppointment": "..dateOfAppointment..",
                        "address": "..address..",
                        "dscExpiryDate": "..dscExpiryDate..",
                        "name": "..name..",
                        "whetherDscRegistered": "..whetherDscRegistered..",
                        "fatherName": "..fatherName..",
                        "dob": "..dob.."
                        "pan": "",
                        "splitAddress": {
                            "district": [
                                "..district.."
                            ],
                            "state": [
                                [
                                    "..state.."
                                ]
                            ],
                            "city": [
                                "..city.."
                            ],
                            "pincode": "..pincode..",
                            "country": [
                                "..country.."
                            ],
                            "addressLine": "..addressLine.."
                        }
                    }, {
                        "din": "..din..",
                        "designation": "..designation..",
                        "dateOfAppointment": "..dateOfAppointment..",
                        "address": "..address..",
                        "dscExpiryDate": "..dscExpiryDate..",
                        "name": "..name..",
                        "whetherDscRegistered": "..whetherDscRegistered..",
                        "fatherName": "..fatherName..",
                        "dob": "..dob.."
                        "pan": "",
                        "splitAddress": {
                            "district": [
                                "..district.."
                            ],
                            "state": [
                                [
                                    "..state.."
                                ]
                            ],
                            "city": [
                                "..city.."
                            ],
                            "pincode": "..pincode..",
                            "country": [
                                "..country.."
                            ],
                            "addressLine": "..addressLine.."
                        }
                    }, {
                        "din": "..din..",
                        "designation": "..designation..",
                        "dateOfAppointment": "..dateOfAppointment..",
                        "address": "..address..",
                        "dscExpiryDate": "..dscExpiryDate..",
                        "name": "..name..",
                        "whetherDscRegistered": "..whetherDscRegistered..",
                        "fatherName": "..fatherName..",
                        "dob": "..dob.."
                        "pan": "",
                        "splitAddress": {
                            "district": [
                                "..district.."
                            ],
                            "state": [
                                [
                                    "..state.."
                                ]
                            ],
                            "city": [
                                "..city.."
                            ],
                            "pincode": "..pincode..",
                            "country": [
                                "..country.."
                            ],
                            "addressLine": "..addressLine.."
                        }
                    }, {
                        "din": "..din..",
                        "designation": "..designation..",
                        "dateOfAppointment": "..dateOfAppointment..",
                        "address": "..address..",
                        "dscExpiryDate": "..dscExpiryDate..",
                        "name": "..name..",
                        "whetherDscRegistered": "..whetherDscRegistered..",
                        "fatherName": "..fatherName..",
                        "dob": "..dob.."
                        "pan": "",
                        "splitAddress": {
                            "district": [
                                "..district.."
                            ],
                            "state": [
                                [
                                    "..state.."
                                ]
                            ],
                            "city": [
                                "..city.."
                            ],
                            "pincode": "..pincode..",
                            "country": [
                                "..country.."
                            ],
                            "addressLine": "..addressLine.."
                        }
                    }],
                    "pan": "",
                    "splitAddress": {
                        "district": [
                            "..district.."
                        ],
                        "state": [
                            [
                                "..state.."
                            ]
                        ],
                        "city": [
                            "..city.."
                        ],
                        "pincode": "..pincode..",
                        "country": [
                            "..country.."
                        ],
                        "addressLine": "..addressLine.."
                    }
                },
                "verify": "true/false"
            }
            "result": {
                "details": {
                    ..api response..
                },
                "nameVerificationStatus": {
                    "verified": "Match/No Match",
                    "message": "..message.."
                },
                "doiVerificationStatus": {
                    "verified": "No Match/Match",
                    "message": "..message.."
                },
                "addressVerificationStatus": {
                    "verified": "Match/No Match",
                    "message": "..message.."
                },
                "fieldMatcher": {
                    "status": "Match/No Match",
                    "premissesAddress": "No Match/Match"
                }
            }

        ],
        "addressDocuments": [
            {
                "type": "electricity",
                "idNo": "..idNo..",
                "provider": "..provider..",
                "address": "..address..",
                "inputFront": {
                    "name": "..name..",
                    "currentBalance": "..currentBalance..",
                    "dueDate": "..dueDate.",
                    "mobileNumber": "..mobileNumber..",
                    "emailAddress": "",
                    "address": "..address..",
                    "consumerNo": "..consumerNo..",
                    "splitAddress": {
                        "district": [
                            "..district.."
                        ],
                        "state":"entityAddress": "..entityAddress..",
                "dateOfIncorporation": "..dateOfIncorporation..", [
                            [
                                "..state.."
                            ]
                        ],
                        "city": [
                            "..city.."
                        ],
                        "pincode": "..pincode..",
                        "country": [
                            "..country.."
                        ],
                        "addressLine": "..addressLine.."
            }
                },
                "verify": "true/false",
                "result": {
                    "details": {
                        "mobileNumber": "..mobileNumber..",
                        "name": "..name..",
                        "emailAddress": "",
                        "dueDate": "..dueDate..",
                        "currentBalance": "..currentBalance..",
                        "address": "..address..",
                        "consumerNo": "..consumerNo..",
                        "splitAddress": {
                            "district": [
                                "..district.."
                            ],
                            "state": [
                                [
                                    "..state.."
                                ]
                            ],
                            "city": [
                                "..city.."
                            ],
                            "pincode": "..pincode..",
                            "country": [
                                "..country.."
                            ],
                            "addressLine": "..addressLine.."
                        }
                    },
                    "verificationStatus": {
                        "verified": "Exact Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "name": "Match/No Match",
                        "currentBalance": "Match/No Match",
                        "dueDate": "Match/No Match",
                        "mobileNumber": "Match/No Match",
                        "emailAddress": "Match/No Match",
                        "consumerNo": "Match/No Match",
                        "address": "Exact Match"
                    }
                }
            },
            {
               "type": "lpg",
               "idNo": "..idNo..",
               "provider": "..provider..",
               "address": "",
               "inputFront": {
                   "distributorCode": "..distributorCode..",
                   "refillBookingStatus": "..refillBookingStatus..",
                   "consumerName": "..consumerName..",
                   "lpgId": "..lpgId..",
                   "aadhaarLinkedToBankAccount": "..aadhaarLinkedToBankAccount..",
                   "approximateSubsidyAvailed": "..approximateSubsidyAvailed...",
                   "address": "..address..",
                   "emailId": "..emailId..",
                   "optedOutOfSubsidy": "..optedOutOfSubsidy..",
                   "bankAccountNo": "..bankAccountNo..",
                   "distributorAddress": "..distributorAddress..",
                   "bankAccountLinkedToLpg": "..bankAccountLinkedToLpg..",
                   "lastRefillBookingDate": "..lastRefillBookingDate..",
                   "consumerNo": "..consumerNo..",
                   "distributorName": "..distributorName..",
                   "subsidizedRefillConsumed": "..subsidizedRefillConsumed..",
                   "mobileNo": "..mobileNo..",
                   "bankIfscCode": "..bankIfscCode.. ",
                   "consumerStatus": "..consumerStatus..",
                   "aadhaarLinkedToLpgAccount": "..aadhaarLinkedToLpgAccount.. ",
                   "bankName": "..bankName.. ",
                   "consumerBase": "..consumerBase..",
                   "closingStockWithDistributor": "..",
                   "aadhaarNumber": "..aadhaarNumber..",
                   "pincode": "",
                   "cityOrTown": "",
                   "splitAddress": {
                       "district": [
                           "..district.."
                       ],
                       "state": [
                           [
                               "..state.."
                           ]
                       ],
                       "city": [
                           "..city.."
                       ],
                       "pincode": "..pincode..",
                       "country": [
                           "..country.."
                       ],
                       "addressLine": "..addressLine.."
                   }
               },
               "verify": "true",
               "result": {
                   "details": {
                       ..api response..
                   },
                   "nameVerificationStatus": {
                       "verified": "Match/No Match",
                       "message": "..message.."
                   },
                   "doiVerificationStatus": {
                       "verified": "No Match/Match",
                       "message": "..message.."
                   },
                   "addressVerificationStatus": {
                       "verified": "Match/No Match",
                       "message": "..message.."
                   },
                   "fieldMatcher": {
                       "status": "Match/No Match",
                       "premissesAddress": "No Match/Match"
                   }
               },
                   "verificationStatus": {
                       "verified": "Match/No Match",
                       "message": "..message.."
                   },
                   "fieldMatcher": {
                       "distributorCode": "Match/No Match",
                       "refillBookingStatus": "No Match",
                       "consumerName": "Match/No Match",
                       "lpgId": "Match/No Match",
                       "aadhaarLinkedToBankAccount": "Match/No Match",
                       "approximateSubsidyAvailed": "Match/No Match",
                       "emailId": "Match/No Match",
                       "optedOutOfSubsidy": "Match/No Match",
                       "bankAccountNo": "Match/No Match",
                       "distributorAddress": "Match/No Match",
                       "bankAccountLinkedToLpg": "Match/No Match",
                       "lastRefillBookingDate": "Match/No Match",
                       "consumerNo": "Match/No Match",
                       "distributorName": "Match/No Match",
                       "subsidizedRefillConsumed": "Match/No Match",
                       "mobileNo": "Match/No Match",
                       "bankIfscCode": "Match/No Match",
                       "consumerStatus": "Match/No Match",
                       "aadhaarLinkedToLpgAccount": "Match/No Match",
                       "bankName": "Match/No Match",
                       "consumerBase": "No Match/Match",
                       "closingStockWithDistributor": "Match/No Match",
                       "aadhaarNumber": "Match/No Match",
                       "pincode": "Match/No Match",
                       "cityOrTown": "Match/No Match",
                       "address": "Exact Match"
                   }
               }
           },
           {
                "type": "phone",
                "idNo": "..idNo.",
                "code": "..code..",
                "verify": "..verify..",
                "provider": "..provider..",
                "address": "..address..",
                "inputFront": {
                    "name": "..name..",
                    "city": "..city..",
                    "address": "..address..",
                    "houseNo": "..houseNo..",
                    "phoneNumber": "..phoneNumber..",
                    "state": "..state..",
                    "pincode": "..pincode..",
                    "telephoneNo": "..telephoneNo..",
                    "splitAddress": {
                        "district": [
                            "..district.."
                        ],
                        "state": [
                            [
                                "..state.."
                            ]
                        ],
                        "city": [
                            "..city.."
                        ],
                        "pincode": "..pincode..",
                        "country": [
                            "..country.."
                        ],
                        "addressLine": "..addressLine.."
                    }
                },
                "result": {
                    "details": {
                        ..api response..
                    },
                    "nameVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "doiVerificationStatus": {
                        "verified": "No Match/Match",
                        "message": "..message.."
                    },
                    "addressVerificationStatus": {
                        "verified": "Match/No Match",
                        "message": "..message.."
                    },
                    "fieldMatcher": {
                        "status": "Match/No Match",
                        "premissesAddress": "No Match/Match"
                    }
                },
                    "verificationStatus": {
                        "verified": "No Match",
                        "message": "Verifcation done with No Match result"
                    },
                    "fieldMatcher": {
                        "name": "Match",
                        "city": "Match",
                        "houseNo": "Match",
                        "phoneNumber": "Match",
                        "state": "Match",
                        "pincode": "Match",
                        "telephoneNo": "Match",
                        "address": "Exact Match"
                    }
                }
            }

        ],
        "info": {
            "name": "..name..",
            "emailId": "emailId..",
            "phone": "..phone..",
            "permanentAddress": "",
            "dob": "",
            "communicationAddress": ""
        },
        "contract": {
            "url": "..url..",
            "name": "",
            "aadhaarNumber": ""
        },
        "others": [{
			"images": [
				"..images.."
			],
			"fields": {
				"fields1": "..fields1..",
				"fields2": "..fields2..",
				"fields3": "..fields3..",
				"fields4": "..fields4.."
			}
		}],
		"email": {
			"emailId": "..emailId.."
		      }
        },
        "crossChecks": {
            "nameMatcher": {
                "gstn_centralServiceTax_nameResult": "No Match/Partial Match/Match",
                "gstn_vat_nameResult": "No Match/Partial Match/Match",
                "gstn_fssai_nameResult": "No Match/Partial Match/Match",
                "gstn_tan_nameResult": "No Match/Partial Match/Match",
                "gstn_mci_nameResult": "No Match/Partial Match/Match",
                "gstn_icsi_nameResult": "No Match/Partial Match/Match",
                "gstn_icai_nameResult": "No Match/Partial Match/Match",
                "gstn_icwai_nameResult": "No Match/Partial Match/Match",
                "gstn_ua_nameResult": "No Match/Partial Match/Match",
                "gstn_sec_nameResult": "No Match/Partial Match/Match",
                "gstn_ptr_nameResult": "No Match/Partial Match/Match",
                "gstn_iec_nameResult": "No Match/Partial Match/Match",
                "gstn_cst_nameResult": "No Match/Partial Match/Match",
                "gstn_tin_nameResult": "No Match/Partial Match/Match",
                "gstn_roc_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_vat_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_fssai_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_tan_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_mci_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_icsi_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_icai_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_icwai_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_ua_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_sec_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_ptr_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_iec_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_cst_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_tin_nameResult": "No Match/Partial Match/Match",
                "centralServiceTax_roc_nameResult": "No Match/Partial Match/Match",
                "vat_fssai_nameResult": "No Match/Partial Match/Match",
                "vat_tan_nameResult": "No Match/Partial Match/Match",
                "vat_mci_nameResult": "No Match/Partial Match/Match",
                "vat_icsi_nameResult": "No Match/Partial Match/Match",
                "vat_icai_nameResult": "No Match/Partial Match/Match",
                "vat_icwai_nameResult": "No Match/Partial Match/Match",
                "vat_ua_nameResult": "No Match/Partial Match/Match",
                "vat_sec_nameResult": "No Match/Partial Match/Match",
                "vat_ptr_nameResult": "No Match/Partial Match/Match",
                "vat_iec_nameResult": "No Match/Partial Match/Match",
                "vat_cst_nameResult": "No Match/Partial Match/Match",
                "vat_tin_nameResult": "No Match/Partial Match/Match",
                "vat_roc_nameResult": "No Match/Partial Match/Match",
                "fssai_tan_nameResult": "No Match/Partial Match/Match",
                "fssai_mci_nameResult": "No Match/Partial Match/Match",
                "fssai_icsi_nameResult": "No Match/Partial Match/Match",
                "fssai_icai_nameResult": "No Match/Partial Match/Match",
                "fssai_icwai_nameResult": "No Match/Partial Match/Match",
                "fssai_ua_nameResult": "No Match/Partial Match/Match",
                "fssai_sec_nameResult": "No Match/Partial Match/Match",
                "fssai_ptr_nameResult": "No Match/Partial Match/Match",
                "fssai_iec_nameResult": "No Match/Partial Match/Match",
                "fssai_cst_nameResult": "No Match/Partial Match/Match",
                "fssai_tin_nameResult": "No Match/Partial Match/Match",
                "fssai_roc_nameResult": "No Match/Partial Match/Match",
                "tan_mci_nameResult": "No Match/Partial Match/Match",
                "tan_icsi_nameResult": "No Match/Partial Match/Match",
                "tan_icai_nameResult": "No Match/Partial Match/Match",
                "tan_icwai_nameResult": "No Match/Partial Match/Match",
                "tan_ua_nameResult": "No Match/Partial Match/Match",
                "tan_sec_nameResult": "No Match/Partial Match/Match",
                "tan_ptr_nameResult": "No Match/Partial Match/Match",
                "tan_iec_nameResult": "No Match/Partial Match/Match",
                "tan_cst_nameResult": "No Match/Partial Match/Match",
                "tan_tin_nameResult": "No Match/Partial Match/Match",
                "tan_roc_nameResult": "No Match/Partial Match/Match",
                "mci_icsi_nameResult": "No Match/Partial Match/Match",
                "mci_icai_nameResult": "No Match/Partial Match/Match",
                "mci_icwai_nameResult": "No Match/Partial Match/Match",
                "mci_ua_nameResult": "No Match/Partial Match/Match",
                "mci_sec_nameResult": "No Match/Partial Match/Match",
                "mci_ptr_nameResult": "No Match/Partial Match/Match",
                "mci_iec_nameResult": "No Match/Partial Match/Match",
                "mci_cst_nameResult": "No Match/Partial Match/Match",
                "mci_tin_nameResult": "No Match/Partial Match/Match",
                "mci_roc_nameResult": "No Match/Partial Match/Match",
                "icsi_icai_nameResult": "No Match/Partial Match/Match",
                "icsi_icwai_nameResult": "No Match/Partial Match/Match",
                "icsi_ua_nameResult": "No Match/Partial Match/Match",
                "icsi_sec_nameResult": "No Match/Partial Match/Match",
                "icsi_ptr_nameResult": "No Match/Partial Match/Match",
                "icsi_iec_nameResult": "No Match/Partial Match/Match",
                "icsi_cst_nameResult": "No Match/Partial Match/Match",
                "icsi_tin_nameResult": "No Match/Partial Match/Match",
                "icsi_roc_nameResult": "No Match/Partial Match/Match",
                "icai_icwai_nameResult": "No Match/Partial Match/Match",
                "icai_ua_nameResult": "No Match/Partial Match/Match",
                "icai_sec_nameResult": "No Match/Partial Match/Match",
                "icai_ptr_nameResult": "No Match/Partial Match/Match",
                "icai_iec_nameResult": "No Match/Partial Match/Match",
                "icai_cst_nameResult": "No Match/Partial Match/Match",
                "icai_tin_nameResult": "No Match/Partial Match/Match",
                "icai_roc_nameResult": "No Match/Partial Match/Match",
                "icwai_ua_nameResult": "No Match/Partial Match/Match",
                "icwai_sec_nameResult": "No Match/Partial Match/Match",
                "icwai_ptr_nameResult": "No Match/Partial Match/Match",
                "icwai_iec_nameResult": "No Match/Partial Match/Match",
                "icwai_cst_nameResult": "No Match/Partial Match/Match",
                "icwai_tin_nameResult": "No Match/Partial Match/Match",
                "icwai_roc_nameResult": "No Match/Partial Match/Match",
                "ua_sec_nameResult": "No Match/Partial Match/Match",
                "ua_ptr_nameResult": "No Match/Partial Match/Match",
                "ua_iec_nameResult": "No Match/Partial Match/Match",
                "ua_cst_nameResult": "No Match/Partial Match/Match",
                "ua_tin_nameResult": "No Match/Partial Match/Match",
                "ua_roc_nameResult": "No Match/Partial Match/Match",
                "sec_ptr_nameResult": "No Match/Partial Match/Match",
                "sec_iec_nameResult": "No Match/Partial Match/Match",
                "sec_cst_nameResult": "No Match/Partial Match/Match",
                "sec_tin_nameResult": "No Match/Partial Match/Match",
                "sec_roc_nameResult": "No Match/Partial Match/Match",
                "ptr_iec_nameResult": "No Match/Partial Match/Match",
                "ptr_cst_nameResult": "No Match/Partial Match/Match",
                "ptr_tin_nameResult": "No Match/Partial Match/Match",
                "ptr_roc_nameResult": "No Match/Partial Match/Match",
                "iec_cst_nameResult": "No Match/Partial Match/Match",
                "iec_tin_nameResult": "No Match/Partial Match/Match",
                "iec_roc_nameResult": "No Match/Partial Match/Match",
                "cst_tin_nameResult": "No Match/Partial Match/Match",
                "cst_roc_nameResult": "No Match/Partial Match/Match",
                "tin_roc_nameResult": "No Match/Partial Match/Match"
            },
            "dateOfIncorporationMatcher": {
                "fssai_tan_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_mci_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_icsi_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_icai_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_icwai_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_ua_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_sec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_ptr_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_iec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_cst_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "fssai_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_mci_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_icsi_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_icai_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_icwai_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_ua_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_sec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_ptr_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_iec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_cst_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tan_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "mci_icsi_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "mci_icai_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "mci_icwai_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "mci_ua_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "mci_sec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "mci_ptr_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "mci_iec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "mci_cst_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "mci_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "mci_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icsi_icai_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icsi_icwai_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icsi_ua_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icsi_sec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icsi_ptr_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icsi_iec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icsi_cst_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icsi_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icsi_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icai_icwai_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icai_ua_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icai_sec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icai_ptr_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icai_iec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icai_cst_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icai_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icai_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icwai_ua_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icwai_sec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icwai_ptr_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icwai_iec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icwai_cst_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icwai_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "icwai_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "ua_sec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "ua_ptr_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "ua_iec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "ua_cst_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "ua_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "ua_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "sec_ptr_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "sec_iec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "sec_cst_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "sec_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "sec_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "ptr_iec_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "ptr_cst_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "ptr_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "ptr_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "iec_cst_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "iec_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "iec_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "cst_tin_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "cst_roc_dateOfIncorporationResult": "No Match/Partial Match/Match",
                "tin_roc_dateOfIncorporationResult": "No Match/Partial Match/Match"
            },
            "addressMatcher": {
                "gstn_centralServiceTax_addressResult": "No Match/Partial Match/Match",
                "gstn_vat_addressResult": "No Match/Partial Match/Match",
                "gstn_fssai_addressResult": "No Match/Partial Match/Match",
                "gstn_tan_addressResult": "No Match/Partial Match/Match",
                "gstn_mci_addressResult": "No Match/Partial Match/Match",
                "gstn_icsi_addressResult": "No Match/Partial Match/Match",
                "gstn_icai_addressResult": "No Match/Partial Match/Match",
                "gstn_icwai_addressResult": "No Match/Partial Match/Match",
                "gstn_ua_addressResult": "No Match/Partial Match/Match",
                "gstn_sec_addressResult": "No Match/Partial Match/Match",
                "gstn_ptr_addressResult": "No Match/Partial Match/Match",
                "gstn_iec_addressResult": "No Match/Partial Match/Match",
                "gstn_cst_addressResult": "No Match/Partial Match/Match",
                "gstn_tin_addressResult": "No Match/Partial Match/Match",
                "gstn_roc_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_vat_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_fssai_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_tan_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_mci_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_icsi_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_icai_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_icwai_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_ua_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_sec_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_ptr_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_iec_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_cst_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_tin_addressResult": "No Match/Partial Match/Match",
                "centralServiceTax_roc_addressResult": "No Match/Partial Match/Match",
                "vat_fssai_addressResult": "No Match/Partial Match/Match",
                "vat_tan_addressResult": "No Match/Partial Match/Match",
                "vat_mci_addressResult": "No Match/Partial Match/Match",
                "vat_icsi_addressResult": "No Match/Partial Match/Match",
                "vat_icai_addressResult": "No Match/Partial Match/Match",
                "vat_icwai_addressResult": "No Match/Partial Match/Match",
                "vat_ua_addressResult": "No Match/Partial Match/Match",
                "vat_sec_addressResult": "No Match/Partial Match/Match",
                "vat_ptr_addressResult": "No Match/Partial Match/Match",
                "vat_iec_addressResult": "No Match/Partial Match/Match",
                "vat_cst_addressResult": "No Match/Partial Match/Match",
                "vat_tin_addressResult": "No Match/Partial Match/Match",
                "vat_roc_addressResult": "No Match/Partial Match/Match",
                "fssai_tan_addressResult": "No Match/Partial Match/Match",
                "fssai_mci_addressResult": "No Match/Partial Match/Match",
                "fssai_icsi_addressResult": "No Match/Partial Match/Match",
                "fssai_icai_addressResult": "No Match/Partial Match/Match",
                "fssai_icwai_addressResult": "No Match/Partial Match/Match",
                "fssai_ua_addressResult": "No Match/Partial Match/Match",
                "fssai_sec_addressResult": "No Match/Partial Match/Match",
                "fssai_ptr_addressResult": "No Match/Partial Match/Match",
                "fssai_iec_addressResult": "No Match/Partial Match/Match",
                "fssai_cst_addressResult": "No Match/Partial Match/Match",
                "fssai_tin_addressResult": "No Match/Partial Match/Match",
                "fssai_roc_addressResult": "No Match/Partial Match/Match",
                "tan_mci_addressResult": "No Match/Partial Match/Match",
                "tan_icsi_addressResult": "No Match/Partial Match/Match",
                "tan_icai_addressResult": "No Match/Partial Match/Match",
                "tan_icwai_addressResult": "No Match/Partial Match/Match",
                "tan_ua_addressResult": "No Match/Partial Match/Match",
                "tan_sec_addressResult": "No Match/Partial Match/Match",
                "tan_ptr_addressResult": "No Match/Partial Match/Match",
                "tan_iec_addressResult": "No Match/Partial Match/Match",
                "tan_cst_addressResult": "No Match/Partial Match/Match",
                "tan_tin_addressResult": "No Match/Partial Match/Match",
                "tan_roc_addressResult": "No Match/Partial Match/Match",
                "mci_icsi_addressResult": "No Match/Partial Match/Match",
                "mci_icai_addressResult": "No Match/Partial Match/Match",
                "mci_icwai_addressResult": "No Match/Partial Match/Match",
                "mci_ua_addressResult": "No Match/Partial Match/Match",
                "mci_sec_addressResult": "No Match/Partial Match/Match",
                "mci_ptr_addressResult": "No Match/Partial Match/Match",
                "mci_iec_addressResult": "No Match/Partial Match/Match",
                "mci_cst_addressResult": "No Match/Partial Match/Match",
                "mci_tin_addressResult": "No Match/Partial Match/Match",
                "mci_roc_addressResult": "No Match/Partial Match/Match",
                "icsi_icai_addressResult": "No Match/Partial Match/Match",
                "icsi_icwai_addressResult": "No Match/Partial Match/Match",
                "icsi_ua_addressResult": "No Match/Partial Match/Match",
                "icsi_sec_addressResult": "No Match/Partial Match/Match",
                "icsi_ptr_addressResult": "No Match/Partial Match/Match",
                "icsi_iec_addressResult": "No Match/Partial Match/Match",
                "icsi_cst_addressResult": "No Match/Partial Match/Match",
                "icsi_tin_addressResult": "No Match/Partial Match/Match",
                "icsi_roc_addressResult": "No Match/Partial Match/Match",
                "icai_icwai_addressResult": "No Match/Partial Match/Match",
                "icai_ua_addressResult": "No Match/Partial Match/Match",
                "icai_sec_addressResult": "No Match/Partial Match/Match",
                "icai_ptr_addressResult": "No Match/Partial Match/Match",
                "icai_iec_addressResult": "No Match/Partial Match/Match",
                "icai_cst_addressResult": "No Match/Partial Match/Match",
                "icai_tin_addressResult": "No Match/Partial Match/Match",
                "icai_roc_addressResult": "No Match/Partial Match/Match",
                "icwai_ua_addressResult": "No Match/Partial Match/Match",
                "icwai_sec_addressResult": "No Match/Partial Match/Match",
                "icwai_ptr_addressResult": "No Match/Partial Match/Match",
                "icwai_iec_addressResult": "No Match/Partial Match/Match",
                "icwai_cst_addressResult": "No Match/Partial Match/Match",
                "icwai_tin_addressResult": "No Match/Partial Match/Match",
                "icwai_roc_addressResult": "No Match/Partial Match/Match",
                "ua_sec_addressResult": "No Match/Partial Match/Match",
                "ua_ptr_addressResult": "No Match/Partial Match/Match",
                "ua_iec_addressResult": "No Match/Partial Match/Match",
                "ua_cst_addressResult": "No Match/Partial Match/Match",
                "ua_tin_addressResult": "No Match/Partial Match/Match",
                "ua_roc_addressResult": "No Match/Partial Match/Match",
                "sec_ptr_addressResult": "No Match/Partial Match/Match",
                "sec_iec_addressResult": "No Match/Partial Match/Match",
                "sec_cst_addressResult": "No Match/Partial Match/Match",
                "sec_tin_addressResult": "No Match/Partial Match/Match",
                "sec_roc_addressResult": "No Match/Partial Match/Match",
                "ptr_iec_addressResult": "No Match/Partial Match/Match",
                "ptr_cst_addressResult": "No Match/Partial Match/Match",
                "ptr_tin_addressResult": "No Match/Partial Match/Match",
                "ptr_roc_addressResult": "No Match/Partial Match/Match",
                "iec_cst_addressResult": "No Match/Partial Match/Match",
                "iec_tin_addressResult": "No Match/Partial Match/Match",
                "iec_roc_addressResult": "No Match/Partial Match/Match",
                "cst_tin_addressResult": "No Match/Partial Match/Match",
                "cst_roc_addressResult": "No Match/Partial Match/Match",
                "tin_roc_addressResult": "No Match/Partial Match/Match"
            }
        },
        "isCompleted": 1
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

