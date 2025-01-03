
# StoreConnect NPSP Anon Household Fix

WARNING: This unmanaged package comes delivered as unsupported from StoreConnect.

## The problem this solves:
When using NPSP and StoreConnect, when an order is created and the customer account does not exist, the account that gets created is not of the Household Recordtype, instead, it is set to Organization. The related contact record that is then created is linked to this Organization account. When using NPSP, an “Anonymous Household” account is created when the contact is first created. These “Anonymous Household” records need to be removed and the first account record type needs to change to Household.

## Flow Overview:
- Trigger Criteria: Order Create by the StoreConnect Sync User.
- Changes the Record Type of the Account that was just created related to this Order to “HouseHold”
- Find the most recent Anonymous Household record created by StoreConnect Sync User.
- Delete this single Anonymous Household record that is associated with the order.

## Unmanaged Package Link:
[https://test.salesforce.com/packaging/installPackage.apexp?p0=04t92000000DhK5 ](https://test.salesforce.com/packaging/installPackage.apexp?p0=04t92000000DhK5).


## Instructions to install & configure into your sandbox:

- Install the Unmanaged Package in your sandbox.
- Collect UserID of the StoreConnect Sync User
    - Store in these instructions to reference later.
- Collect Recordtypeid of the Household Account Record Type
    - Store in these instructions to reference later.
- Find the flow named “StoreConnect: NPSP Anon Household Fix”. Open flow. Save a new version.
- Modify the entry criteria of the flow to replace the “OwnerId” value with your StoreConnect Sync Userid. 
- Modify the “Change Record Type of Account” element. 
    - Replace the RecordTypeId value with your Account Household RecordTypeId.
- Modify the “Get AnonHousehold” element. 
    - Replace the RecordTypeId value with your Account Household RecordTypeId.. 
    - Replace CreatedById with the StoreConnect Sync Userid
- Save & Activate.
- Complete an order on the store as a new customer to test.
- Review results in org.


