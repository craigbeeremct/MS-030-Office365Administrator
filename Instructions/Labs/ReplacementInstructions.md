# Course MS-030 - Replacement Labs

These instructions must be used in the virtual environment provided by learnondemand.net.

## TOC ##

[Setup](#Lab Setup)

[Module 1](#Module 1: Planning and Provisioning Office 365)

[Module 2](#Module 2: Managing Office 365 users and groups)

## Lab Setup

### Exercise 1: Download lab files

1. Connect to **LON-CL1**.

1. *Follow the instructions in the LODS instructions.*

### Exercise 2: DNS Registration

1. Connect to **LON-DC1**.

1. *Follow the instructions in the LODS instructions.*

1. Record the full domain name (`adatumXXXXXX.onelearndns.com`), name server name (`NSadatumXXXXXX`), and public IP address in the text boxes in the LODS interface.

## Module 1: Planning and Provisioning Office 365

### Exercise 1: Explore the various administrative portals.

1. Connect to **LON-CL1**.

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

1. Connect to **LON-DC1**.

1. Open Internet Explorer. Browse to **https://admin.microsoft.com**.

1. Sign in using the supplied tenant administrator (`admin@LODSXXXXXX.onmicrosoft.com`).

1. If asked to save the password or to stay signed in, choose **Yes**.

1. In the Navigation menu, click **Settings > Domains**. Click **Add domain**.

1. Type the provided domain name (`adatumXXXXXX.onelearndns.com`). Click **Use this domain**.

1. Select **Add a TXT record**. Click **Continue**.

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

1. Connect to **LON-CL1**.

1. Open Edge. Browse the **Microsoft 365 admin center** portal.

1. Sign in using the supplied tenant administrator.

1. In the Navigation menu (left-hand pane), click **Users > Active users**. 

1. Add users as follows. Make a note of the automatically generated passwords.

    - [ ] Lindsey.

    | Setting | Value |
    | --- | --- |
    | First name | Lindsey |
    | Last name | Gates |
    | Display Name |  Lindsey Gates |
    | Username | lindsey@adatumXXXXXX.onelearndns.com |
    | Password | Auto-generate |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | Sales |
    
    - [ ] Christie.

    | Setting | Value |
    | --- | --- |
    | First name | |
    | Last name | |
    | Display Name | |
    | Username | @adatumXXXXXX.onelearndns.com |
    | Password | Auto-generate |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | Sales |

    | Setting | Value |
    | --- | --- |
    | First name | |
    | Last name | |
    | Display Name | |
    | Username | @adatumXXXXXX.onelearndns.com |
    | Password | Auto-generate |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | Sales |

    | Setting | Value |
    | --- | --- |
    | First name | |
    | Last name | |
    | Display Name | |
    | Username | @adatumXXXXXX.onelearndns.com |
    | Password | Auto-generate |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | Sales |

    | Setting | Value |
    | --- | --- |
    | First name | |
    | Last name | |
    | Display Name | |
    | Username | @adatumXXXXXX.onelearndns.com |
    | Password | Auto-generate |
    | Location | Switzerland |
    | Licenses | Office 365 E5 |
    | Roles | User |
    | Department | Sales |

    



