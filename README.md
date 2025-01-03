
# StoreConnect NPSP Anon Household Fix

WARNING: This unmanaged package comes delivered as unsupported from StoreConnect.

The problem this solves:
When using NPSP and StoreConnect, when an order is created and the customer account does not exist, the account that gets created is not of the Household Recordtype, instead, it is set to Organization. The related contact record that is then created is linked to this Organization account. When using NPSP, an “Anonymous Household” account is created when the contact is first created. These “Anonymous Household” records need to be removed and the first account record type needs to change to Household.

## Flow Overview:
- Trigger Criteria: Order Create and  when the order is created by the StoreConnect Sync User.
- Changes the Record Type of the Account that was just created related to this Order to “HouseHold”
- Find the most recent Anonymous Household record created by StoreConnect Sync User.
- Delete this single Anonymous Household record that is associated with the order.

## Unmanaged Package Link:
[https://test.salesforce.com/packaging/installPackage.apexp?p0=04t92000000DhK5 ](https://test.salesforce.com/packaging/installPackage.apexp?p0=04t92000000DhK5).


## Instructions for install & configure into your sandbox:

- Install the Unmanaged Package in your sandbox.
![Install 1](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936108/media/npsp_1a.png)
![Install 2](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936131/media/npsp_2.png)
- Collect UserID of the StoreConnect Sync User
    - Navigate to collect StoreConnect Sync User ID.
    - Setup > Users. Find StoreConnect Sync User. 
    - In the URL when you open up the user record you can find the userid by looking for “page?address=%2F” and taking the value after that until the next “%”.
    - Collect this value, we will use it later in the flow.
    - ![Sync](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936145/media/npsp_3.png)
- Collect Recordtypeid of the Household Account Record Type
    - Navigate to collect the Household Account Record Type.
    - Setup > Object Manager > Account > Record Types > Household Account
    - In the URL when you open up the Household Account record type you can find the record if after “/RecordTypes/” and before “/view”. 
    - Collect this value, we will use it later in the flow.
    - ![AccountRT](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936161/media/npsp_4.png)
- Follow the steps to modify the flow for your org.
    - Setup > Flow > “SC Transfer to Household Account”
    - Steps 1 - 11 are in each image marked with a red arrow.
    - ![Flow1](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936173/media/npsp_5.png)
    - ![Flow2](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936196/media/npsp_6.png)
    - ![Flow3](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936208/media/npsp_7.png)
    - ![Flow4](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936222/media/npsp_8.png)
    - ![Flow5](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936235/media/npsp_9.png)
    - ![Flow6](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936249/media/npsp_10.png)
    - ![Flow7](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936260/media/npsp_11.png)
    - ![Flow8](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936272/media/npsp_12.png)
    - ![Flow9](https://res.cloudinary.com/hzkr6fi81/image/upload/v1735936284/media/npsp_13.png)
- Complete an order on the store as a new customer to test.



