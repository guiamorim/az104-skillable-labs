# Lab 01 - Manage Microsoft Entra ID Identities

Lab introduction
In this lab, you learn about users and groups. Users and groups are the basic building blocks for an identity solution.
This lab requires an Azure subscription. Your subscription type may affect the availability of features in this lab. You may change the region, but the steps are written using East US.

## Lab scenario
Your organization is building a new lab environment for pre-production testing of apps and services. A few engineers are being hired to manage the lab environment, including the virtual machines. To allow the engineers to authenticate by using Microsoft Entra ID, you have been tasked with provisioning users and groups. To minimize administrative overhead, membership of the groups should be updated automatically based on job titles.
Architecture diagram

## Job skills
**Task 1:** Create and configure user accounts.<br />
**Task 2:** Create groups and add members.<br />

### Task 1: Create and configure user accounts<br />
In this task, you will create and configure user accounts. User accounts will store user data such as name, department, location, and contact information.
<br />

1. Sign in to the [Azure portal](https://portal.azure.com). To proceed to the portal, select **Cancel** on the Welcome to Azure splash screen.<br />
2. Search for and select **Microsoft Entra ID** - *Microsoft Entra ID is Azure's cloud-based identity and access management solution*.<br />
3. Select the Overview blade and then the **Manage tenants** tab.
4. Return to the **Entra ID page** by pressing back in the browser or selecting the option in the breadcrumb menu.
5. Create a new user by In the Manage blade, select **Users**; then in the New user drop-down select **Create new user**.
7. Create a new user with the following settings (*leave others with their defaults*).<br />
*On the Properties tab notice all the different types of information that can be included in the user account.*

**Setting / Value:**
- **User principal name:** az104-user1 <br />
- **Display name:** az104-user1 <br />
- **Auto-generate password:** checked <br />
- **Account enabled:** checked <br />
- **Job title (Properties tab):** IT Lab Administrator <br />
- **Department (Properties tab):** IT <br />
- **Usage location (Properties tab):** United States <br />

8. Once you have finished reviewing, select **Review + create** and then **Create**
9. Refresh the page and confirm your new user was created.


**Invite an external user**
1. In the New user drop-down, select **Invite an external user**.

**Setting / Value** <br />
- **Email:** your email address <br />
- **Display name:** your name <br />
- **Send invite message:** check the box <br />
- **Message:** Welcome to Azure and our group project <br />

2. Move to the **Properties tab**. Complete the basic information, including these fields.

**Setting / Value**
- **Job title:** IT Lab Administrator <br />
- **Department:** IT <br />
- **Usage location (Properties tab):** United States <br />

3. Select **Review + invite**, and then **Invite**.
4. Refresh the page and confirm the invited user was created. You should receive the invitation email shortly.


**Task 2: Create groups and add members** <br />
In this task, you create a group account. Group accounts can include user accounts or devices. <br />
These are two basic ways members are assigned to groups: Statically and Dynamically. <br />
- Static groups require administrators to add and remove members manually. <br />
- Dynamic groups update automatically based on the properties of a user account or device. For example, job title. <br />

1. In the Azure portal, search for and select Microsoft Entra ID. In the Manage blade, select Groups. <br />
- Expiration lets you configure a group lifetime in days. After that time the group must be renewed by the owner. <br />
- Naming policy lets you configure blocked words and add a prefix or suffix to group names. <br />

2. In the All groups blade, select **+ New group** and **create a new group**. <br />

**Setting / Value** <br />
- **Group type:** Security <br />
- **Group name:** IT Lab Administrators <br />
- **Group description:** Administrators that manage the IT lab <br />
- **Membership type:** Assigned <br />

Note: *An Entra ID Premium P1 or P2 license is required for dynamic membership. If other Membership types are available,<br /> the options will show up in the drop-down.*
 
3. Select **No owners selected**. <br />
4. In the Add owners page, search for and **select yourself** (shown in the top right corner) as the owner. <br />Notice you can have more than one owner.
5. Select **No members selected**. <br />
6. In the Add members pane, search for and **select the az104-user1** and **the guest user you invited**.  <br />Add both of the users to the group. <br />
7. Select **Create to deploy the group**. <br />
8. Refresh the page and ensure your group was created. <br />
9. Select the new group and review the Members and Owners information. <br />

## Key takeaways
- A tenant represents your organization and helps you to manage a specific instance of Microsoft cloud services for your internal and external users.
- Microsoft Entra ID has user and guest accounts. Each account has a level of access specific to the scope of work expected to be done.
- Groups combine together related users or devices. There are two types of groups including Security and Microsoft 365.
- Group membership can be statically or dynamically assigned.

## Learn more with self-paced training
[Understand Microsoft Entra ID](https://learn.microsoft.com/training/modules/create-azure-resource-manager-template-vs-code/). - Compare Microsoft Entra ID to Active Directory DS, learn about Microsoft Entra ID P1 and P2, and explore Microsoft Entra Domain Services for managing domain-joined devices and apps in the cloud.  <br />
[Create Azure users and groups in Microsoft Entra ID](https://learn.microsoft.com//training/modules/create-users-and-groups-in-azure-active-directory/). - Create users in Microsoft Entra ID. Understand different types of groups. Create a group and add members. Manage business-to-business guest accounts.  <br />
[Allow users to reset their password with Microsoft Entra self-service password reset](https://learn.microsoft.com/training/modules/allow-users-reset-their-password/). - Evaluate self-service password reset to allow users in your organization to reset their passwords or unlock their accounts. Set up, configure, and test self-service password reset.  <br />

## Extend your learning with Copilot *(For my future reference)*
Copilot can assist you in learning how to use the Azure scripting tools. Copilot can also assist in areas not covered in the lab or where you need more information. Open an Edge browser and choose Copilot (top right) or navigate to copilot.microsoft.com. Take a few minutes to try these prompts.
- What are the Azure PowerShell and CLI commands to create a security group called IT Admins? Provide the official command reference page.
- Provide a step-by-step strategy for managing users and groups in Microsoft Entra ID.
- What are the steps in the Azure portal to bulk create users and groups?
- Provide a comparison table of internal and external Microsoft Entra ID user accounts.
