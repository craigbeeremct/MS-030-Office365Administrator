# Course MS-030 - Replacement Labs

These instructions must be used in the virtual environment provided by learnondemand.net.

## TOC ##

[Setup](#lab-setup)

[Module 1](#Module-1-planning-and-provisioning-office-365)



## Lab Setup

### Exercise 1: Download lab files

1. Connect to **LON-CL1**. Sign on as **ADATUM\Administrator**.

1. *Follow the instructions in the LODS instructions.*

### Exercise 2: DNS Registration

1. Connect to **LON-DC1**.

1. *Follow the instructions in the LODS instructions.*

1. Record the full domain name (`adatumXXXXXX.onelearndns.com`), name server name (`NSadatumXXXXXX`), and public IP address in the text boxes in the LODS interface.



## Module 1: Planning and Provisioning Office 365

### Exercise 1: Explore the various administrative portals.

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

### Exercise 2: Add a DNS domain

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

### Exercise 1: Create users using the portal

1. Connect to **LON-CL1**. Sign on as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** portal and sign in using the supplied tenant administrator.

1. In the Navigation menu, click **Users > Active users**. 

1. Add users as follows.

    - [ ] **Lindsey**

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
    
    - [ ] **Christie**

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

    - [ ] **Amy**

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

    - [ ] **Sallie**

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

    - [ ] **Francisco**

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

    - [ ] **Holly**

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

    - [ ] **Chris**

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
    
### Exercise 2: Modify users

1. Switch to the **Microsoft 365 admin center** browser window signed in as the supplied tenant administrator.

1. In the **Active Users** list, click **Amy Santiago**.

1. Set Amy's department to Sales.

### Exercise 3: Block a user

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

### Exercise 4: Delete and undelete a user

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

### Exercise 5: Pasword Policy

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

### Exercise 6: Multifactor Authentication

TODO: https://docs.microsoft.com/en-us/azure/active-directory/authentication/tutorial-enable-azure-mfa



