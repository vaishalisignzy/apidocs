# 👩‍💻 Understanding the Backops users

Users with Backops access can use the portal as well as work on applications.&#x20;

{% hint style="info" %}
Backops users can vary in levels of permission.&#x20;
{% endhint %}

For example, they go through the applications and check them, taking the final call on whether to reject or accept them. Their details can be edited, and they can be deleted from the control given to them in the form of _**grants**_.

<details>

<summary>What is a Grant?</summary>

It is to give or allow the Backops users to access certain actions like

* View applications assigned to him
* Accept, reject, and move the application to drafts
* Add internal notes

and much more which we will discuss in more detail in [**Manage** **Roles.**](../settings/manage-roles/create-a-new-role/grants.md)****

</details>

There can be multiple designations and levels of access for different users within an organization.&#x20;

This can be accomplished by assigning designations and levels. You can grant each of them permission to take certain actions on applications that arrive at the backops portal.&#x20;

> You can also define the internal hierarchy of the organization. (for eg., Managers can reassign the applications and not users based on the grants that they are provided)

### Let us understand the role of Backops users in detail:

* Backops Officer enters into the Backops application
* Finds the list of applications in the dashboard and picks any one of the applications to review (It can be from pending/drafted/rejected/escalated applications)
* Taps on view details and enters into the due diligence tab of the respective application
* Checks the AML and CFT results&#x20;
* Compares the results with the documents submitted
* Results can be either safe/ unsafe(Risky)
* According to that backops user proceeds with the document
  1. If safe - no more verification or rechecks needed - user can directly proceed to further data checks
  2. If risky - The User has to notice the matches found related to the data/document submitted
* Checks the list of records that have been found by the API from the database
* Each result contains various data matches according to the document submitted
  1. Example: DOB/ Region/address/ name etc.,
* User reviews and compares the source data with the results shown
* Users can deal with two types of data matches according to the rules
  1. Data match with less risk found
  2. Data match with high risk found
* Views the overall score.
* Moves the application to the appropriate bucket (accept/draft/reject).

![Role of Backops Officer](<../.gitbook/assets/image (1).png>)
