# Course MS-030 - Replacement Labs

These instructions must be used in the virtual environment provided by learnondemand.net.

## TOC ##

Module 1: Planning and Provisioning Office 365

[Lab 1](#lab-1)

Module 2: Managing Office 365 users and groups

[Lab 2A: Using the portal](#lab-2a)

[Lab 2B: Using PowerShell](#lab-2b)

[Lab 2C: Service administrators](#lab-2c)




## Lab Setup

#### Download lab files

1. Connect to **LON-CL1**. Sign on as **ADATUM\Administrator**.

1. *Follow the instructions in the LODS instructions.*

#### DNS Registration

1. Connect to **LON-DC1**.

1. *Follow the instructions in the LODS instructions.*

1. Record the full domain name (`adatumXXXXXX.onelearndns.com`), name server name (`NSadatumXXXXXX`), and public IP address in the text boxes in the LODS interface.



## Module 1: Planning and Provisioning Office 365

### Lab 1

#### Exercise 1: Explore the various administrative portals.

1. Connect to **LON-CL1**. Sign on as **ADATUM\Administrator**.

1. Open Edge. Browse to **https://admin.microsoft.com**. This opens the **Microsoft 365 admin center** portal.

1. Sign in using the supplied tenant administrator (`admin@LODSXXXXXX.onmicrosoft.com`).

1. If asked to save the password or to stay signed in, choose **Yes**.

1. In the Navigation menu, click **… Show all**.

1. In the Navigation menu (left-hand pane), click **Users > Active users**. 

1. How many users are listed? What licences are assigned to them?

1. In the Navigation menu, click **Exchange**. This opens the **Exchange admin center** portal.

1. In the Navigation menu, click **recipients**. In the centre pane, click **mailboxes**.

1. How many mailboxes are listed? The number should match the number of active users licensed with Office 365.

1. Select the **Microsoft 365 admin center** browser tab.

1. In the Navigation menu, click **Azure Active Directory**. This opens the **Azure Active Directory admin center** portal.

1. In the navigation menu, click **Azure Active Directory**. In the **Contoso | Overview blade**, click **Users** in the **Manage** section.

1. How many accounts are listed? The number should match the number of active users.

1. Select the **Microsoft 365 admin center** browser tab.

1. In the Navigation menu, click **Health > Service health**. 

1. If there are any warnings or advisories then click on the link and read the messages.

1. In the Navigation menu, click **Security**. This opens the **Office 365 Security & Compliance** portal.

    - Note that you can open this portal by browsing to **https://protection.office.com**.
  
1. Select the **Microsoft 365 admin center** browser tab.

1. In the Navigation menu, click **Compliance**. This opens the **Microsoft 365 compliance** portal.

    - Note that you can open this portal by browsing to **https://compliance.microsoft.com**.
  
1. Select the **Microsoft 365 admin center** browser tab.

#### Exercise 2: Add a DNS domain

1. Connect to **LON-DC1**. Sign on as **ADATUM\Administrator**.

1. Open Internet Explorer. Browse to the **Microsoft 365 admin center** portal (admin.microsoft.com) and sign in using the supplied tenant administrator.

1. If asked to save the password or to stay signed in, choose **Yes**.

1. In the Navigation menu, click **Settings > Domains**. Click **Add domain**.

1. Type the provided domain name (`adatumXXXXXX.onelearndns.com`) then click **Use this domain**.

1. Select **Add a TXT record** then click **Continue**.

1. Copy the **TXT value** to the clipboard.

1. Open **DNS Manager** (**Start** > **Windows Administrative Tools** > **DNS**).

1. Create a new **Forward Lookup Zone**.

    | Setting | Value |
    | --- | --- |
    | Zone type: | Primary |
    | Store in Active Directory | Selected |
    | Replicated to | Domain controllers in the forest |
    | Zone name | The provided domain name (`adatumXXXXXX.onelearndns.com`) |
    | Dynamic updates | Allow only secure |

1. Right-click **adatumXXXXXX.onelearndns.com**, choose **Other new records…**, **Text (TXT)**.

    | Setting | Value |
    | --- | --- |
    | Record name | (Leave blank) |
    | Text | (Paste the TXT value from above) |

1. Return to the **Microsoft 365 admin center**. On the **Verify you own this domain** page, click **Verify**.

1. On the **How do you want to connect your domain?** page, click **Close**. *We will add the DNS records later*.



## Module 2: Managing Office 365 users and groups

### Lab 2A

#### Exercise 1: Create users

1. Connect to **LON-CL1**. Sign on as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** portal and sign in using the supplied tenant administrator.

1. In the Navigation menu, click **Users > Active users**. 

1. Add users as follows.

    | Setting | Value |
    | --- | --- |
    | First name | Lindsey |
    | Last name | Gates |
    | Display Name |  Lindsey Gates |
    | Username | lindsey@adatumXXXXXX.onelearndns.com |
    | Password | Pa55w.rd1234 |
    | Require the user to change their password when they first sign in | No |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | Sales |
    
    | Setting | Value |
    | --- | --- |
    | First name | Christie |
    | Last name | Thomas |
    | Display Name | Christie Thomas |
    | Username | christie@adatumXXXXXX.onelearndns.com |
    | Password | Pa55w.rd1234 |
    | Require the user to change their password when they first sign in | No |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | Sales |

    | Setting | Value |
    | --- | --- |
    | First name | Amy |
    | Last name | Santiago |
    | Display Name | Amy Santiago |
    | Username | amy@adatumXXXXXX.onelearndns.com |
    | Password | Pa55w.rd1234 |
    | Require the user to change their password when they first sign in | No |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | (Leave blank) |

    | Setting | Value |
    | --- | --- |
    | First name | Sallie |
    | Last name | McIntosh |
    | Display Name | Sallie McIntosh |
    | Username | sallie@adatumXXXXXX.onelearndns.com |
    | Password | Pa55w.rd1234 |
    | Require the user to change their password when they first sign in | No |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | Accounts |

    | Setting | Value |
    | --- | --- |
    | First name | Francisco |
    | Last name | Chaves |
    | Display Name | Francisco Chaves |
    | Username | francisco@adatumXXXXXX.onelearndns.com |
    | Password | Pa55w.rd1234 |
    | Require the user to change their password when they first sign in | No |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | Accounts |

    | Setting | Value |
    | --- | --- |
    | First name | Holly |
    | Last name | Dickson |
    | Display Name | Holly Dickson |
    | Username | holly@adatumXXXXXX.onelearndns.com |
    | Password | Pa55w.rd1234 |
    | Require the user to change their password when they first sign in | No |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | Global admin |
    | Department | IT |

    | Setting | Value |
    | --- | --- |
    | First name | Chris |
    | Last name | Breland |
    | Display Name | Chris Breland |
    | Username | chris@adatumXXXXXX.onelearndns.com |
    | Password | Pa55w.rd1234 |
    | Require the user to change their password when they first sign in | No |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | (Leave blank) |
    
#### Exercise 2: Modify users

1. Switch to the **Microsoft 365 admin center** browser window signed in as the supplied tenant administrator.

1. In the **Active Users** list, click **Amy Santiago**.

1. Set Amy's department to Sales.

#### Exercise 3: Block a user

1. Switch to the **Microsoft 365 admin center** browser window signed in as the supplied tenant administrator.

1. In the **Active Users** list, click **Francisco Chaves**.

1. Block Francisco's sign-in.

1. In Edge, open an InPrivate window. Browse to **https://portal.office.com**. 

1. Sign in as **francisco@adatumXXXXXX.onelearndns.com**, password **Pa55w.rd1234**. If asked to save the password or to stay signed in, choose **No**.

1. You wil see a "Your account has been locked" message.

1. Close the InPrivate window.

1. Select the **Microsoft 365 admin center** browser window signed in as the supplied tenant administrator.

1. In the **Active Users** list, click **Francisco Chaves**.

1. Unblock Francisco's sign-in. *Note*: THis may take up to 15 minutes to take effect. 

1. In Edge, open an InPrivate window. Sign on to the portal again as Francisco.

1. Close the InPrivate window.

#### Exercise 4: Delete and undelete a user

1. Switch to the **Microsoft 365 admin center** browser window signed in as the supplied tenant administrator.

1. In the **Active Users** list, click **Lindsey Gates**.

1. Delete Lindsey's account.

1. In Edge, open an InPrivate window. Browse to **https://portal.office.com**. 

1. Sign in as **lindsey@adatumXXXXXX.onelearndns.com**.

1. You wil see a "This username may be incorrect" message.

1. Close the InPrivate window.

1. Switch to the **Microsoft 365 admin center** browser window signed in as the supplied tenant administrator.

1. In the Navigation menu, click **Users > Deleted users**. 

1. In the **Deleted Users** list, click **Lindsey Gates**.

1. Restore the user account. Use an automatically-generated password and note down the temporary password.

1. In Edge, open an InPrivate window. Browse to **https://portal.office.com**. 

1. Sign in as **lindsey@adatumXXXXXX.onelearndns.com**, using the temporary password. Change the password to **Pa55w.rd1234**. If asked to save the password or to stay signed in, choose **No**.

1. Note that Lindsey has no apps in the list. Deleting the account removed the licence assignment.

1. Close the InPrivate window.

1. Switch to the **Microsoft 365 admin center** browser window (signed in as the supplied tenant administrator).

1. In the Navigation menu, click **Users > Active users**. 

1. In the **Active Users** list, click **Lindsey Gates**.

1. Assign an Office 365 E5 license.

#### Exercise 5: Pasword Policy

1. Switch to the **Microsoft 365 admin center** browser window signed in as the supplied tenant administrator.

1. In the Navigation menu, click **Settings > Org settings**. 

1. In the middle pane, click **Security & privacy** then click **Password expiration policy**.

1. Set 14 days before passwords expire, 14 days before a user is notified.

1. Sign out of the portal and then close Edge.

1. Open Edge, browse to **https://portal.office.com**. 

1. Sign in as **lindsey@adatumXXXXXX.onelearndns.com**, password **Pa55w.rd1234**. If asked to save the password or to stay signed in, choose **No**.

1. Note that Lindsey now has Outlook, OneDrive, etc in the list.

1. Click the Notification icon in the top right. Note the "Time to change your password" message.

1. Sign out of the portal and then close Edge.

#### Exercise 6: Multifactor Authentication

TODO: https://docs.microsoft.com/en-us/azure/active-directory/authentication/tutorial-enable-azure-mfa

#### Exercise 7: Create groups

1. Connect to **LON-CL1**. Sign on as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** portal and sign in using the supplied tenant administrator.

1. In the Navigation menu, click **Groups > Active groups**. 

1. Add groups as follows.

    | Setting | Value |
    | --- | --- |
    | Type | Security |
    | Name | Sales |
    | Description | Sales department |

    | Setting | Value |
    | --- | --- |
    | Type | Security |
    | Name | Accounts |
    | Description | Accounts department |

#### Exercise 8: Modify groups

1. In the **Active groups** list, click **Refresh**. Repeat until both Sales and Accounts are in the list.

1. In the **Active groups** list, click **Sales**. Set the members as follows.

    | Setting | Value |
    | --- | --- |
    | Owners | Lindsey Gates |
    | Members | Lindsey Gates, Christie Thomas, Amy Santiago |
    
1. In the **Active groups** list, click **Accounts**. Set the members as follows.

    | Setting | Value |
    | --- | --- |
    | Owners | Francisco Chaves |
    | Members | Sallie McIntosh, Francisco Chaves |
    
#### Exercise 9: Delete a group

1. In the **Active groups** list, click the selection circle to the left of **Accounts**. Click **Delete group**.

1. In the Navigation menu, click **Users > Active users**. Note that the user accounts for Amy, Christie and Lindsey are still present.

1. In the Navigation menu, click **Groups > Deleted groups**. Note that the Sales group does not appear. Only Microsoft 365 groups can be undeleted.


### Lab 2B

Before running the code below, you must replace the placeholder "@adatumXXXXXX.onelearndns.com" with your actual domain name.

#### Exercise 1: Create users

1. Connect to **LON-CL1**. Sign on as **ADATUM\Administrator**.

1. Using **Run as Administrator**, open **Windows PowerShell ISE**.

1. Install the latest version of the MSOnline module. 

```PowerShell
    Install-Module MSOnline -Force
```

1. Close **Windows PowerShell ISE** and open it again without using Run as administrator.

1. Connect to Office 365. Sing in as the supplied tenant administrator.

```PowerShell
    Connect-MsolService
```

1. Create the users. 

```PowerShell
    New-MsolUser –UserPrincipalName "catherine@adatumXXXXXX.onelearndns.com" –DisplayName "Catherine Richard" –FirstName "Catherine" –LastName "Richard" –Password "Pa55w.rd1234" –ForceChangePassword $false –UsageLocation "CH"

    New-MsolUser –UserPrincipalName "tameka@adatumXXXXXX.onelearndns.com" –DisplayName "Tameka Reed" –FirstName "Tameka" –LastName "Reed" -Password "Pa55w.rd1234" –ForceChangePassword $false –UsageLocation "CH"
```

#### Exercise 2: Licence users

1. List the unlicensed users.

```PowerShell
    Get-MsolUser -UnlicensedUsersOnly
```

1. Determine the available licenses.

```PowerShell
    Get-MsolAccountSku
```

1. Assign licenses. Edit the correct license name (LODSXXXXXXX:ENTERPRISEPREMIUM) before running the script.

```PowerShell
    Set-MsolUserLicense -UserPrincipalName "catherine@adatumXXXXXX.onelearndns.com" –AddLicenses "LODSXXXXXXX:ENTERPRISEPREMIUM"

    Set-MsolUserLicense -UserPrincipalName "tameka@adatumXXXXXX.onelearndns.com" –AddLicenses "LODSXXXXXXX:ENTERPRISEPREMIUM"
```

#### Exercise 3: Block a user

1. Block Catherine's sign-in.

```PowerShell
    Set-MsolUser -UserPrincipalName "catherine@adatumXXXXXX.onelearndns.com" -BlockCredential $true
```

#### Exercise 4: Delete and undelete a user

1. Delete Catherine's user account.

```PowerShell
    Remove-MsolUser -UserPrincipalName "catherine@adatumXXXXXX.onelearndns.com" 
```
1. List all deleted users. Note that Catherin's account is still licensed.

```PowerShell
    Get-MsolUser -ReturnDeletedUsers
```

1. Undelete Catherine's user account.

```PowerShell
    Restore-MsolUser -UserPrincipalName "catherine@adatumXXXXXX.onelearndns.com" 
```

1. List users.

```PowerShell
    Get-MsolUser
    Get-MsolUser -UnlicensedUsersOnly
    Get-MsolUser -ReturnDeletedUsers
```

#### Exercise 5: Bulk create users

1. Run Explorer and navigate to C:\Labfiles.

1. Right-click O365users.csv, choose Edit.

1. Replace all "yourdomain.hostdomain.com" with your domain name (adatumXXXXXX.onelearndns.com).

1. Replace all "adatumyyxxxx:ENTERPRISEPACK" with your license name (LODSXXXXXXX:ENTERPRISEPREMIUM).

1. Save the file and close Notepad.

1. Load the file and use it to create users. Note that you might run out of licenses. If so, make a note of which users were not created.

```PowerShell
    Import-Csv -Path "C:\labfiles\O365Users.csv" | ForEach-Object { New-MsolUser -UserPrincipalName $PSItem."UPN" -AlternateEmailAddresses $PSItem."AltEmail" -FirstName $PSItem."FirstName" -LastName $PSItem."LastName" -DisplayName $PSItem."DisplayName" -BlockCredential $False -ForceChangePassword $False -LicenseAssignment $PSItem."LicenseAssignment" -Password $PSItem."Password" -PasswordNeverExpires $True -Title $PSItem."Title" -Department $PSItem."Department" -Office $PSItem."Office" -PhoneNumber $PSItem."PhoneNumber" -MobilePhone $PSItem."MobilePhone" -Fax $PSItem."Fax" -StreetAddress $PSItem."StreetAddress" -City $PSItem."City" -State $PSItem."State" -PostalCode $PSItem."PostalCode" -Country $PSItem."Country" -UsageLocation $PSItem."UsageLocation" }`
```

1. List users.

```PowerShell
    Get-MsolUser
```

#### Exercise 6: Modify groups

1. Create a group.

```PowerShell
    New-MsolGroup –DisplayName "Marketing" –Description "Marketing department"
```

1. Add members.

```PowerShell
$MarketingGroup = Get-MsolGroup | Where-Object DisplayName -eq "Marketing"
$CatherineUser = Get-MsolUser | Where-Object DisplayName -eq "Catherine Richard"
$TamekaUser = Get-MsolUser | Where-Object DisplayName -eq "Tameka Reed"
Add-MsolGroupMember -GroupObjectId $MarketingGroup.ObjectId -GroupMemberType "User" -GroupMemberObjectId $CatherineUser.ObjectId
Add-MsolGroupMember -GroupObjectId $MarketingGroup.ObjectId -GroupMemberType "User" -GroupMemberObjectId $TamekaUser.ObjectId
```

1. Verify membership.

```PowerShell
Get-MsolGroupMember -GroupObjectId $MarketingGroup.ObjectId
```

#### Exercise 7: Passwords, Password Policy

1. Set password expiry back to the default values.

```PowerShell
Set-MsolPasswordPolicy -DomainName "adatum26863b.onelearndns.com" -ValidityPeriod 90 -NotificationDays 14 
```

If you wanted to do this for all your domains, you could use the following.
    
```PowerShell
Get-MsolDomain | Where-Object IsInitial -eq $false | Select-Object @{ l="DomainName"; e={$PSItem.Name} } | Set-MsolPasswordPolicy -ValidityPeriod 90 -NotificationDays 14
```

1. Reset a user's password.

```PowerShell
Set-MsolUserPassword –UserPrincipalName "tameka@adatumXXXXXX.onelearndns.com" –NewPassword "Pa55w.rd9876"
```

1. Enable password expiry for all users.

```PowerShell
Get-MsolUser | Set-MsolUser –PasswordNeverExpires $false 
```

### Lab 2C

#### Exercise 1: Setting service administrators using the portal

1. Open Edge. Browse to the **Microsoft 365 admin center** portal and sign in using the supplied tenant administrator.

1. In the Navigation menu, click **Users > Active users**. 

1. In the **Active Users** list, click **Francisco Chaves** then click **Manage roles**.

1. Select **Billing admin** (in the **Other** section). 

1. In the **Active Users** list, click **Tameka Reed** then click **Manage roles**.

1. Select **Password admin** (in the **Identity** section). 

1. In the **Active Users** list, click **Christie Thomas** then click **Manage roles**.

1. Select **User admin**.

#### Exercise 2: Setting service administrators using PowerShell

1. Assign roles.

```PowerShell
Add-MsolRoleMember –RoleName "Service Support Administrator" –RoleMemberEmailAddress "sallie@adatumXXXXXX.onelearndns.com"
Add-MsolRoleMember –RoleName "Company Administrator" –RoleMemberEmailAddress "amy@adatumXXXXXX.onelearndns.com"
```

1. Verify role membership.

```PowerShell
$role = Get-MsolRole –RoleName "Service Support Administrator"
Get-MsolRoleMember –RoleObjectId $role.ObjectId
```

```PowerShell
$role = Get-MsolRole –RoleName "Billing Administrator"
Get-MsolRoleMember –RoleObjectId $role.ObjectId
```

```PowerShell
$role = Get-MsolRole –RoleName "Company Administrator"
Get-MsolRoleMember –RoleObjectId $role.ObjectId
```


