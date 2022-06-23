# Input Verification Data

## Introduction

This API is used to save the particulars and details of the new client entity/organisation and records the basic details in the system like name, id proof details, address and other demographic information. Upon successful integration, it provides a unique request ID to the users for future use.

How to use the API


You will need to login before sending request. You are required to pass the access token received from the login call, as authorization header in the Entity Onboarding Save Request request along with essentials and task

Use the following exchange parameters for Entity Onboarding Save Request\


```
// Data exchange
For Test Credentials
// POST :: https://preproduction.signzy.tech/api/v2/patrons/..your-patron-id../entityonboardings
For Production Credentials
// POST :: https://signzy.tech/api/v2/patrons/...patronID.../entityonboardings

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
					"type": "aadhaar",
					"images": [],
					"idNo": "",
					"name": "",
					"dob": "",
					"address": "",
					"issueDate": "",
					"state": "",
					"purpose": ["POI", "POA"],
					"verify": "true / false"
				},
				{
					"type": "passport",
					"images": [],
					"idNo": "",
					"name": "",
					"dob": "",
					"address": "",
					"issueDate": "",
					"state": "",
					"purpose": ["POI", "POA"],
					"verify": "true / false"

				},
				{
					"type": "dl",
					"images": [],
					"idNo": "",
					"name": "",
					"dob": "",
					"address": "",
					"issueDate": "",
					"state": "",
					"purpose": ["POI", "POA"],
					"verify": "true / false"
				},
				{
					"type": "pan",
					"images": [],
					"idNo": "",
					"name": "",
					"dob": "",
					"address": "",
					"issueDate": "",
					"state": "",
					"purpose": ["POI"],
					"verify": "true / false"
				},
				{
					"type": "voterid",
					"images": [],
					"idNo": "",
					"name": "",
					"dob": "",
					"address": "",
					"issueDate": "",
					"state": "",
					"purpose": ["POI"],
					"verify": "true / false"
				}

			],
			"video": {
				"url": "",
				"matchImage": "",
				"signzyVerifiableString": "",
				"seconds": ["...time at which face was tracked at frontend..."]
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
			"fetch": [{
					"type": "gstn",
					"idNo": "..idNo..",
					"entityName": "..entityName.. ",
					"entityAddress": "..entityAddress..",
					"dateOfIncorporation": "..dateOfIncorporation..",
					"inputFront": {
						"gstnDetailed": {
							"constitutionOfBusiness": "..constitutionOfBusiness..",
							"legalNameOfBusiness": "..legalNameOfBusiness..",
							"centreJurisdiction": "..centreJurisdiction..",
							"stateJurisdiction": "..stateJurisdiction..",
							"registrationDate": "..registrationDate../07/2017",
							"taxPayerDate": "..taxPayerDate..",
							"gstinStatus": "Active",
							"cancellationDate": "",
							"natureOfBusinessActivities": [
								"Office / Sale Office"
							]
						},
						"gstnRecords": [{
							"registrationName": "..registrationName..",
							"applicationStatus": "..applicationStatus..",
							"emailId": "..emailId..",
							"tinNumber": "..tinNumber..",
							"regType": "..regType..",
							"gstinRefId": "..gstinRefId..",
							"mobNum": "..mobNum..",
							"gstin": "..gstin.."
						}],
						"gstin": "..gstin.."
					},
					"verify": "true/false"
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
					"verify": "true/false"
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
							"district": [],
							"state": [
								[]
							],
							"city": [],
							"pincode": "",
							"country": [

							],
							"addressLine": "..addressLine.."
						}
					},
					"verify": "true/false"
				}, {
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
				}, {
					"type": "tan",
					"idNo": "..idNo..",
					"entityName": "..entityName..",
					"entityAddress": "..entityAddress..",
					"dateOfIncorporation": "..dateOfIncorporation..",
					"inputFront": {
						"verified": "true / false",
						"message": "..message.."
					},
					"verify": "true/false"
				}, {
					"type": "mci",
					"idNo": "..idNo..",
					"entityName": "..entityName..",
					"entityAddress": "..entityAddress..",
					"dateOfIncorporation": "..dateOfIncorporation..",
					"qualificationYear": "..qualificationYear..",
					"state": "..state..",
					"inputFront": {
						"name": "..name..",
						"permanent_address": "..permanent_address..",
						"date_of_reg": "..date_of_reg.."
					},
					"verify": "true/false"
				}, {
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
				}, {
					"type": "icai",
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
				}, {
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
				}, {
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
				}, {
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
				}, {
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
				}, {
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
								"city": ["City"],
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
				}, {
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
				}, {
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
				}, {
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
							"dob": "..dob../07/1993",
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
							"dob": "..dob../07/1993",
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
							"dob": "..dob../07/1993",
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
							"dob": "..dob../07/1993",
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
			],
			"addressDocuments": [{
					"verify": "true/false",
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
					}
				},
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
				}, {
					"type": "phone",
					"idNo": "..idNo..",
					"code": "..code..",
					"provider": "..provider..",
					"address": "..address..",
					"inputFront": {
						"name": "..name..",
						"city": "..city.",
						"address": "..address..",
						"houseNo": "..houseNo..",
						"phoneNumber": "..houseNo..",
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
					"verify": "true/false"
				}, {
					"type": "lpg",
					"idNo": "..idNo..",
					"provider": "..provider..",
					"address": "..address..",
					"inputFront": {
						"closingStockWithDistributor": "...closingStockWithDistributor..",
						"emailId": "..emailId..",
						"mobileNo": "mobileNo..",
						"approximateSubsidyAvailed": "..approximateSubsidyAvailed..",
						"bankAccountNo": "...bankAccountNo..",
						"lpgId": "..lpgId..",
						"aadhaarLinkedToBankAccount": "..aadhaarLinkedToBankAccount..",
						"distributorCode": "..distributorCode..",
						"bankAccountLinkedToLpg": "..bankAccountLinkedToLpg..",
						"subsidizedRefillConsumed": "...subsidizedRefillConsumed..",
						"aadhaarLinkedToLpgAccount": "...aadhaarLinkedToLpgAccount...",
						"consumerBase": "..consumerBase..",
						"refillBookingStatus": "..refillBookingStatus..",
						"aadhaarNumber": "..aadhaarNumber..",
						"optedOutOfSubsidy": "No/Yes",
						"bankName": "..bankName..",
						"distributorName": "..distributorName..",
						"lastRefillBookingDate": "..lastRefillBookingDate..",
						"bankIfscCode": "..bankIfscCode..",
						"address": "..address..",
						"distributorAddress": "..distributorAddress..",
						"consumerNo": "..consumerNo..",
						"consumerName": "..consumerName..",
						"consumerStatus": "..consumerStatus..",
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
					"verify": "true/false"
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
