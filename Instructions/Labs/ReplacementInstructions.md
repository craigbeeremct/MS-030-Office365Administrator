
# Course MS-030 - Replacement Labs

These instructions must be used in the virtual environment provided by learnondemand.net.


## Table of Contents

- [Lab 1: Planning and Provisioning Office 365](#lab-1-planning-and-provisioning-office-365)

   - [Admin Center Reference](#admin-center-reference)

- [Lab 2A: Managing Office 365 users and groups using the portal](#lab-2a-managing-office-365-users-and-groups-using-the-portal)

- [Lab 2B: Managing Office 365 users and groups using PowerShell](#lab-2b-managing-office-365-users-and-groups-using-powershell)

- [Lab 2C: Managing Office 365 service administrators](#lab-2c-managing-office-365-service-administrators)

- [Lab 3: Configuring client connectivity to Microsoft Office 365](#lab-3-configuring-client-connectivity-to-microsoft-office-365)

- [Lab 4: Planning and configuring directory synchronization](#lab-4-planning-and-configuring-directory-synchronization)

- [Lab 5: Planning and deploying Office 365 ProPlus](#lab-5-planning-and-deploying-office-365-proplus)

- [Lab 6: Managing Exchange Online recipients and permissions](#lab-6-managing-exchange-online-recipients-and-permissions)

- [Lab 7A: Configuring message transport in Exchange Online](#lab-7a-configuring-message-transport-in-exchange-online)

- [Lab 7B: Configuring email protection and client policies](#lab-7b-configuring-email-protection-and-client-policies)

- [Lab 8: Teams Overview](#lab-8-teams-overview)

- [Lab 9: Configuring SharePoint Online](#lab-9-configuring-sharepoint-online)

- [Lab 10: Planning and configuring an Office 365 collaboration solution](#lab-10-planning-and-configuring-an-office-365-collaboration-solution)

- [Lab 11: Planning and configuring security and compliance in ‎Office 365](#lab-11-planning-and-configuring-security-and-compliance-in-office-365)

- [Lab 12: Monitoring and troubleshooting Microsoft Office 365](#lab-12-monitoring-and-troubleshooting-microsoft-office-365)


____________________________________________________________
## Lab Setup

### DNS Registration

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. *Follow the instructions in the LODS instructions.*

1. Record the full domain name (`adatumXXXXXX.onelearndns.com`), name server name (`NSadatumXXXXXX`), and public IP address in the text boxes in the LODS interface.

### External email address

You require an external email address (for example an outlook.com or gmail.com account). The lab instructions refer to this as `alias@outlook.com`.

   This can be from any email provider, however some features (for example SharePoint Online site sharing) only work with Microsoft accounts.


____________________________________________________________
## TODO

Microsoft 365 admin center, Settings | Org settings, Organization profile, Organization information.

____________________________________________________________
## Lab 1: Planning and Provisioning Office 365

### Exercise 1: Explore the various administrative portals.

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to **https://portal.office.com**. This opens the **Office 365 home page**.

1. Sign in using the tenant owner account (`admin@LODSXXXXXXX.onmicrosoft.com`).

1. Select the Admin link. This opens the **Microsoft 365 admin center**.

1. Close Edge.

1. Open Edge. Browse to **https://admin.microsoft.com**. This opens the **Microsoft 365 admin center** directly, without having to go to the Office 365 home page first.

1. Sign in using the tenant owner account.

1. If asked to save the password or to stay signed in, choose **Yes**.

1. In the Navigation menu (left-hand pane), select **… Show all**.

1. In the Navigation menu, select **Users > Active users**. 

1. How many users are listed? What licences are assigned to them?

1. In the Navigation menu, select **Exchange**. This opens the **Exchange admin center**.

   You can open this site directly by browsing to `https://outlook.office365.com/ecp`.

1. In the Navigation menu, select **recipients**. In the centre pane, select **mailboxes**.

1. How many mailboxes are listed? The number should match the number of active users licensed with Office 365.

1. Select the **Microsoft 365 admin center** browser tab.

1. In the Navigation menu, select **Azure Active Directory**. This opens the **Azure Active Directory admin center**.

   You can open this site directly by browsing to `https://aad.portal.azure.com`.

1. In the navigation menu of the **Azure Active Directory admin center**, select **Azure Active Directory**. In the **Contoso | Overview blade**, select **Users** in the **Manage** section.

1. How many accounts are listed? The number should match the number of active users.

1. Select the **Microsoft 365 admin center** browser tab.

1. In the Navigation menu, select **Security**. This opens the old **Office 365 Security & Compliance** center.

   Note that you can open this portal by browsing to **https://protection.office.com**.
  
1. Select the **Microsoft 365 admin center** browser tab.

1. In the Navigation menu, select **Compliance**. This opens the new **Microsoft 365 Compliance** portal.

   Note that you can open this portal by browsing to **https://compliance.microsoft.com**.
  
1. Open a new tab and browse to https://compliance.microsoft.com. This opens the new **Microsoft 365 Security** portal.

1. Select the **Microsoft 365 admin center** browser tab.

### Exercise 2: Add a DNS domain

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open Internet Explorer. Browse to the **Microsoft 365 admin center** (admin.microsoft.com) and sign in using the tenant owner account.

1. If asked to save the password or to stay signed in, choose **Yes**.

1. In the Navigation menu, select **Settings > Domains**. select **Add domain**.

1. Type the provided domain name (`adatumXXXXXX.onelearndns.com`) then select **Use this domain**.

1. Select **Add a TXT record** then select **Continue**.

1. Copy the **TXT value** to the clipboard.

1. Open **DNS Manager**.

1. Create a new **Forward Lookup Zone**.

   | Setting | Value |
   | --- | --- |
   | Zone type | Primary |
   | Store in Active Directory | Selected |
   | Replicated to | Domain controllers in the forest |
   | Zone name | The provided domain name (`adatumXXXXXX.onelearndns.com`) |
   | Dynamic updates | Allow only secure |

1. Right-select **adatumXXXXXX.onelearndns.com**, choose **Other new records…**, **Text (TXT)**.

   | Setting | Value |
   | --- | --- |
   | Record name | (Leave blank) |
   | Text | (Paste the TXT value from above) |

1. Switch to the **Microsoft 365 admin center** browser window signed in as the tenant owner account.

1. On the **Verify you own this domain** page, select **Verify**.

1. On the **How do you want to connect your domain?** page, select **Close**. *We will add the DNS records later*.

### Admin Center Reference

- Microsoft 365 admin center - [https://admin.microsoft.com](https://admin.microsoft.com) or [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home)

- Microsoft 365 Compliance admin center - [https://compliance.microsoft.com](https://compliance.microsoft.com)

- Microsoft 365 Security admin center - [https://security.microsoft.com](https://security.microsoft.com)

- Office 365 Security & Compliance admin center (superseded by the above two) - [https://protection.microsoft.com](https://protection.microsoft.com)

- Microsoft Endpoint Manager admin center - [https://endpoint.microsoft.com](https://endpoint.microsoft.com)

- Azure Active Directory admin center - [https://aad.portal.azure.com](https://aad.portal.azure.com)

- Exchange Admin Center - [https://outlook/office365.com/ecp](https://outlook/office365.com/ecp)

- (Preview) Modern Exchange Admin Center - [https://admin.exchange.microsoft.com](https://admin.exchange.microsoft.com)

- SharePoint admin center - https://\<TenantName\>-admin.sharepoint.com

- Teams admin center - [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com)


____________________________________________________________
## Lab 2A: Managing Office 365 users and groups using the portal

### Exercise 1: Create users

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Users > Active users**. 

1. Add a user as follows.

   | Setting | Value |
   | --- | --- |
   | First name | Lindsey |
   | Last name | Gates |
   | Display Name |  Lindsey Gates |
   | Username | lindsey@adatumXXXXXX.onelearndns.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | Sales |
    
1. Add a user as follows.

   | Setting | Value |
   | --- | --- |
   | First name | Christie |
   | Last name | Thomas |
   | Display Name | Christie Thomas |
   | Username | christie@adatumXXXXXX.onelearndns.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | Sales |

1. Add a user as follows.

   | Setting | Value |
   | --- | --- |
   | First name | Amy |
   | Last name | Santiago |
   | Display Name | Amy Santiago |
   | Username | amy@adatumXXXXXX.onelearndns.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | (Leave blank) |

1. Add a user as follows.

   | Setting | Value |
   | --- | --- |
   | First name | Sallie |
   | Last name | McIntosh |
   | Display Name | Sallie McIntosh |
   | Username | sallie@adatumXXXXXX.onelearndns.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | Accounts |

1. Add a user as follows.

   | Setting | Value |
   | --- | --- |
   | First name | Francisco |
   | Last name | Chaves |
   | Display Name | Francisco Chaves |
   | Username | francisco@adatumXXXXXX.onelearndns.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | Accounts |

1. Add a user as follows.

   | Setting | Value |
   | --- | --- |
   | First name | Holly |
   | Last name | Dickson |
   | Display Name | Holly Dickson |
   | Username | holly@adatumXXXXXX.onelearndns.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | Global admin |
   | Department | IT |
    
### Exercise 2: Modify users

1. Switch to the **Microsoft 365 admin center** browser window signed in as the tenant owner account.

1. In the **Active Users** list, select **Amy Santiago**.

1. Set Amy's department to Sales.

### Exercise 3: Block a user

1. Switch to the **Microsoft 365 admin center** browser window signed in as the tenant owner account.

1. In the **Active Users** list, select **Francisco Chaves**.

1. Block Francisco's sign-in.

1. In Edge, open an InPrivate window and browse to **https://portal.office.com**. Sign in as Francisco. If asked to save the password or to stay signed in, choose **No**.

1. You wil see a "Your account has been locked" message.

1. Close the InPrivate window.

1. Select the **Microsoft 365 admin center** browser window signed in as the tenant owner account.

1. In the **Active Users** list, select **Francisco Chaves**.

1. Unblock Francisco's sign-in. *Note*: This may take up to 15 minutes to take effect. 

1. In Edge, open an InPrivate window and sign in to the Office portal again as Francisco.

1. Close the InPrivate window.

### Exercise 4: Delete and undelete a user

1. Switch to the **Microsoft 365 admin center** browser window signed in as the tenant owner account.

1. In the **Active Users** list, select **Lindsey Gates**.

1. Delete Lindsey's account.

1. In Edge, open an InPrivate window and browse to **https://portal.office.com**. Sign in as Lindsey.

1. You will see a "This username may be incorrect" message.

1. Close the InPrivate window.

1. Switch to the **Microsoft 365 admin center** browser window signed in as the tenant owner account.

1. In the Navigation menu, select **Users > Deleted users**. 

1. In the **Deleted Users** list, select **Lindsey Gates**.

1. Restore the user account. Use an automatically-generated password and note down the temporary password.

1. In Edge, open an InPrivate window and sign in to the Office portal again as Lindsey, using the temporary password. Change the password to **Pa55w.rd1234**. If asked to save the password or to stay signed in, choose **No**.

1. Note that Lindsey has no apps in the list. Deleting the account removed the licence assignment.

1. Close the InPrivate window.

1. Switch to the **Microsoft 365 admin center** browser window (signed in as the tenant owner account).

1. In the Navigation menu, select **Users > Active users**. 

1. In the **Active Users** list, select **Lindsey Gates**.

1. Assign an Office 365 E5 and an Enterprise Mobility + Security E5 license.

### Exercise 5: Pasword Policy

1. Switch to the **Microsoft 365 admin center** browser window signed in as the tenant owner account.

1. In the Navigation menu, select **Settings > Org settings**. 

1. In the middle pane, select **Security & privacy** then select **Password expiration policy**.

1. Set 14 days before passwords expire, 14 days before a user is notified.

1. In Edge, open an InPrivate window and browse to **https://portal.office.com**. Sign in as Lindsey.

1. Note that Lindsey now has Outlook, OneDrive, etc in the list.

1. select the Notification icon in the top right. Note the "Time to change your password" message.

1. Close the InPrivate window.

### Exercise 6: Multifactor Authentication

TODO: https://docs.microsoft.com/en-us/azure/active-directory/authentication/tutorial-enable-azure-mfa

### Exercise 7: Create groups

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Groups > Active groups**. 

1. Add a group.

   | Setting | Value |
   | --- | --- |
   | Type | Security |
   | Name | Sales |
   | Description | Sales department |

1. Add a group.

   | Setting | Value |
   | --- | --- |
   | Type | Security |
   | Name | Accounts |
   | Description | Accounts department |

### Exercise 8: Modify groups

1. In the **Active groups** list, select **Refresh**. Repeat until both Sales and Accounts are in the list.

1. In the **Active groups** list, select **Sales**. Set the members as follows.

   | Setting | Value |
   | --- | --- |
   | Owners | Lindsey Gates |
   | Members | Lindsey Gates, Christie Thomas, Amy Santiago |
    
1. In the **Active groups** list, select **Accounts**. Set the members as follows.

   | Setting | Value |
   | --- | --- |
   | Owners | Francisco Chaves |
   | Members | Sallie McIntosh, Francisco Chaves |
    
### Exercise 9: Delete a group

1. In the **Active groups** list, select **Sales**. 

1. Delete the group.

1. In the Navigation menu, select **Users > Active users**. Note that the user accounts for Amy, Christie and Lindsey are still present.

1. In the Navigation menu, select **Groups > Deleted groups**. Note that the Sales group does not appear. Only Microsoft 365 groups can be undeleted.


____________________________________________________________
## Lab 2B: Managing Office 365 users and groups using PowerShell

Before running the code below, you must replace the placeholder "@adatumXXXXXX.onelearndns.com" with your actual domain name.

### Exercise 1: Create users

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Using **Run as Administrator**, open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Install the latest version of the MSOnline module. 

   ```PowerShell
   Install-Module MSOnline -Force
   ```

1. Close **Windows PowerShell ISE** and open it again without using Run as administrator.

1. Connect to Office 365. Sing in as the tenant owner account.

   ```PowerShell
   Connect-MsolService
   ```

1. Enable Directory Synchonisation (in preperation for Lab 4).

   ```PowerShell
   Set-MsolDirSyncEnabled -EnableDirSync $true -Force
   ```

1. Create the users. 

   ```PowerShell
   New-MsolUser –UserPrincipalName "catherine@adatumXXXXXX.onelearndns.com" –DisplayName "Catherine Richard" –FirstName "Catherine" –LastName "Richard" –Password "Pa55w.rd1234" –ForceChangePassword $false –UsageLocation "CH"
   ```

   ```PowerShell
   New-MsolUser –UserPrincipalName "tameka@adatumXXXXXX.onelearndns.com" –DisplayName "Tameka Reed" –FirstName "Tameka" –LastName "Reed" -Password "Pa55w.rd1234" –ForceChangePassword $false –UsageLocation "CH"
   ```

### Exercise 2: Licence users

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
   Set-MsolUserLicense -UserPrincipalName "catherine@adatumXXXXXX.onelearndns.com" –AddLicenses "LODSXXXXXXX:ENTERPRISEPREMIUM", "LODSXXXXXXX:EMSPREMIUM"
   ```

   ```PowerShell
   Set-MsolUserLicense -UserPrincipalName "tameka@adatumXXXXXX.onelearndns.com" –AddLicenses "LODSXXXXXXX:ENTERPRISEPREMIUM", "LODSXXXXXXX:EMSPREMIUM"
   ```

### Exercise 3: Block a user

1. Block Catherine's sign-in.

   ```PowerShell
   Set-MsolUser -UserPrincipalName "catherine@adatumXXXXXX.onelearndns.com" -BlockCredential $true
   ```

### Exercise 4: Delete and undelete a user

1. Delete Catherine's user account.

   ```PowerShell
   Remove-MsolUser -UserPrincipalName "catherine@adatumXXXXXX.onelearndns.com" 
   ```
1. List all deleted users. Note that Catherine's account is still licensed.

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

### Exercise 5: Bulk create users

1. Run **Explorer** and navigate to **C:\Labfiles**.

1. Right-select **O365users.csv**, choose **Edit**.

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

### Exercise 6: Modify groups

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

### Exercise 7: Passwords, Password Policy

1. Set password expiry.

   ```PowerShell
   Set-MsolPasswordPolicy -DomainName "adatumXXXXXX.onelearndns.com" -ValidityPeriod 90 -NotificationDays 14 
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


____________________________________________________________
## Lab 2C: Managing Office 365 service administrators

### Exercise 1: Setting service administrators using the portal

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Users > Active users**. 

1. In the **Active Users** list, select **Francisco Chaves** then select **Manage roles**.

1. Select **Billing admin** (in the **Other** section). 

1. In the **Active Users** list, select **Tameka Reed** then select **Manage roles**.

1. Select **Password admin** (in the **Identity** section). 

1. In the **Active Users** list, select **Christie Thomas** then select **Manage roles**.

1. Select **User admin**.

1. Close all Edge windows.


### Exercise 2: Setting service administrators using PowerShell

1. Assign roles.

   ```PowerShell
   Add-MsolRoleMember –RoleName "Service Support Administrator" –RoleMemberEmailAddress "sallie@adatumXXXXXX.onelearndns.com"
   ```
   
   ```PowerShell
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

### Exercise 3: Test service administrators

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as Tameka.

1. In the Navigation menu, select **Users > Active users**. 

1. In the **Active Users** list, select **Jessica Jennings**.

1. Note that you cannot change group membership or contact information.

1. Reset Jessica's password. Make a note of the new password.

1. Sign out of the admin center and close Edge.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as Tameka.

1. In the Navigation menu, select **Users > Active users**. 

1. In the **Active Users** list, select **Jessica Jennings**.

1. Note that you can change group membership and contact information.

1. Add a user as follows.

   | Setting | Value |
   | --- | --- |
   | First name | Chris |
   | Last name | Breland |
   | Display Name | Chris Breland |
   | Username | chris@adatumXXXXXX.onelearndns.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | (Leave blank) |
    
1. In the **Active Users** list, select **Chris Breland**.

1. Delete Chris Breland's user account.

1. Sign out of the admin center and close Edge.



____________________________________________________________
## Lab 3: Configuring client connectivity to Microsoft Office 365 

### Exercise 1: DNS Records

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open Internet Explorer. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Settings > Domains**. 

1. select **adatumXXXXXX.onelearndns.com** then select **Continue setup**.

1. On the Add DNS Records screen, select **Exchange and Exchange Online Protection**, **Skype for Business**, and **Intune and Mobile Device Management for Microsoft 365**.

1. Open **DNS Manager**. 

1. Add the following records, copying the values from the web browser.

   1. Mail Exchanger (MX).
      | Setting | Value |
      | --- | --- |
      | Host or child domain | (Leave blank) |
      | Fully qualified domain name (FQDN) of mail server | AdatumXXXXXX-onelearndns-com.mail.protection.outlook.com |
      | Mail server priority | 0 |

   1. CNAME.
      | Setting | Value |
      | --- | --- |
      | Alias name | autodiscover |
      | Fully qualified domain name (FQDN) for target host | autodiscover.outlook.com |

   1. Text (TXT).
      | Setting | Value |
      | --- | --- |
      | Record name | (Leave blank) |
      | Text | v=spf1 include:spf.protection.outlook.com -all

   1. CNAME.
      | Setting | Value |
      | --- | --- |
      | Alias name | sip |
      | Fully qualified domain name (FQDN) for target host | sipdir.online.lync.com |

   1. CNAME.
      | Setting | Value |
      | --- | --- |
      | Alias name | lyncdiscover |
      | Fully qualified domain name (FQDN) for target host | webdir.online.lync.com |

   1. Service Location (SRV).
      | Setting | Value |
      | --- | --- |
      | Service | _sip |
      | Protocol | _tls |
      | Priority | 100 |
      | Weight | 1 |
      | Port number | 443 |
      | Host offering this service | sipdir.online.lync.com |

   1. Service Location (SRV).
      | Setting | Value |
      | --- | --- |
      | Service | _sipfederationtls |
      | Protocol | _tcp |
      | Priority | 100 |
      | Weight | 1 |
      | Port number | 5061 |
      | Host offering this service | sipfed.online.lync.com |

   1. CNAME.
      | Setting | Value |
      | --- | --- |
      | Alias name | enterpriseregistration |
      | Fully qualified domain name (FQDN) for target host | enterpriseregistration.windows.net |

   1. CNAME.
      | Setting | Value |
      | --- | --- |
      | Alias name | enterpriseenrollment |
      | Fully qualified domain name (FQDN) for target host | enterpriseenrollment.manage.microsoft.com |

1. Switch to the **Microsoft 365 admin center** browser window signed in as the tenant owner account.

1. select **Continue** then **Done**. Correct any mismatches reported.

### Exercise 2: Office 365 connectivity analyzer

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to **https://testconnectivity.microsoft.com**. This opens the **Microsoft Remote Connectivity Analyzer**.

1. In the navigation menu, select **Office 365**. In the main pane, select **Help Identify My Issue with Exchange DNS**.

1. Enter your domain name (adatumXXXXXX.onelearndns.com), select **Office 365 (Default)**, then select **Perform Test**.

1. Verify that there are no errors.

1. In the navigation menu, select **Office 365**. In the main pane, select **Help Identify My Issue with Lync DNS**.

1. Enter Francisco's sign-in address (francisco@adatumXXXXXX.onelearndns.com), select **Office 365 (Default)**, then select **Perform Test**.

1. Verify that there are no errors.

1. In the navigation menu, select **Office 365**. In the main pane, select **Outlook Connectivity**.

1. Enter Francisco's sign-in address and password, select **Use Autodiscover to detect server settings**, select the **I understand** box, then select **Perform Test**.

1. Verify that there are no errors.

1. In the navigation menu, select **SARA Client**. Download and install the tool.

### Exercise 3: Office 365 Support and Recovery Assistant

1. In the **Microsoft Support and Recovery Assistant**, select **Outlook** then select **Next**. 

1. Select **I need help setting up my Office 365 email in Outlook** then select **Next**.

1. Select **Yes** to **Is this the affected machine?** then select **Next**.

1. Enter the email address and password of the tenant owner account (admin@LODSXXXXXX.onmicrosoft.com) then select **Next**.

1. Note any recommendations then close the tool.

### Exercise 4: Connecting Office 2016 clients

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Run Outlook 2016. 
   | Setting | Value |
   | --- | --- |
   | Your name | MOD Administrator |
   | E-mail address | admin@LODSXXXXXX.onmicrosoft.com |

1. Send an e-mail to Francisco.

1. Create a meeting and invite Francisco.

1. On **LON-CL2**, signed in as **.\Student**.

1. Run Outlook 2016. 
   | Setting | Value |
   | --- | --- |
   | Your name | Francisco Chaves |
   | E-mail address | francisco@adatumXXXXXX.onelearndns.com |

1. Reply to MOD Administrator's email.

1. Accept MOD Administrator's meeting request.



____________________________________________________________
## Lab 4: Planning and configuring directory synchronization

### Exercise 1: Preparing for Directory Synchonisation

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open **Active Directory Domains and Trusts**.

1. In the console tree, right-select **Active Directory Domains and Trusts [LON-DC1.Adatum.com]** and choose **Prperties**.

1. Add a UPN suffix of **adatumXXXXXX.onelearndns.com**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**. 

1. Set the UPN suffixes for all users.

   ```PowerShell
   Get-ADUser –Filter * -Properties SamAccountName | ForEach-Object { Set-ADUser $PSItem -UserPrincipalName ($PSItem.SamAccountName + "@adatumXXXXXX.onelearndns.com" ) }
   ```

### Exercise 2: Create issues 

1. Run the break script.

   ```PowerShell
   cd C:\Labfiles
   .\CreateProblemUsers.ps1
   ```

1. Verify that five accounts were updated - Klemen, Lara, Logan, Holly and Maj. Note that IdFix will not detect the issues with Holly and Maj.

### Exercise 3: Resolve issues

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

   Not LON-DC1 - it does not have the .NET Framework required.

1. Open Edge. Browse to **https://github.com/microsoft/idfix**.

1. Scroll down to the selectOnce Launch heading and select the launch link. Install and run the app.

1. In IdFIx, select Query on the toolbar. Five issues will be shown.

1. Issue: An Dung Dao's account has spaces in the User Principal Name.

   Resolution: In the Action column, select **EDIT**.

1. Issue: DefaultAccount has a blank Display Name.

   Resolution: In the Action column, select **EDIT**.

1. Issue: Klemen Sic's account has two @ symbols in the User Principal Name.

   Resolution: In the Action column, select **EDIT**.

1. Issue: Ngoc Bich Tran's account has spaces in the User Principal Name.

   Resolution: In the Action column, select **EDIT**.

1. Issue: Lara Raisic and Logan Boyle have the same email adrress. IdFIx doesn't display Logan's account (a bug?).

   Resolution: In the Update column, enter **larar@adatum.com**. In the Action column, select **EDIT**.

1. In the toolbar, select Apply.

1. In the toolbar, select Query. Verify that no issues are listed.

1. Close IdFix.

### Exercise 4: Configure the Azure AD tenant

1. Open **Windows PowerShell ISE** or **Windows PowerShell**. 

1. Connect to Office 365. Sign in as the tenant owner account.

   ```PowerShell
   Connect-MsolService
   ```

1. Get DirSync information.

   ```PowerShell
   Get-MsolCompanyInformation | fl *sync*
   ```

   Verify that DirectorySynchronizationEnable is True. If it is not then run the following and check again.

   ```PowerShell
   Set-MsolDirSyncEnabled -EnableDirSync $true -Force
   ```

1. Do not close PowerShell, it will be used later.

### Exercise 5: Download and install AD Connect, set up synchronization

1. On **LON-DS1**, signed in as **ADATUM\Administrator**.

1. Open Internet Explorer. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Azure Acive Directory**. 

1. In the navigation menu of the **Azure Active Directory admin center**, select **Azure Active Directory**. In the **Contoso | Overview blade**, select **Azure AD Connect** in the **Manage** section.

1. select **Download Azure AD Connect**. Download and install the tool.

1. In the Microsoft Azure Active Directory Connect tool, select **Customize**.

1. At the **Install required components** screen, select **Install**.

1. At the **User-sign-in** screen, select **Password Hash Synchronization** and select **Next**.

1. At the **Connect to Azure AD** screen, sign in using the tenant owner account and select **Next**.

1. At the **Connect your directories** screen, select **Add directory**. 

1. At the **Ad forest account** screen, select **Create new AD account**, sign in using **ADATUM\Administrator** and select **OK**.

1. At the **Connect your directories** screen, verify that Adatum.com has been added, then select **Next**. 

1. At the **Azure AD sign-in configuration** screen, select **Continue without matching all UPN suffixes to verified domains** and select **Next**.

1. At the **Domain and OU filtering** screen, choose **Sync selected domains and OUs** and select only the **IT** OU, then select **Next**.

1. At the **Uniquely identifying your users** screen, select **Next**.

1. At the **Filter users and devices** screen, select **Next**.

1. At the **Optional features** screen, select **Next**.

1. At the **Ready to congure** screen, select **Install**.

1. At the **Configuration complete** screen, select **Exit**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**. 


### Exercise 6: Verify that synchronization was successful

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Switch to the PowerShell session where Connect-MsolService was run.

1. Get DirSync information.

   ```PowerShell
   Get-MsolCompanyInformation | fl *sync*
   ```

   Verify that all the properties have values (in particular that LastDirSyncTime has a date and time).

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Users > Active users**. 

1. Verify that there are more users than before.

1. Check that Vera Pace (IT) does have an account.

1. Check that Arturs Priede (Research) does not have an account.

1. Check that Ada Russell (Marketing) does not have an account.


### Exercise 7: Modify synchronisation

1. On **LON-DS1**, signed in as **ADATUM\Administrator**.

1. Open **Azure AD Connect**. select **Configure**.

1. At the **Additional tasks** screen, select **Customize synchronisation options** and select **Next**.

1. At the **Connect to Azure AD** screen, sign in using the tenant owner account and select **Next**.

1. At the **Connect your directories** screen, select **Next**. 

1. 1. At the **Domain and OU filtering** screen, select the **Research** OU, then select **Next**.

1. At the **Optional features** screen, select **Next**.

1. At the **Ready to congure** screen, select **Configure**.

1. At the **Configuration complete** screen, select **Exit**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**. 

1. Perform a manual sync.

   ```PowerShell
   Start-AdSyncSyncCycle Delta
   ```

### Exercise 8: Verify that synchronization was successful

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Users > Active users**. 

1. Check that Arturs Priede (a researcher) does have an account.


### Exercise 9: Managing AD DS users and groups

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open **Active Directory Users and Computers**.

1. In the console tree, select **Research**.

1. Create a user.

   | Setting | Value |
   | --- | --- |
   | First name | Perry |
   | Last name | Brill |
   | Full name | Perry Brill |
   | User logon name | perry@adatumXXXXXX.onelearndns.com |
   | User logon name (pre-Windows 2000) | ADATUM\perry |
   | Password | Pa55w.rd |
   | Password options | Unselected |

1. Create a group.

   | Setting | Value |
   | --- | --- |
   | Group name | Project Team |
   | Group name (pre-Windows 2000) | Project Team |
   | Scope | Universal |
   | Type | Security |

1. Right select **Vera Pace**, choose **Move**. Move the account to the **Marketing** OU.

1. Right-select **Research** security group, select **Properties**.

1. Remove **Vera Pace** and **Tia Zecirevic** from the group. Add **Ada Russell* to the group.

1. In the console tree, select **Marketing**.

1. Right select **Ada Russell**, choose **Move**. Move the account to the **Research** OU.


### Exercise 10: Synchronise

1. On **LON-DS1**, signed in as **ADATUM\Administrator**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**. 

1. Perform a manual sync.

   ```PowerShell
   Start-AdSyncSyncCycle Delta
   ```

### Exercise 11: Verify that synchronization was successful

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Users > Active users**. 

1. Check that Vera Pace (IT) does not have an account.

1. Check that Ada Russell (Marketing) does have an account.

1. In the Navigation menu, select **Groups > Active groups**. 

1. Check that Project Team is present.

1. Check that Ada is a member of the Research group and that Vera and Tia are not.


#### Exercise 12: Assign licenses

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Users > Active users**. 

1. Select **Filter**, **Licensed users**.

1. Tick all the users imported earlier using the csv file (some or all of Nona, Jessica, Misty, Elvis, Leila, Sheri, Mickey and Leanna).

1. Select **Manage licenses**. Remove all product licenses from the selected users.

1. Select **Filter**, **Unlicensed users**.

1. Tick Ada, Arturs, August and Cai.

1. Select **Manage licenses**. Add **Enterprise Mobility + Security E5** and **Office 365 E5** licenses to the selected users, with a **Usage location** of **Switzerland**.


#### Exercise 13: Enable Seamless SSO (*Optional*)

#### Task 1: Azure AD Connect

1. On **LON-DS1**, signed in as **ADATUM\Administrator**.

1. Open **Azure AD Connect**. select **Configure**.

1. At the **Additional tasks** screen, select **Change user sign-in** and select **Next**.

1. At the **Connect to Azure AD** screen, sign in using the tenant owner account and select **Next**.

1. At the **User sign-in** screen, select the **Enable single sign-on**, then select **Next**.

1. At the **Enable single-sign-on** screen, select **Enter credentials**. Sign in as **ADATUM\Administrator**. select *Next*.

1. At the **Ready to congure** screen, select **Configure**.

1. At the **Configuration complete** screen, select **Exit**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**. 

1. Perform a manual sync.

   ```PowerShell
   Start-AdSyncSyncCycle Delta
   ```

#### Task 2: Group Policy

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open **Group Policy Management**.

1. Edit *Default Domain Policy*. Navigate to  **User Configuration** > **Preferences** > **Window Settings** > **Registry**.

1. Create a new **Registry item**.

   | Setting | Value |
   | --- | --- |
   | Action | Update |
   | Hive | HKEY_CURRENT_USER |
   | Key Path | software\Microsoft\Windows\CurrentVersion\Internet Settings\ZoneMap\Domains\microsoftazuread-sso.com\autologon |
   | Value name | https |
   | Value type | REG_DWORD |
   | Value data | 1 |

1. Close **Group Policy Management Editor**.


____________________________________________________________
## Lab 5: Planning and deploying Office 365 ProPlus

### Exercise 1: Preparing an Office 365 ProPlus managed installation

#### Task 1: Download the Office 365 deployment tool

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open **Server Manager**. Choose **File and Storage Services** > **Shares**, **Tasks**, **New Share**. 

1. Create a shared folder.

   | Setting | Value |
   | --- | --- |
   | File share profile | SMB Share - Quick |
   | Share location | Select by volume C: |
   | Share Name | OfficeProPlus |
   | Enable access-based enumeration | Off |
   | Allow caching of share | Off |
   | Encrypt data access | Off |
   | NTFS Permissions | Disable inheritance, leave entries as default |
   | Share permissions | Authenticated Users: Full Control |

1. Open Internet Explorer. Browse to **https://www.microsoft.com/en-us/download/details.aspx?id=49117**. Download and run the tool. Store the extracted files in **C:\Shares\OfficeProPlus**.

#### Task 2: Modify an Office 365 ProPlus installation

1. Run File Explorer. Browse to **C:\Shares\OfficeProPlus**.

1. Right-select **configuration-Office365-x64.xml**, choose **Edit**.

1. Edit the XML as follows.

   ```XML
   <Configuration>
     <Add SourcePath="\\LON-DC1\OfficeProPlus" OfficeClientEdition="64" Channel="Monthly" AllowCdnFallback="TRUE">
       <Product ID="O365ProPlusRetail">
         <Language ID="en-us" />
       </Product>
     </Add>
     <Property Name="PinIconsToTaskbar" Value="TRUE" />
     <Updates Enabled="TRUE" Channel="Monthly" />
     <Logging Level="Standard" Path="\\LON-DC1\OfficeProPlus" />
   </Configuration>
   ```

1. Save the file as **"AdatumConfiguration.xml"**. Including the double-quotes in Notepad will stop Notepad from appending.txt to the file name.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**. 

1. Download the setup files.

   ```PowerShell
   cd C:\Shares\OfficeProPlus
   .\setup.exe /download \\LON-DC1\OfficeProPlus\AdatumConfiguration.xml
   ```

   This download takes several minutes to complete. COntinue with the next task and leave the download in the background.

### Exercise 2: Managing user-driven Office 365 ProPlus installations

#### Task 1: Managing user rights to install Office 365 ProPlus

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Users > Active users**. 

1. select **Lindsey Gates**. On a **Licenses and Apps** section, deselect **Microsoft 365 apps for enterprise**. 

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Office 365 home page** (https://portal.office.com) and sign in as **abbi@adatumXXXXXX.onelearndns.com**. This is an AD DS account so the password is **Pa55w.rd**.

   Note that Abbi has no apps in the list and no option to install Office 365 apps (the orange link at the top right).

1. Sign out from the portal. Close Edge.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **lindsey@adatumXXXXXX.onelearndns.com**.

   Note that Lindsey has Outlook and OneDrive and the other apps, because she has an Office 365 license. She does not have the option to install Office 365 apps, because we deslected this.

1. Sign out from the portal. Close Edge.

#### Task 2: Installing Office 365 ProPlus from the Office 365 portal

1. Open Edge. Browse to the **Office 365 home page** and sign in as **amy@adatumXXXXXX.onelearndns.com**.

   Note that Amy has Outlook and OneDrive and the other apps the option to install Office 365 apps.

1. select **Install Office** then select **Office 365 apps**. Download and run the tool.

   *This installation takes several minutes to complete. Continue with the next task and leave the download in the background.*

### Exercise 3: Managing centralized Office 365 ProPlus installations

#### Task 1: Verify ODT download

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Verify that the ODT download has completed without errors.

1. Run File Explorer. Browse to **C:\Shares\OfficeProPlus**.

   Note the Office folder containing the installation source files.

#### Task 2: Install Office 365 apps

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Using **Run as Administrator**, open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Install Office 365 apps.

   ```PowerShell
   \\LON-DC1\OfficeProPlus\setup.exe /configure \\LON-DC1\OfficeProPlus\AdatumConfiguration.xml
   ```

1. Wait until the installation has finished on both **LON-CL3** and **LON-CL4**.

#### Task 2: Verify installation

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open **Word**. Sign in as Amy.

1. At the **Stay signed in to all your apps** screen, select **No, sign in to this app only**.

1. Create a document. Save it to **OneDrive - Contoso** (OneDrive for Business).

1. Close Word.

1. Open **Outlook**. Sign in as **Amy.

1. Send an e-mail to Sallie.

1. Create a meeting and invite Sallie.

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Open **Word**. Sign in as Sallie.

1. At the **Stay signed in to all your apps** screen, select **No, sign in to this app only**.

1. Create a document. Save it to **Documents**. 

   Note that OneDrive for Business is not set up for Sallie, because the installation was done as ADATUM\Administrator. 

1. Close Word.

1. Open **Outlook**. Sign in as Sallie

1. Reply to Amy's e-mail.

1. Accept Amy's meeting request.

1. Leave Outlook running on LON-CL3 and LON-CL4. They will be used in later labs.



____________________________________________________________
## Lab 6: Managing Exchange Online recipients and permissions

### Exercise 1: Configuring Exchange Online recipients

#### Task 1: Exchange admin center

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Exchange admin center** and sign in using the tenant owner account. 

1. In the Navigation menu, select **recipients**. In the centre pane, select **mailboxes**.

   Note the mailboxes for the licensed users.

1. In the centre pane, select **groups**.

   Note the default groups. 

1. select the **down arrow** button next to **New Microsoft 365 group**.

   Note that the Exchange admin center allows you to create four types of group: Microsoft 365, distribution, Mail-enabled security, and dynamic distribution.

#### Task 2: Connect to Exchange Online with Windows PowerShell

1. Open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Enter a credential. Sign in as the tenant owner account.

   ```PowerShell
   $Credential = Get-Credential
   ```

1. Connect to Exchange Online.

   ```PowerShell
   $PSSession = New-PSSession -ConfigurationName "Microsoft.Exchange" -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $Credential -Authentication "Basic" -AllowRedirection
   Import-PSSession $PSSession -DisableNameChecking
   ```

1. Verify connectivity.

   ```PowerShell
   Get-AcceptedDomain
   Get-Mailbox
   ```

#### Task 3: Create groups and assign members

1. Create distribution groups.

   ```PowerShell
   New-DistributionGroup -Name "IT2" -Members holly -DisplayName "IT 2"
   New-DistributionGroup -Name "Development" -Members catherine, tameka -DisplayName "Development"
   New-DistributionGroup -Name "Sales" -Members lindsey, christie -DisplayName "Sales"   Get-DistributionGroup
   ```

#### Task 4: Create resource mailboxes

1. Create resource mailboxes.

   ```PowerShell
   New-Mailbox -Name "Conference Room" -DisplayName "Conference Room" -Room -Alias "conferenceroom" 
   Set-Mailbox -Identity "Conference Room" –ResourceCapacity 25
   ```

   ```PowerShell
   New-Mailbox -Name "Demonstration Laptop" -DisplayName "Demonstration Laptop" –Equipment -Alias "demonstrationlaptop"
   ```

1. Set auto-accept.

   ```PowerShell
   Get-Mailbox | ft name, recipienttype*
   ```

   ```PowerShell
   Get-Mailbox -RecipientTypeDetails RoomMailbox | Set-CalendarProcessing -AutomateProcessing AutoAccept
   ```

   ```PowerShell
   Get-Mailbox -RecipientTypeDetails EquipmentMailbox | Set-CalendarProcessing -AutomateProcessing AutoAccept
   ```

#### Task 5: Test resource mailboxes.

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open Outlook, signed in as Amy.

1. Create a meeting. Invite Francisco, Demonstration Laptop and Conference Room.

1. Wait for the "accepted" messages from Demonstration Laptop and Conference Room.

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Open Outlook, signed in as Sallie.

1. Create a meeting at the same time as Amy's meeting. Select the Scheduling Assistant tab. 

   Invite Francisco, Demonstration Laptop and Conference Room. Note that Francisco's time shows as Tentative and Demonstration Laptop and Conference Room show as Busy.

   Send the meeting request.

1. Wait for the "declined" messages from Demonstration Laptop and Conference Room.

### Exercise 2: Configuring role-based access control

#### Task 1: Assign users to built-in role groups

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Swith to Edge connected to the Exchange admin center.

1. In the Navigation menu, select **permissions**. In the centre pane, select **admin roles**.

1. select **Organization Management**, then select **Edit** (the pencil icon).

1. Under **Members**, Select **Add** (the plus icon).

1. Add **Holly**.

#### Task 2: Create a new admin role and assign a user to it

1. Switch to PowerShell ISE or PowerShell connected to Exchange Online.

1. Enable customization of the Exhange Online tenant.

   ```PowerShell
   Enable-OrganizationCustomization
   ```

1. Create a new role group and add a member.

   ```PowerShell
   New-RoleGroup -Name "Branch Office Admins" -Roles "Mail Recipients", "Distribution Groups", "Move Mailboxes", "Mail Recipient Creation" 
   Add-RoleGroupMember "Branch Office Admins" -Member Christie
   ```

1. Swith to Edge connected to the Exchange admin center.

1. In the Navigation menu, select **permissions**. In the centre pane, select **admin roles** then select **Refresh** (the circled arrows icon).

1. Verify that Branch Office Admins is present.



____________________________________________________________
## Lab 7A: Configuring message transport in Exchange Online

### Exercise 1: Configuring message-transport settings

#### Task 1: Create a custom send and receive connector to enforce TLS

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Exchange admin center** and sign in using the tenant owner account. 

1. In the Exchange admin center navigation menu, select **mail flow**. In the centre pane, select **connectors**.

1. select **New** (the plus icon).

   | Setting | Value |
   | --- | --- |
   | From | Office 365 |
   | To | Partner organization |
   | Name | Humongous Insurance Outgoing |
   | When do you want to use this connector? | Only when email messages are sent to these domains: humongousinsurance.com |
   | How do you want to route email messages? | Use the MX record |
   | How should Office 365 connect? | Always use Transport Layer Security, Issued by a trusted CA |
   | Validate this connector | Yes, to postmaster@humongousinsurance.com, but note that this will fail |

1. select **New** (the plus icon).

   | Setting | Value |
   | --- | --- |
   | From | Partner organization |
   | To | Office 365 |
   | Name | Humongous Insurance Incoming |
   | How do you want to identify the partner organization? | Use the sender's domain |
   | What sender domain? | humongousinsurance.com |
   | What security restrictions do you want to apply? | Reject email messages if they aren’t sent over TLS |

#### Task 2: Create transport rules

1. In the Navigation menu, select **mail flow**. In the centre pane, select **rules**.

1. select the **down arrow** button next to the plus icon, choose **Apply disclaimers…**

   | Setting | Value |
   | --- | --- |
   | Name | A. Datum disclaimer |
   | Apply this rule if… | The recipient is located… Outside the organization |
   | Do the following… | Append the disclaimer… |
   | Edit text | \<hr /\>Disclaimer goes here. |
   | Fall back to action | Wrap |
   | Audit this rule with severity level | Low |
   | Choose a mode for this rule | Enforce |

1. select the **down arrow** button next to the plus icon, choose **Send messages to a moderator…**

   | Setting | Value |
   | --- | --- |
   | Name | IT2 Moderation |
   | Apply this rule if… | The recipient is a member of… IT 2 |
   | Do the following… | Forward the message for approval to… MOD Administrator |
   | Audit this rule with severity level | Medium |
   | Choose a mode for this rule | Enforce |

#### Task 3: Verify transport rules

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open **Outlook**, signed in as Amy.

1. Send an e-mail to alias@outlook.com.

1. Send an email to Holly.

1. Open a web browser and sign in to alias@outlook.com  and verify the disclaimer has been added.

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open **Outlook 2016**, signed in as MOD Administrator.

1. Approve Amy's e-mail message to Holly.

#### Task 4: Create a journal rule for members of the research department

1. Switch to Edge running the Exchange admin center.

1. In the navigation menu, select **compliance management**. In the centre pane, select **journal rules**.

1. Next to **Send undeliverable journal reports to**, select **Select address**. Select **MOD Administrator**

1. select **New** (the plus icon).

   | Setting | Value |
   | --- | --- |
   | Send journal reports to | journal@humongousinsurance.com |
   | Name | Development journalling | 
   | If the message is sent to or received from… | A specific user or group… Development |
   | Journal the following messages… | All messages |


____________________________________________________________
## Lab 7B: Configuring email protection and client policies

### Exercise 1: Configuring email protection

#### Task 1: Configure the malware filter

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Exchange admin center** and sign in using the tenant owner account. 

1. In the navigation menu, select **protection**. In the centre pane, select **malware filter**.

1. select **Default**, and then select **Edit** (the pencil icon).

   | Setting | Value |
   | --- | --- |
   | Do you want to notify recipients if their messages are quarantined? | Yes and use custom notification text |
   | Custom notification text | Malware has been detected. Please wait to be contacted by the IT team. |
   | Sender notifications | Both internal senders and external senders |
   | Notify administrator about undelivered messages from internal senders | Admin@adatumXXXXXX.onelearndns.com |
   | Notify administrator about undelivered messages from external senders | Admin@adatumXXXXXX.onelearndns.com |

#### Task 2: Configure the connection filter

1. In the navigation menu, select **protection**. In the centre pane, select **connection filter**.

1. select **Default**, and then select **Edit** (the pencil icon).

   | Setting | Value |
   | --- | --- |
   | IP Block list | Add 191.161.0.0/24 |
   | Enable safe list | Selected |

#### Task 3: Configure the spam filter

1. In the navigation menu, select **protection**. In the centre pane, select **spam filter**.

1. select **Default**, and then select **Edit** (the pencil icon).

   | Setting | Value |
   | --- | --- |
   | Spam | Move message to Junk Email folder |
   | High confidence spam | Quarantine message |

1. select **New** (the plus icon).

   | Setting | Value |
   | --- | --- |
   | Name | Sales spam policy |
   | Spam | Prepend subject line with text. |
   | High confidence spam | Move message to Junk Email folder |
   | Prepend subject line with this text | Junk: |
   | Applied to *(scroll to bottom)* | If the recipient is a member of… Sales |

#### Task 4: Test the spam-filter settings *(optional)*

*This feature sometimes take time to be implemented. Come back to this task later.*

1. Open a web browser and sign in to your external address.

1. Create a new message to lindsey@adatumXXXXXX.onelearndns.com.

1. Copy and paste the following into the body of the message and then send.

   ```
   XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
   ```

1. Repeat the above, to francisco@adatumXXXXXX.onelearndns.com.

1. Switch to the Edge tab running  **Office 365 Security & Compliance**.

1. In the navigation pane, select **Threat management > Review**. In the center pane, select **Quarantine**.

1. Review the quarantined messages.


### Exercise 2: Configuring client access policies

#### Task 1: Configure an Outlook Web App policy

1. Switch to the Edge tab running **Exchange admin center**.

1. In the navigation menu, select **permissions**. In the centre pane, select **Outlook Web App policies**.

1. select **New** (the plus icon).

   | Setting | Value |
   | --- | --- |
   | Name | Limited features |
   | Instant messaging | Not selected |
   | Text messaging | Not selected |
   | Unified messaging | Not selected |
   | LinkedIn contact sync | Not selected |
   | Journaling | Not selected |
   | Direct File Access | Not selected |

1. In the navigation menu, select **recipients**. In the centre pane, select **mailboxes**.

1. select **Sallie McIntosh**, then select **Edit** (the pencil icon).

1. On the **mailbox features** tab, next to Email Connectivity, Outlook on the web: Enabled, select **View details**. Assign the Limited features policy.

1. Open **Outlook 2016**, signed in as MOD Administrator.

1. Send a message to Sallie, attaching the csv files in C:\Labfiles.

   *This feature sometimes take time to be implemented. Come back to this task later.*

1. In Edge, open an InPrivate window and browse to **https://portal.office.com**. Sign in as Sallie. If asked to save the password or to stay signed in, choose **No**.

1. Open the e-mail from MOD Administrator. 

#### Task 2: Configure mobile-device access

1. Switch to the Edge tab running **Exchange admin center**.

1. In the navigation menu, select **mobile**. In the centre pane, select **mobile device access**.

1. select **edit** (right-hand side).

   | Setting | Value |
   | --- | --- |
   | When a mobile device that isn't managed by a rule or personal exemption connects to Exchange | Quarantine |
   | Select administrators to receive email messages when a mobile device is quarantined | MOD Administrator |

#### Task 3: Configure a mailbox policy for mobile devices

1. In the navigation menu, select **mobile**. In the centre pane, select **mobile device mailbox policies**.

1. select **Default (default)**, and then select **Edit** (the pencil icon).

   | Setting | Value |
   | --- | --- |
   | Require a password | Selected |
   | Allow simple passwords | Selected |
   | Minimum password length | 6 |



____________________________________________________________
## Lab 8: Teams Overview

*Do the lab in LODS. It is reasonably well-written.*



____________________________________________________________
## Lab 9: Configuring SharePoint Online

### Exercise 1: Configuring SharePoint Online settings

#### Task 1: Configure settings

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **SharePoint admin center** and sign in using the tenant owner account.

1. In the **SharePoint admin center**, select **Settings** then select **Site storage limits**

1. Verify that Site storage limits is set to **Automatic**.

1. In the **SharePoint admin center**, select **Policies > Sharing**. Verify that both SharePoint and OneDrive are set to **Most permissive**.

#### Task 2: Configure user profiles

1. In the **SharePoint admin center**, select **More features**. In the centre pane, under **User profiles** select **Open**.

1. select ** Manage user profiles**. 

1. Enter "Ada", select **Find**. Edit Ada's profile.

1. Set the **Manager** to **MOD Administrator**.

1. Close the browser tab and select **Open** again. *This is because many SharePoint central admin pages have no breadcrumb trail.*

1. select **Setup My Sites**.

1. Under **My Site Cleanup**, set the **Secondary owner** to **MOD Administrator**. select **OK** (bottom-right).

1. Close the browser tab.

#### Task 3: Configure apps

1. In the **SharePoint admin center**, select **More features**. In the centre pane, under **Apps** select **Open**.

1. Select **Configure Store settings**. Set **Should Apps for Office from the store be able to start when documents are opened in the browser?** to **No**.

### Exercise 2: Creating and configuring SharePoint Online site collections

#### Task 1: Create a site collection using the SharePoint admin center

1. In the **SharePoint admin center**, select **Sites > Active Sites**, then select **+ Create**.

1. Create a new **Team site**.

   | Setting | Value |
   | --- | --- |
   | Site name, email address, address | Marketing |
   | Group owner | MOD Administrator |
   | Language | English |
   | Privacy settings | Private |
   | Time zone | Pacific Time (US and Canada) |
   | Site description | Marketing department |
   | Addition owners | (None) |
   | Members | (None) |

1. Select the new site's name then select **Sharing**

1. Set **Site concent can be shared with** to **Anyone**.

#### Task 2: Create a site collection using Windows PowerShell

   In the script below, replace *LODSAXXXXXX* with your tenant details (for example, LODSA1234567).

1. Open Edge. Browse to **https://www.microsoft.com/en-us/download/details.aspx?id=35588**. Download and install the x64 version of the tool.

1. Run **Windows PowerShell ISE** or **Windows PowerShell**.

1. Enter a credential. Sign in as the tenant owner account.

   ```PowerShell
   $Credential = Get-Credential
   ```

1. Connect to SharePoint Online. 

   ```PowerShell
   Connect-SPOService –Url https://LODSAXXXXXX-admin.sharepoint.com -Credential $Credential
   ```

1. Verify connectivity.

   ```PowerShell
   Get-SpoSite
   ```

1. Create a new site.

   ```PowerShell
   New-SPOSite -Url https://LODSAXXXXXX.sharepoint.com/sites/AcctsProj -Owner admin@LODSAXXXXXX.onmicrosoft.com -StorageQuota 500 -NoWait -Template PROJECTSITE#0 –Title "Accounts Project"
   ```

#### Task 3: Configure permissions on the site collections

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. In the **SharePoint admin center**, select **Sites > Active Sites**, then select the **Site name** column of **Marketing**.

1. Under **Permissions**, **Additional Admins**, select **Manage**. Add **Tameka**.

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **tameka@adatumXXXXXX.onelearndns.com**.

1. Select SharePoint. Note that Tameka has no sites listed.

1. Open a new browser tab. Browse to  https://LODSAXXXXXX.sharepoint.com/sites/marketing.

1. select **Not following** and wait for the link to change to "Following".

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Open a new browser tab. Browse to  https://LODSAXXXXXX.sharepoint.com/sites/marketing. Sign in as **catherine@adatumXXXXXX.onelearndns.com**. 

   This should fail. Catherine's account is blocked (from a previous lab).

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. Unblock Catherine's account.

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Open a new browser tab. Browse to  https://LODSAXXXXXX.sharepoint.com/sites/marketing. Sign in as **catherine@adatumXXXXXX.onelearndns.com**. 

1. In the **You need permission to access this site** box, enter some text and request access.

1. Close Edge.

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Switch to the **SharePoint** browser tab and refresh the page. Marketing will appear in the **Following* list.

1. Switch to the **Marketing - Home** browser tab.

1. Select **Settings** (the cog icon), **Site permissions**, **Advanced permissions settings**.

1. Select **Show access requests and invitations**. **Aprove** Catherine's request.

1. Select **Home**.

1. Select **Settings** (the cog icon), **Site permissions**, **Advanced permissions settings**.

1. select **Marketing Members** then **New**. 

1. Invite Francisco.

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to  https://LODSAXXXXXX.sharepoint.com/sites/marketing. Sign in as **catherine@adatumXXXXXX.onelearndns.com**. 

   Catherine has acess to the site.

1. Sign out Catherine and close Edge.

1. Open Edge. Browse to  https://LODSAXXXXXX.sharepoint.com/sites/marketing. Sign in as **francisco@adatumXXXXXX.onelearndns.com**. 

   Francisco has access to the site.

1. Sign out Francisco and close Edge.

### Exercise 3: Configuring and verifying external user sharing

#### Task 1: Configure a site collection for external user sharing

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **SharePoint admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Sites > Active sites**. 

1. Select **Policies**, **External Sharing**. Set **Site content can be shared with:** **Anyone**.

1. Open a new browser tab. Browse to  https://LODSAXXXXXX.sharepoint.com/sites/AcctsProj.

1. Select **Share** (top-right).

1. Invite alias@outlook.com.

1. Select the **Documents** collection. Create a **Word document** called **Budgets**.
 
1. Select **Share** (top-right). Select **Anyone with the link can view**. Copy the link.

1. Open Outlook on the Web in a new browser tab. 

1. Send  an e-mail to Alias@outlook.com with a subject of "Document link" and the link pasted into the message body.

#### Task 2: Verify external user sharing

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Close all Edge windows.

1. Open Edge. Open the e-mail client for alias@outlook.com.

1. Open the "MOD Administrator wants to share Accounts project" e-mail and select **Go To Accounts Project**.

1. Verify that the site loads.

1. Open the "Document link" e-mail and select **Budgets.docx**.

1. Verify that the document loads.

1. Close all Edge windows.

 
____________________________________________________________
## Lab 10: Planning and configuring an Office 365 collaboration solution

### Exercise 2: Configuring OneDrive for Business

#### Task 1: Enable OneDrive for Business synchronization (cloud-only users)

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open **Word**. 

1. Create a document and save it to **OneDrive - Contoso**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **amy@adatumXXXXXX.onelearndns.com**.

1. Select **OneDrive**. Verify that the new document is listed.

1. Open **File Explorer**. 

1. Select **OneDrive**. Sign in as **amy@adatumXXXXXX.onelearndns.com**. 

1. Once OneDrive synchronisation is complete, select **OneDrive - Contoso**. Verify that the new document is listed.

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Open **Word**. 

1. Select **Account**. Sign out administrator@adatumXXXXXX.onelearndns.com and sign in as **sallie@adatumXXXXXX.onelearndns.com**. 

1. Under **Connected Services**, add **Storage > OneDrive for Business**. Sign in as **sallie@adatumXXXXXX.onelearndns.com**. 

1. Create a document and save it to **OneDrive - Contoso**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **sallie@adatumXXXXXX.onelearndns.com**.

1. Select **OneDrive**. Verify that the new document is listed.

1. Open **File Explorer**. 

1. Select **OneDrive**. Sign in as **sallie@adatumXXXXXX.onelearndns.com**. 

1. Once OneDrive synchronisation is complete, select **OneDrive - Contoso**. Verify that the new document is listed.


#### Task 2: Share files with other users

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Open **File Explorer**. 

1. Select **OneDrive - Contoso**.

1. Create a folder called **Tailspin Project**. Right-select **Tailspin Project**, choose **Share**. Select **Anyone with the link can edit**. Send the link to **Amy Santiago**.

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Run **Outlook**.

1. Open the "Sallie McIntosh shared the folder" e-mail and select **Tailspin Project**.

1. Verify that the folder loads (in Edge).

#### Task 3: Enable OneDrive for Business synchronization (synced users) (*Optional*)

If Seamless SSO has been set up then the AD DS users will not need to provide passwords to sign in to Office 365 resources.

1. On **LON-CL3**, signed in as **ADATUM\Ada**.

1. Open **Word**. 

1. Select **Account**. If required, sign in as **ada@adatumXXXXXX.onelearndns.com**. 

1. Create a document and save it to **OneDrive - Contoso**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **ada@adatumXXXXXX.onelearndns.com**.

1. Select **OneDrive**. Verify that the new document is listed.

1. Open **File Explorer**. 

1. Select **OneDrive**. Sign in as **ada@adatumXXXXXX.onelearndns.com**. 

1. Once OneDrive synchronisation is complete, select **OneDrive - Contoso**. Verify that the new document is listed.

1. On **LON-CL4**, signed in as **ADATUM\Cai**.

1. *Repeat the above steps.*

*Note*: Why is the OneDrive for Business folder called "OneDrive - Contoso"? Because the tenant name is "Contoso".

Microsoft 365 admin center, Settings | Org settings, Organization profile, Organization information.


### Exercise 3: Configuring Microsoft 365 groups

#### Task 1: Configure a private Microsoft 365 group using the portal

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Groups > Active groups**. 

1. Add a group.

   | Setting | Value |
   | --- | --- |
   | Type | Microsoft 365 |
   | Name | ADatum Marketing |
   | Description | A. Datum Corporation Marketing team |
   | Owners | MOD Administrator, Holly Dickson |
   | Group email address | adatummarketing@adatumXXXXXX.onelearndns.com |
   | Privacy | Private |
   |Create a team for this group | Selected |

1. *Refresh* the list until ADatum Marketing appears.

1. Select **ADatum Marketing**. Add a member, select **Amy** and **Cai**. 

#### Task 2: Configure a public Office 365 group using PowerShell

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Enter a credential. Sign in as the tenant owner account.

   ```PowerShell
   $Credential = Get-Credential
   ```

1. Connect to Exchange Online.

   ```PowerShell
   $PSSession = New-PSSession -ConfigurationName "Microsoft.Exchange" -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $Credential -Authentication "Basic" -AllowRedirection
   Import-PSSession $PSSession -DisableNameChecking
   ```

1. Create a Microsoft 365 group.

   ```PowerShell
   New-UnifiedGroup –DisplayName "Planning Group" -Alias "PlanningGroup" –EmailAddresses "planninggroup@adatumXXXXXX.onelearndns.com" -Owner "MOD Administrator" -Members "Francisco" -AccessType Public
   ```

1. Add additional owners.

   ```PowerShell
   Add-UnifiedGroupLinks "Planning Group" –Links "Holly Dickson" –LinkType Owner
   ```

   Note the "Only Members can be Owners of a group. Please add 'holly' first as members before adding them as owners." error message.

1. Add additional members.

   ```PowerShell
   Add-UnifiedGroupLinks "Planning Group" –Links "Sallie McIntosh", "Holly Dickson" –LinkType Member
   ```

1. Add additional owners.

   ```PowerShell
   Add-UnifiedGroupLinks "Planning Group" –Links "Holly Dickson" –LinkType Owner
   ```

1. List groups and members.

   ```PowerShell
   Get-UnifiedGroup
   Get-UnifiedGroup | fl *name
   Get-UnifiedGroup "Planning Group" | Get-UnifiedGroupLinks -LinkType Member
   Get-UnifiedGroup "Planning Group" | Get-UnifiedGroupLinks -LinkType Owner
   ```

#### Task 3: Explore the Office 365 group components

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **amy@adatumXXXXXX.onelearndns.com**.

1. Select **Outlook**. 

1. Note the "You've joined the ADatum Marketing group" e-mail.

1. In the navigation pane, select **ADatum Marketing** (scroll down).

1. Send an e-mail to the group.

1. In the navigation pane, select **Discover groups** (scroll down).

1. Search for and join **Planning Group**.

   The group is public, so Amy does not need permission or approval to join the group.

1. In the navigation pane, select **Planning Group** (scroll down).

1. Send an e-mail to the group.

1. Open **Outlook**. Sign in as **amy@adatumXXXXXX.onelearndns.com**, choose **No, sign in to this app only**.

1. In the navigation pane, select **Planning Group**. 

1. Open **Teams**. Sign in as **amy@adatumXXXXXX.onelearndns.com**, choose **No, sign in to this app only**.

1. In the **Teams** list, select **Adatum Marketing**.

1. In the **Activity feed**, note the "MOD added you to ADatum Marketing" message.

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **sallie@adatumXXXXXX.onelearndns.com**.

1. Select **Outlook**. 

1. Note that there is no "You've joined the Planning Group group" e-mail (because Sallie was added using powerShell). **TODO**

1. In the navigation pane, select **Planning Group** (scroll down).

1. Send an e-mail to the group.

1. Open **Outlook**. Sign in as **sallie@adatumXXXXXX.onelearndns.com**, choose **No, sign in to this app only**.

1. In the navigation pane, select **Planning Group**. 

1. Open **Teams**. Sign in as **sallie@adatumXXXXXX.onelearndns.com**, choose **No, sign in to this app only**.

1. Note that there is no Planning Group team.

1. Select **Join or create a team**, then **Create team**, then  **Create from… An existing Microsoft 365 group or team**.

1. No groups are listed, because Sallie is not an owner of any groups.

1. Sign out of Teams.

1. Open **Teams**. Sign in as **holly@adatumXXXXXX.onelearndns.com**, choose **No, sign in to this app only**.

1. Select **Join or create a team**, then **Create team**, then  **Create from… An existing Microsoft 365 group or team**, then **Microsoft 365 group**.

1. Select **Planning Group** and select **Create**.

1. Sign out of Teams.



 
____________________________________________________________
## Lab 11: Planning and configuring security and compliance in ‎Office 365

### Exercise 1: Azure Information Protection 

#### Task 1: Install the Azure Information Protection client

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Run Ineternet Explorer. Browse to **https://www.microsoft.com/en-us/download/details.aspx?id=53018**, the Azure Information Protection unified labeling client.

1. Download **AzInfoProtection_UL.exe** and save it to **C:\Shares\OfficeProPlus**.

   Note that there is a msi download available for centralised software deployment.

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Run\
**\\LON-DC1\OfficeProPlus\AzInfoProtection_UL.exe**

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Run\
**\\LON-DC1\OfficeProPlus\AzInfoProtection_UL.exe**

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Run\
**\\LON-DC1\OfficeProPlus\AzInfoProtection_UL.exe**

#### Task 2: Configure Azure Information Protection

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 Compliance** admin center and sign in using the tenant owner account.

1. In the Navigation menu, select **Solutions > Information protection**. 

  Note that sensitivity labels can also be modified in the Office 365 Security & Compliance admin center (Classification > Sensitivity labels) and the Microsoft 365 security admin center (Classification > Sensitivity labels).

1. If you see a message to turn on the ability to process content in Office online files, then select **Turn on now**.

1. Select **+Create a label**.

   | Setting | Value |
   | --- | --- |
   | Name | PII |
   | Description for users | Personal Identifiable Information |
   | Description for admins | Personal Identifiable Information |
   | Encryption | None |
   | Content Marking | On |
   | Add a watermark | On |
   | Watermark text | Personal Identifiable Information (PII) |
   | Font size | 10 |
   | Font color | Red |
   | Text laoyt | Diagonal |
   | Add a header | Off |
   | Add a footer | Not Off |
   | Auto-labelling for Office apps | On |
   | Detect content that matches these conditions | Document contains New Zealand Inland Revenue number |
   | When content matches these conditions | Automatically apply the label |
   | Display this message to users when the label is applied | Personal Identifiable Information (PII) was detected |

1. Select **Publish labels*. This creates a policy.

   | Setting | Value |
   | --- | --- |
   | Sensitivity labels to publish | All |
   | Publish to users and groups | All |
   | Apply this label by default | None |
   | Users must provide justification to set a lower classification label | Selected |
   | Require users to apply a label to their email or documents | Not selected |
   | Provide users with a link to a custom help page | Selected |
   | Custom help page | https://docs.microsoft.com/en-us/azure/information-protection/faqs |
   | Policy name | ADatum PII |
   | Policy description | A. Datum Corporation Personal Identifiable Information (PII) policy |

#### Task 3: Create protected content (cloud-only user)

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to **https://lodsXXXXXXX.sharepoint.com/sites/adatummarketing**. Sign in as Amy.

1. Follow the site.

1.. Select the Documents library. Note the files and folders present.

1. Open **Word**. 

1. Open **Accounts** and verify that Office ProPlus is signed in as Amy and that OneDrive - Contoso and Sites - Contoso are both under Connected Services.

1. If prompted to sign in to Microsoft Azure Information Protection then sign in as **Amy**.

1. Create a new document. Enter the following text into the document.\
Memo to HR.\
Alex Wilbur's IRD number is 21-234-567.

   *Note: This number was generated (2 then 123456 then the correct checksum digit). Any resemblance to an actual entity is accidental.*

1. Save the document to the **Documents** library of the **ADatum Marketing** SharePoint site.

   Note: If the Sites location in the Sav As dialog shows "There are no sites to show right now" then Office has not yet cached the SharePoint Sites. In this case, select Browse and enter https://lodsXXXXXXX.sharepoint.com/sites/adatummarketing in the address bar.

1. Word should automatically apply the PII policy.

  *It should, but often doesn't. I can't find anything on the web for why it might not work. Watch this space, I guess.*

#### Task 3: Create protected content (AD DS user)

1. On **LON-CL4**, signed in as **ADATUM\Cai**.

*Repeat the above steps.*



____________________________________________________________
## Lab 12: Monitoring and troubleshooting Microsoft Office 365

### Exercise 1: Monitoring Office 365

#### Task 1: Send an email to a nonexistent domain

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open **Outlook**, signed in as **Amy**.

1. Send an email to **user@alt.none** with a subject of **Test email to nonexistent domain**.

1. Open the "Delivery has failed" message.

1. Copy the grey body text (from "Diagnostic information for administrators" to the end) to the clipboard.

1. Open Edge. Browse to **https://testconnectivity.microsoft.com**.

1. Select **Message Analyzer**.

1. Paste the text, select **Analyze headers**.

1. Review the results, in particular the first header, that contains "DNS domain … does not exist."

#### Task 2: Send an email to a nonexistent user

1. Send an email to **difflop1248999@outlook.com** with a subject of **Test email to nonexistent user**.

1. Open the "Delivery has failed" message.

1. Copy the grey body text (from "Diagnostic information for administrators" to the end) to the clipboard.

1. Open Edge. Browse to **https://testconnectivity.microsoft.com**.

1. Select **Message Analyzer**.

1. Paste the text, select **Analyze headers**.

1. Review the results, in particular the first header, that contains "Mailbox unavailable."

#### Task 3: Analyse Mail Flow using the portal

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Office 365 Security & Compliance Center** and sign in using the tenant owner account.

   *Note*: Message Trace is also available in the Modern Exchange Admin Center, but not in the Microsoft 365 Compliance center or the Microsoft 365 Security center. *At the time of writing, anyway…*

1. In the navigation pane, select **Mail flow > Message trace**.

1. select **Start a trace**.

   | Setting | Value |
   | --- | --- |
   | By these people | Amy |
   | To these people | All recipients |
   | Within this time range | In the last 6 hours |

1. Review the message trace search results. In particular, review the two failed messages from Amy. 

   The message detail pane does not allow you to copy the message headers in the same way we did above.

1. Select **Export results > Export loaded results**.

1. Open the downloaded csv file. Note how little information is included.

#### Task 4: Analyse Mail Flow using PowerShell.

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Enter a credential. Sign in as the tenant owner account.

   ```PowerShell
   $Credential = Get-Credential
   ```

1. Connect to Exchange Online.

   ```PowerShell
   $PSSession = New-PSSession -ConfigurationName "Microsoft.Exchange" -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $Credential -Authentication "Basic" -AllowRedirection
   Import-PSSession $PSSession -DisableNameChecking
   ```

1. View the message trace.

   ```PowerShell
   Get-MessageTrace -Page 1 -PageSize 10
   ```

1. View message trace details.

   ```PowerShell
   Get-MessageTrace -Page 1 -PageSize 10 | fl *address, *id, subject
   ```

   Copy the MessageTraceId of the "Test email to nonexistent user" message.

   ```PowerShell
   Get-MessageTraceDetail -MessageTraceId "\<paste\>" -RecipientAddress "difflop1248999@outlook.com" 
   ```

### Exercise 2: Monitoring service health and analyzing reports

#### Task 1: View Office 365 service health

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in using the tenant owner account.

1. In the Navigation menu, select **Health > Service health**. 

1. If there are any warnings or advisories then select on the link and read the messages.

1. In the Navigation menu, select **Health > Message center**. 

1. Review the content.

1. In the Navigation menu, select **Reports > Usage**. 

1. Review the content. Note the "Date as of" - these reports are 48 hours behind the current time. 

1. In Edge, open a new tab. Browse to the **Microsoft 365 security center**.

1. In the Navigation menu, select **Reports**. 

1. Review the content.

1. In Edge, open a new tab. Browse to the **Microsoft 365 Compliance Center**.

1. In the Navigation menu, select **Reports**. 

1. Review the content.





