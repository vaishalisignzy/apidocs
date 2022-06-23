---
description: This page contains the UI Flo
---

# The UI  Journey

BBPS UI and API journey (Postpaid)

1. GetBillerlist API is called which shows the different categories to choose from to the user After the category for Bill payment is selected, the user gets details of the service provider and his/her account.&#x20;
2. GetBillerDetails API is called here The user needs to then pass the required unique identifier (Eg. Mobile number for Mobile Postpaid payment) and other details to get the bill details.&#x20;
3. FetchBill API needs to be called for this Next, the user has to pass his details to pay the bill as selected earlier.&#x20;
4. BillPay API comes here. Payment gateway API has to be called before this to facilitate the payment if PG is required&#x20;
5. BBPS Check Payment Details API comes next in sequence to get the reference ID of the Bill payment

BBPS UI and API journey (Mobile Prepaid)&#x20;

1. GetBillerlist API is called which shows the different categories to choose from to the user After the category for Bill payment is selected as ‘MOBILE PREPAID’, the user gets details of the service provider and his/her account.&#x20;
2. GetBillerDetails API is called here On passing the mobile number while calling the&#x20;
3. Get Operator List, Circle Info, Mobile Plan Details API, the user gets the recharge details On passing the prepaid account details, the payment details are validated on calling the Validate Payment API and then the user can proceed for the payment. Next, the user has to pass his details to complete the payment.&#x20;
4. Mobile Recharge Payment API comes here. Payment gateway API has to be called before this to facilitate the payment if PG is required



![Home Page Screen:](https://lh5.googleusercontent.com/-bTXO9RLbQVfjUfBxabTTIwsyiZeE8i84I-\_1EOdBqT7z6486ZZ0HyJdwBsu8rOfS7\_fHYYTuXNkYRnttv4vH9qfFWPHuRpdNfOrrIFo\_D6PE0KIIGwTa6JEcOXV355FSmJIyubE)

![Login Page Screen](https://lh3.googleusercontent.com/SBJOHo34HD5mYM-fETzd17e\_IVR2g28HfguVzABiw7gHIcnQP8d87DN6kKIkEqsm-Eip-dV74ObaZzAVPHwcSGcmlYzXitG\_Q9NE3jYNiftlFK7UhfHdofG8avVy03ipMJhaS7UY)



![Biller List Screen](https://lh3.googleusercontent.com/zuVWfd932hEJW0uZ3otlW3z8pUqriy37K\_gpr1nMwlrtqFKPXbz\_njXMyZzGL4jcWANVTVsSrfmt3m3340CkUccqbZb85DqymxEqWTI3XW-XAmNrIdT7QiHn0UgyB0Uv4novEoqv)

![Input Account Details Screen](https://lh5.googleusercontent.com/LOD5gKxFLxoB1W77EP52TJOqYbdF9ZwtGZ4vS12mnLRuAkiueHhQGH7n5eCWr1myJ2tRWxRogrmPT4K5Lk-3\_H8TlPHEJtbzuCKtptX5silXasF6LbiiHEMK5Bc0DT9ZRpwv0wGE)

![Bill Details Screen](https://lh6.googleusercontent.com/YsNwUlXeVsHXo8X0cPCiXr6\_h0MQh96It7\_JrXDQHprway5J2\_USEz16aJmMyP1p7j9g06gakz9GfbNL2EaZ3dCmW85CYKhf7TjQI5cJmPvR\_ce1ngAi16Cnz828FfR-zc51GvFA)

![Payment Screen](https://lh3.googleusercontent.com/ImD\_ggpWz0Ej2R9NgVjxzdEMJu\_8e3Zcnuz2b83JmTqoN5rnT6nGSF8k80fvnXwT3fWZOUbOlPn6PUDi-RMfNboygqb4fDK583RqbA2AL\_57YfHQXUdsEuSb4SC2ooMDQugnVXWD)

![Transaction Confirmation Screen](https://lh6.googleusercontent.com/KpScZmR0dgcaxaaAQFvj3JYfW5QjTBNS167MOs3e8Br7cw\_Beq4Idi0YdI9DmrkFz-0ZM1-zslTWrdQgc7ggRK-Q8A8EYu\_lrxasIRFmsJacjAfUxvdVi0ys107ollZQ8einaNUQ)

![Check Transaction Status Screen](https://lh6.googleusercontent.com/xYWgKlLk9y0fhMMvyI\_RIxVSC29eBylkJqGbmmUctjv5fEFiATr1P\_ovRrYE\_UJDVfLB4SefkFei4XpURmOVaL6t-XUj02jNaliL5MhKAFDRPbfyeav5SkLDGBuuRHSo7RVmTwIW)

![Confirmation SMS](https://lh5.googleusercontent.com/bKHjuVChsQ\_h\_aET1MKpkcbvSpnqNJRcaLccjBtUb5LmBikSS1CCFmvlEySEbD4jRqVD0DtmbnIW5\_fp-Fz\_r78HmXcFy0NhSEPxyjDoZatHvXtTwDT5C1Vv0CGZ8X\_Q\_EAACjIX)
