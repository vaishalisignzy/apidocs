# Pull Contract

The Pull Contract API is used to extract the details of an existing contract using the unique Contract ID and all the details related to the contract parties involved will be displayed.

Client can avail the contract along with its metadata using the pull contract API call by passing contactId and customerId parameters.

{% swagger baseUrl="https://contracting.signzy.tech" path="/api/contractdetails/pullData" method="post" summary="Pull Contract" %}
{% swagger-description %}
This method is used to pull the details of an existing contract.
{% endswagger-description %}

{% swagger-parameter in="body" name="contractId" type="string" %}
The unique ID of the contract to be pulled
{% endswagger-parameter %}

{% swagger-parameter in="body" name="customerId" type="string" %}
The unique customer ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "contractResponse": {
        "customerId": "..customerId..",
        "contractId": "..contractId..",
        "userReminderTime": userReminderTime,
        "maximumValidityTime": maximumValidityTime,
        "adminReminderTime": adminReminderTime,
        "contractCreationTime": ..contractCreationTime..,
        "callbackUrl": "..callbackUrl..",
        "initialContract": "..initialContract..",
        "isCompleted": "..isCompleted...",
        "contractName": "...contractName...",
        "contractPageCount": "...contractPageCount...",
        "tnc": "...tnc...",
        "intialPdfHash": "...intialPdfHash...",
        "customerMailList": [
         "...customerMailList..."
         ],
        "contractCompletionTime" : "...contractCompletionTime..."
        "finalSignedContract": "..finalSignedContract..",
        "finalSignedContractHash": "...finalSignedContractHash...",
       "finalDscSignedContractUrl": "...finalDscSignedContractUrl...",
       "finalDscSignedContractBase64": "...finalDscSignedContractBase64...",
       "finalDscSignedContractHash": "...finalDscSignedContractHash...",
       "auditCertificateUrl": "...auditCertificateUrl...",
       "auditCertificateBase64": "...auditCertificateBase64...",
       "auditCertificateHash": "...auditCertificateHash...",
        "signerdetail": [
            {
                "signerName": "..signerName..",
                "signerEmail": "..signerEmail..",
                "signOrder": "..signOrder..",
                "signerId": "..signerId..",
                "signaturePosition": "..signaturePosition..",
                "contractSendTime": ..contractSendTime..,
                "esignUrl": "..esignUrl..",
                "contractUrl": "..contractUrl..",
                "contractSignTime": ..contractSignTime..,
                "signatureOptions": [...signatureOptions...],
                "additionalVerification": [...additionalVerification...],
                "showId": "true",
                "idImage": "...idImage...",
                "signerMobile": "...signerMobile...",
                "signerOtpMobile": "...signerOtpMobile...",
                "tnc": "...tnc...",
                "status": "...status...",
                "contractUrl": "...contractUrl...",
                "initialPdfHash": "...initialPdfHash...",
                "signatureType": "...signatureType...",
                "result": {
                    "outputPdfHash": "...outputPdfHash...",
                    "esignedOutput": "..esignedOutput.."
                },
                "forensics": {
                           "geoLocationData": {
                               "ip": "..ip..",
                               "city": "..city..",
                               "region": "..region..",
                               "region_code": "..region_code..",
                               "country": "..country..",
                               "country_name": "..country_name..",
                               "continent_code": "..continent_code..",
                               "latitude": ..latitude..,
                               "longitude": ..longitude..,
                               "timezone": "..timezone..",
                               "utc_offset": "..utc_offset..",
                               "asn": "..asn..",
                               "org": "..org.."
                           },
                           "userBrowserData": {
                               "browserCodeName": "..userBrowserData..",
                               "browserVersion": "..browserVersion..",
                               "cookieEnabled": ..cookieEnabled..,
                               "browserLanguage": "..browserLanguage..",
                               "os": "..os..",
                               "userAgent": "..userAgent.."
                           }
                       },
                       "signerMatchData": {
                           "nameMatch": "..nameMatch..",
                           "pincodeMatch": "..pincodeMatch..",
                           "genderMatch": "..genderMatch..",
                           "dobMatch": "..dobMatch..",
                           "uidLastFourDigitsMatch": "..uidLastFourDigitsMatch.."
                       },
                       "signerSignedContract": "...signerSignedContract...",
                       "otp": {
                           "message": "...message...",
                           "verified": "..verified...",
                           "transactionId": "...transactionId..."
                       },
                       "video": {
                           "video": "...video...",
                           "transactionId": "...transactionId...",
                           "matchImage": "...matchImage...",
                           "randomNumber": "...randomNumber...",
                           "seconds": [...seconds...],
                           "videoForensics": {
                               "videoMatch": {
                                   "matchAudioScore": "...matchAudioScore...",
                               },
                               "videoFaceMatch": {
                                   "videoImages": [...videoImages...],
                                   "finalMatchImage": "...finalMatchImage...",
                                   "matchStatistics": {
                                       "coVariance": "...coVariance...",
                                       "matchPercentage": "...matchPercentage..."
                                   }
                               }
                           }
                       },
                       "timestamp": {
                           "login": ...login...,
                           "signatureSelect": ...signatureSelect...,
                           "contractiframe": ...contractiframe...,
                           "sendOtp": ...sendOtp...,
                           "verifyOtp": ...verifyOtp...,
                           "videoInstructions": ...videoInstructions...,
                           "idCard": ...idCard...,
                           "video": ...video...
                       }
            },
            {
                "signerName": "..signerName..",
                "signerEmail": "..signerEmail..",
                "signOrder": "..signOrder..",
                "signerId": "..signerId..",
                "signaturePosition": "..signaturePosition..",
                "contractSendTime": ..contractSendTime..,
                "esignUrl": "..esignUrl..",
                "contractUrl": "..contractUrl..",
                "contractSignTime": ..contractSignTime..,
                "signatureOptions": [...signatureOptions...],
                "additionalVerification": [...additionalVerification...],
                "showId": "true",
                "idImage": "...idImage...",
                "signerMobile": "...signerMobile...",
                "signerOtpMobile": "...signerOtpMobile...",
                "tnc": "...tnc...",
                "status": "...status...",
                "contractUrl": "...contractUrl...",
                "initialPdfHash": "...initialPdfHash...",
                "signatureType": "...signatureType...",
                "result": {
                    "outputPdfHash": "...outputPdfHash...",
                    "esignedOutput": "..esignedOutput.."
                },
                "userConsentEmailDetails": {
                       "emailId": "...emailId...",
                       "name": "...name...",
                       "subject": "...subject...",
                       "consentText": "...consentText...",
                       "body": "...body...",
                       "contractId": "...contractId...",
                       "valid": "...valid...",
                       "negativeWordsFound": [..negativeWordsFound..],
                       "mailReceiveTime": ..mailReceiveTime..
                },
                "forensics": {
                           "geoLocationData": {
                               "ip": "..ip..",
                               "city": "..city..",
                               "region": "..region..",
                               "region_code": "..region_code..",
                               "country": "..country..",
                               "country_name": "..country_name..",
                               "continent_code": "..continent_code..",
                               "latitude": ..latitude..,
                               "longitude": ..longitude..,
                               "timezone": "..timezone..",
                               "utc_offset": "..utc_offset..",
                               "asn": "..asn..",
                               "org": "..org.."
                           },
                           "userBrowserData": {
                               "browserCodeName": "..userBrowserData..",
                               "browserVersion": "..browserVersion..",
                               "cookieEnabled": ..cookieEnabled..,
                               "browserLanguage": "..browserLanguage..",
                               "os": "..os..",
                               "userAgent": "..userAgent.."
                           }
                       },
                       "signerMatchData": {
                           "nameMatch": "..nameMatch..",
                           "pincodeMatch": "..pincodeMatch..",
                           "genderMatch": "..genderMatch..",
                           "dobMatch": "..dobMatch..",
                           "uidLastFourDigitsMatch": "..uidLastFourDigitsMatch.."
                       },
                       "signerSignedContract": "...signerSignedContract...",
                       "otp": {
                           "message": "...message...",
                           "verified": "..verified...",
                           "transactionId": "...transactionId..."
                       },
                       "video": {
                           "video": "...video...",
                           "transactionId": "...transactionId...",
                           "matchImage": "...matchImage...",
                           "randomNumber": "...randomNumber...",
                           "seconds": [...seconds...],
                           "videoForensics": {
                               "videoMatch": {
                                   "matchAudioScore": "...matchAudioScore...",
                               },
                               "videoFaceMatch": {
                                   "videoImages": [...videoImages...],
                                   "finalMatchImage": "...finalMatchImage...",
                                   "matchStatistics": {
                                       "coVariance": "...coVariance...",
                                       "matchPercentage": "...matchPercentage..."
                                   }
                               }
                           }
                       },
                       "timestamp": {
                           "login": ...login...,
                           "signatureSelect": ...signatureSelect...,
                           "contractiframe": ...contractiframe...,
                           "sendOtp": ...sendOtp...,
                           "verifyOtp": ...verifyOtp...,
                           "videoInstructions": ...videoInstructions...,
                           "idCard": ...idCard...,
                           "video": ...video...
                       }
            },
            {
                "signerName": "..signerName..",
                "signerEmail": "..signerEmail..",
                "signOrder": "..signOrder..",
                "signerId": "..signerId..",
                "signaturePosition": "..signaturePosition..",
                "contractSendTime": ..contractSendTime..,
                "esignUrl": "..esignUrl..",
                "contractUrl": "..contractUrl..",
                "contractSignTime": ..contractSignTime..,
                "signatureOptions": [...signatureOptions...],
                "additionalVerification": [...additionalVerification...],
                "showId": "true",
                "idImage": "...idImage...",
                "signerMobile": "...signerMobile...",
                "signerOtpMobile": "...signerOtpMobile...",
                "tnc": "...tnc...",
                "status": "...status...",
                "contractUrl": "...contractUrl...",
                "initialPdfHash": "...initialPdfHash...",
                "signatureType": "...signatureType...",
                "result": {
                    "outputPdfHash": "...outputPdfHash...",
                    "esignedOutput": "..esignedOutput.."
                },
                "userConsentEmailDetails": {},
                "forensics": {
                           "geoLocationData": {
                               "ip": "..ip..",
                               "city": "..city..",
                               "region": "..region..",
                               "region_code": "..region_code..",
                               "country": "..country..",
                               "country_name": "..country_name..",
                               "continent_code": "..continent_code..",
                               "latitude": ..latitude..,
                               "longitude": ..longitude..,
                               "timezone": "..timezone..",
                               "utc_offset": "..utc_offset..",
                               "asn": "..asn..",
                               "org": "..org.."
                           },
                           "userBrowserData": {
                               "browserCodeName": "..userBrowserData..",
                               "browserVersion": "..browserVersion..",
                               "cookieEnabled": ..cookieEnabled..,
                               "browserLanguage": "..browserLanguage..",
                               "os": "..os..",
                               "userAgent": "..userAgent.."
                           }
                       },
                       "signerMatchData": {
                           "nameMatch": "..nameMatch..",
                           "pincodeMatch": "..pincodeMatch..",
                           "genderMatch": "..genderMatch..",
                           "dobMatch": "..dobMatch..",
                           "uidLastFourDigitsMatch": "..uidLastFourDigitsMatch.."
                       },
                       "signerSignedContract": "...signerSignedContract...",
                       "otp": {
                           "message": "...message...",
                           "verified": "..verified...",
                           "transactionId": "...transactionId..."
                       },
                       "video": {
                           "video": "...video...",
                           "transactionId": "...transactionId...",
                           "matchImage": "...matchImage...",
                           "randomNumber": "...randomNumber...",
                           "seconds": [...seconds...],
                           "videoForensics": {
                               "videoMatch": {
                                   "matchAudioScore": "...matchAudioScore...",
                               },
                               "videoFaceMatch": {
                                   "videoImages": [...videoImages...],
                                   "finalMatchImage": "...finalMatchImage...",
                                   "matchStatistics": {
                                       "coVariance": "...coVariance...",
                                       "matchPercentage": "...matchPercentage..."
                                   }
                               }
                           }
                       },
                       "timestamp": {
                           "login": ...login...,
                           "signatureSelect": ...signatureSelect...,
                           "contractiframe": ...contractiframe...,
                           "sendOtp": ...sendOtp...,
                           "verifyOtp": ...verifyOtp...,
                           "videoInstructions": ...videoInstructions...,
                           "idCard": ...idCard...,
                           "video": ...video...
                       }
            }
            ],
            "deletedSignerdetail" : []

        }
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
        "contractId": "..contractId..",
        "customerId": "..customerId.."
    }
```
{% endtab %}

{% tab title="Response Parameters" %}


#### Output Parameters

| PARAMETERS                    | DESCRIPTION                                                                                                                                                                                                                          |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| contractId                    | Unique Id of the contract                                                                                                                                                                                                            |
| customerId                    | Unique Id of the customer                                                                                                                                                                                                            |
| contractName                  | Name of the contract                                                                                                                                                                                                                 |
| contractPageCount             | Number of pages in the contract                                                                                                                                                                                                      |
| tnc                           | Terms and conditions of the contract                                                                                                                                                                                                 |
| userReminderTime              | Time after which user will be sent a reminder mail for signing the contract                                                                                                                                                          |
| maximumValidityTime           | Maximun time after which the contract gets expired                                                                                                                                                                                   |
| adminReminderTime             | Time after which the mail for reminder will be sent to the admin to check the progress of the contract                                                                                                                               |
| contractCreationTime          | Time at which the contract is created(time is in EPOCH format)                                                                                                                                                                       |
| initialContract               | initialContract created the customer                                                                                                                                                                                                 |
| intialPdfHash                 | Hash of the Intial Contract PDF created the customer                                                                                                                                                                                 |
| finalSignedContract           | Contract url after all contracts are signed                                                                                                                                                                                          |
| finalSignedHash               | Hash of the Contract PDF after all signers have signed the contract.                                                                                                                                                                 |
| finalDscSignedContractUrl     | Contract URL of the finally signed Contract by signzy DSC after the contract has been signed by all the signers.                                                                                                                     |
| finalDscSignedContractBase64  | Base64 of the Contract finally signed by signzy DSC after the contract has been signed by all the signers.This field contains value only when fileFormat is base64 otherwise it contains a empty string                              |
| finalSignedHash               | Hash of the DSC Contract PDF                                                                                                                                                                                                         |
| auditCertificateUrl           | Audit Certificate is a certificate generated and digitally signed by signzy which contains contract details,signer Details and auditTrail of the Contract.                                                                           |
| auditCertificateBase64        | Base64 of the Audit Certificate.This field contains value only when fileFormat is base64 otherwise it contains a empty string                                                                                                        |
| auditCertificateHash          | Hash of the file of the Audit Certificate.                                                                                                                                                                                           |
| signOrder                     | Order in which signer has to sign in the contract                                                                                                                                                                                    |
| signerId                      | Unique id of the signer                                                                                                                                                                                                              |
| signaturePosition             | Position of the signature in the contract page                                                                                                                                                                                       |
| contractSendTime              | Time at which the contract is sent                                                                                                                                                                                                   |
| contractCompletionTime        | Time at which the contract has compleeted and alll the signers have signed                                                                                                                                                           |
| initialPdfHash                | Hash of the PDF before it has been signed by the signer                                                                                                                                                                              |
| signatureType                 | Type of siging Method used by signer .Possible Values is one of them("aadhaaresign","esign","iaccept").                                                                                                                              |
| esignUrl                      | Signing Url of the signer                                                                                                                                                                                                            |
| contractUrl                   | Url of the Contract                                                                                                                                                                                                                  |
| contractSignTime              | Time at which the contract is signed                                                                                                                                                                                                 |
| isCompleted                   | The value is set to 1 if the contract signing procedure has completed.                                                                                                                                                               |
| customerMailList              | List of the admin mail ids of customers.                                                                                                                                                                                             |
| esignedOutput                 | The output Signed Contract file by the particular signer.                                                                                                                                                                            |
| outputPdfHash                 | Hash of the esignedOutput PDF after it has been signed by the signer.                                                                                                                                                                |
| Forensics Block               | The data from the signer's browser and user geoLocation by the particular signer.                                                                                                                                                    |
| ip                            | IP of the signer.                                                                                                                                                                                                                    |
| city                          | city of the signer.                                                                                                                                                                                                                  |
| region                        | region of the signer.                                                                                                                                                                                                                |
| region\_code                  | region\_code of the signer.                                                                                                                                                                                                          |
| country                       | country code of the signer.                                                                                                                                                                                                          |
| continent\_code               | continent code of the signer.                                                                                                                                                                                                        |
| latitude                      | latitude of the signer.                                                                                                                                                                                                              |
| longitude                     | longitude of the signer.                                                                                                                                                                                                             |
| timezone                      | timezone of the signer.                                                                                                                                                                                                              |
| utc\_offset                   | utc\_offset of the signer.                                                                                                                                                                                                           |
| asn                           | Autonomous system number of the ISP of the signer.                                                                                                                                                                                   |
| org                           | Name of the ISP of the signer.                                                                                                                                                                                                       |
| browserCodeName               | Codename of the browser of the signer.                                                                                                                                                                                               |
| browserVersion                | version of the browser of the signer.                                                                                                                                                                                                |
| cookieEnabled                 | Is Cookie enabled in the browser of the signer.                                                                                                                                                                                      |
| browserLanguage               | Language in the browser of the signer.                                                                                                                                                                                               |
| browserLanguage               | Operation System of the signer.                                                                                                                                                                                                      |
| userAgent                     | userAgent of the signer.                                                                                                                                                                                                             |
| userConsentEmailDetails Block | This Block the details of the email sent by the signer.This block has data only when signer has signed using iacceptwithemail.                                                                                                       |
| emailId                       | Email Id of the signer which he/she used to send the consent email.                                                                                                                                                                  |
| name                          | Name of the signer which he/she used to send the consent email.                                                                                                                                                                      |
| subject                       | Subject of the consent email sent by the signer.                                                                                                                                                                                     |
| consentText                   | Consent Text specified by the signer in the consent email.                                                                                                                                                                           |
| body                          | Body of the consent email sent by the signer.                                                                                                                                                                                        |
| contractId                    | ContractId specified in the subject of the consent email sent by the signer.                                                                                                                                                         |
| valid                         | This is a flag which denotes whether the consent email sent by the signer is valid or not.Possible Values is "true" or "false"                                                                                                       |
| valid                         | This is a flag which denotes whether the consent email sent by the signer is valid or not.Possible Values is "true" or "false"                                                                                                       |
| negativeWordsFound            | The List of Negative Words found in the consent email sent by the signer                                                                                                                                                             |
| mailReceiveTime               | Time at which consent email of the signer is received by Signzy System                                                                                                                                                               |
| signerMatchData Block         | These block returns the match results of the data given in the signer block and data returned by Aadhaar in the Digital Signature Certificate.                                                                                       |
| nameMatch                     | Name Match Result matches the name given in the signer block with name returned by Aadhaar in Digital Signature Certificate (Possible values Direct Match/Partial Match/No Match).                                                   |
| pincodeMatch                  | Pincode Match Result matches the pincode given in the signer block with pincode returned by Aadhaar in Digital Signature Certificate (Possible values Match/No Match).                                                               |
| genderMatch                   | Gender Match Result matches the gender given in the signer block with gender returned by Aadhaar in Digital Signature Certificate (Possible values Match/No Match).                                                                  |
| dobMatch                      | Date of Birth Match Result matches the year of date of birth given in the signer block with year of birth returned by Aadhaar in Digital Signature Certificate (Possible values Match/No Match).                                     |
| uidLastFourDigitsMatch        | uidLastFourDigitsMatch matches the gender last signerUidLastFourDigits given in the signer block with the last 4 digits of the aadhaar Number returned by Aadhaar in Digital Signature Certificate (Possible values Match/No Match). |
| deletedSignerdetail           | This block contains the details of all the signers who were deleted.                                                                                                                                                                 |
| OTP Block                     | The data of the signer if signer has done otp based consent.                                                                                                                                                                         |
| verified                      | Whether signer did a successful otp verification(Possible values "true"/"false").                                                                                                                                                    |
| message                       | Message which denotes whether signer did a successful otp verification(Possible values "otp verified successfully"/"wrong otp entered").                                                                                             |
| transactionId                 | Unique TransactionId of the otp sent to the user.                                                                                                                                                                                    |
| Video Block                   | The data of the signer if signer has recorded his/her video.                                                                                                                                                                         |
| video                         | URL of the video recorded of the signer.                                                                                                                                                                                             |
| transactionId                 | Unique TransactionId of the video recorded of the signer.                                                                                                                                                                            |
| matchImage                    | Face in the IdCard Image which has to be matched with the video.                                                                                                                                                                     |
| randomNumber                  | Random number shown to the signer to speak during the video verification(additionalVerification : \['idvideo']).                                                                                                                     |
| seconds                       | Time intervals at which face has been tracked in the video.                                                                                                                                                                          |
| Video Forensics Block         | The data comes when the signer selects video verification.                                                                                                                                                                           |
| videoFaceMatch block          | Face Match Block denotes the data of the face match between id and video.                                                                                                                                                            |
| videoImages                   | Snap shots taken from video at different time interval.                                                                                                                                                                              |
| finalMatchImage               | Image which the user will pass for verifing the person in the video.                                                                                                                                                                 |
| coVariance                    | percentage of coVariance between the different face match scores of the snap shot image of the video to the match image.                                                                                                             |
| matchPercentage               | Average percentage of face match between different snap shots of the video to the match image .                                                                                                                                      |
| videoMatch block              | Video Match Block denotes the data of the audio match between the random number shown to the signer and number the signer spoke.                                                                                                     |
| matchAudioScore               | Percentage of match between the Signzy verifiable string and the string spoken by user in the video.                                                                                                                                 |
| timestamp block               | UNIX Timestamp recorded of the signer at different time intervals of the signer.                                                                                                                                                     |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/18ea19ff72850ea2b56e)
