
# StoreConnect NPSP Anon Household Fix

WARNING: This unmanaged package comes delivered as unsupported from StoreConnect.

The problem this solves:
When using NPSP and StoreConnect, when an order is created and the customer account does not exist, the account that gets created is not of the Household Record Type, instead, it is set to Organization. The related contact record that is then created is linked to this Organization account. When using NPSP, an “Anonymous Household” account is created when the contact is first created. These “Anonymous Household” records need to be removed and the first account record type needs to change to Household.

## Flow Overview:
- Trigger Criteria: Order Create and when the order is created by the StoreConnect Sync User.
- Changes the Record Type of the Account that was just created related to this Order to “HouseHold”
- Find the most recent Anonymous Household record created by StoreConnect Sync User.
- Delete this single Anonymous Household record that is associated with the order.

## Unmanaged Package Link:
[https://test.salesforce.com/packaging/installPackage.apexp?p0=04t92000000DhK5 ](https://test.salesforce.com/packaging/installPackage.apexp?p0=04t92000000DhK5).


## Instructions for install & configure into your sandbox:

- Install the Unmanaged Package in your sandbox.
![Install 1](/images/npsp_1a.png)
![Install 2](/images/npsp_2.png)
- Collect UserID of the StoreConnect Sync User
    - Navigate to collect StoreConnect Sync User ID.
    - Setup > Users. Find StoreConnect Sync User. 
    - In the URL when you open up the user record you can find the userid by looking for “page?address=%2F” and taking the value after that until the next “%”.
    - Collect this value, we will use it later in the flow.
    - ![Sync](/images/npsp_3.png)
- Collect Recordtypeid of the Household Account Record Type
    - Navigate to collect the Household Account Record Type.
    - Setup > Object Manager > Account > Record Types > Household Account
    - In the URL when you open up the Household Account record type you can find the record if after “/RecordTypes/” and before “/view”. 
    - Collect this value, we will use it later in the flow.
    - ![AccountRT](/images/npsp_4.png)
- Follow the steps to modify the flow for your org.
    - Setup > Flow > “SC Transfer to Household Account”
    - Steps 1 - 11 are in each image marked with a red arrow.
    - ![Flow1](/images/npsp_5.png)
    - ![Flow2](/images/npsp_6.png)
    - ![Flow3](/images/npsp_7.png)
    - ![Flow4](/images/npsp_8.png)
    - ![Flow5](/images/npsp_9.png)
    - ![Flow6](/images/npsp_10.png)
    - ![Flow7](/images/npsp_11.png)
    - ![Flow8](/images/npsp_12.png)
    - ![Flow9](/images/npsp_13.png)
- Complete an order on the store as a new customer to test.



