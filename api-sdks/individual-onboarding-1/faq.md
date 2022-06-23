# FAQ

**Q1. What is the utility of 'Delete verification data' in individual onboarding docs?**Ans: Requestid along with the all the data which has been verified by the client will be deleted.

**Q2. What is the utility of 'reprocess verification data API' in individual onboarding docs?**Ans: If, in the first verification response any of the APIs did not respond then user will rerun with the same request id to get the entire verification response.

**Q3. Is verification of PAN, Aadhaar and Bank sequential or parallel?**Ans: The verification calls happen in parallel.

**Q4. How much time does it take on an average for the upstream APIs to return a success/failure response?**Ans: Average time 20-25 seconds.

**Q5. What time difference should we keep between calling the 'save' API and the 'get' API?**Ans: Average time difference we should keep between calling the "Save" API and the "get" API is 50-60 seconds.

**Q6. Will there be any difference in APIs and upstream services between the test environment and production environment?**Ans: The difference is only in access credentials. API path and the upstream system is same as it is in test env. The only thing will be changing is the API endpoint (production hostname).

**Q7. How will I get the input data for verification?**Ans: Before using VE, you have to get the data that needs to be verified. Now, to get the data you can use our extraction APIs and fetch APIs(ROC/Non- ROC). or you can input the data into our verification engine manually.

**Q8. What are the other way to get the verification data?**Ans: You can use our Get Verification data API.
