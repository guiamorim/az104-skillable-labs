Lab 03 - Manage Governance via Azure Policy
===========================================

Lab introduction
----------------

In this lab, you learn how to implement your organization’sgovernance plans. You learn how Azure policies can ensure operationaldecisions are enforced across the organization. You learn how to useresource tagging to improve reporting.

This lab requires an Azure subscription. Your subscription type mayaffect the availability of features in this lab. You may change theregion, but the steps are written using **East US**.

Estimated timing: 30 minutes
----------------------------

Lab scenario
------------

Your organization's cloud footprint has grown considerably in thelast year. During a recent audit, you discovered a substantial number ofresources that do not have a defined owner, project, or cost center. Inorder to improve management of Azure resources in your organization,you decide to implement the following functionality:

*   apply resource tags to attach important metadata to Azure resources
    
*   enforce the use of resource tags for new resources by using Azure policy
    
*   update existing resources with resource tags
    
*   use resource locks to protect configured resources
    

Interactive lab simulations
---------------------------

> Note: The lab simulations that were previously provided have been retired.

Architecture diagram
--------------------

Job skills
----------

*   Task 1: Create and assign tags via the Azure portal.
    
*   Task 2: Enforce tagging via an Azure Policy.
    
*   Task 3: Apply tagging via an Azure Policy.
    
*   Task 4: Configure and test resource locks.
    

Task 1: Assign tags via the Azure portal
----------------------------------------

In this task, you will create and assign a tag to an Azure resourcegroup via the Azure portal. Tags are a critical component of agovernance strategy as outlined by the Microsoft Well-ArchitectedFramework and Cloud Adoption Framework. Tags can allow you to quicklyidentify resource owners, sunset dates, group contacts, and othername/value pairs that your organization deems important. For this task,you assign a tag identifying the resource Cost Center.

*   \[ \] Sign in to the **Azure portal** - https://portal.azure.com.
    
*   \[ \] Search for and select Resource groups.
    
*   SettingValueSubscription nameyour subscriptionResource group nameaz104-rg2Location**East US**Note: For each lab in this course you will create a new resource group. This lets you quickly locate and manage your lab resources.
    
*   SettingValueNameCost CenterValue000
    
*   \[ \] Select **Review + Create**, and then select **Create**.
    

Task 2: Enforce tagging via an Azure Policy
-------------------------------------------

In this task, you will assign the built-in _Require a tag and its value on resources_policy to the resource group and evaluate the outcome. Azure Policy canbe used to enforce configuration, and in this case, governance, to yourAzure resources.

*   \[ \] In the Azure portal, search for and select Policy.
    

*   \[ \] Search for the Require a tag and its value on resources built-in policy. Select the policy and take a minute to review the definition.
    
*   \[ \] Select **Assign policy**.
    
*   SettingValueSubscription_your subscription_Resource Group**az104-rg2**Note: You can assign policies on the managementgroup, subscription, or resource group level. You also have the optionof specifying exclusions, such as individual subscriptions, resourcegroups, or resources. In this scenario, we want the tag on all theresources in the resource group.
    
*   SettingValueAssignment name\`Require Cost Center tag and its value on resourcesDescriptionRequire Cost Center tag and its value on all resources in the resource groupPolicy enforcementEnabledNote: The Assignment name is automatically populated with the policy name you selected, but you can change it. The Description is optional. Notice you can disable the policy at any time.
    
*   SettingValueTag NameCost CenterTag Value000
    
*   \[ \] Click **Next** and review the **Remediation** tab. Leave the **Create a Managed Identity** checkbox unchecked.
    
*   Note: Now you will verify that the new policyassignment is in effect by attempting to create an Azure Storage accountin the resource group. You will create the storage account withoutadding the required tag.Note: It might take between 5 and 10 minutes for the policy to take effect.
    
*   \[ \] In the portal, search for and select Storage Accounts, and select **\+ Create**.
    
*   SettingValueResource group**az104-rg2**Storage account name_any globally unique combination of between 3 and 24 lower case letters and digits, starting with a letter_
    
*   \[ \] Select **Review** and then click **Create**.
    

> Note: By clicking the Raw Error tab, you can find more details about the error, including the name of the role definition Require a tag and its value on resources. The deployment failed because the storage account you attempted to create did not have a tag named Cost Center with its value set to Default.

Task 3: Apply tagging via an Azure policy
-----------------------------------------

In this task, we will use the new policy definition to remediate anynon-compliant resources. In this scenario, we will make any childresources of a resource group inherit the **Cost Center** tag that was defined on the resource group.

*   \[ \] In the Azure portal, search for and select Policy.
    
*   \[ \] In the **Authoring** section, click **Assignments**.
    
*   \[ \] In the list of assignments, click the ellipsis icon in the row representing the **Require a tag and its value on resources** policy assignment and use the **Delete assignment** menu item to delete the assignment.
    
*   SettingValueSubscriptionyour Azure subscriptionResource Groupaz104-rg2
    
*   \[ \] To specify the **Policy definition**, click the ellipsis button and then search for and select Inherit a tag from the resource group if missing.
    
*   SettingValueAssignment nameInherit the Cost Center tag and its value 000 from the resource group if missingDescriptionInherit the Cost Center tag and its value 000 from the resource group if missingPolicy enforcementEnabled
    
*   SettingValueTag NameCost Center
    
*   SettingValueCreate a remediation taskenabledPolicy to remediate**Inherit a tag from the resource group if missing**Note: This policy definition includes the Modify effect. So, a managed identity is required.
    
*   Note: To verify that the new policy assignment isin effect, you will create another Azure storage account in the sameresource group without explicitly adding the required tag.Note: It might take between 5 and 10 minutes for the policy to take effect.
    
*   \[ \] Search for and select Storage Account and click **\+ Create**.
    
*   SettingValueStorage account name_any globally unique combination of between 3 and 24 lower case letters and digits, starting with a letter_
    
*   \[ \] Verify that this time the validation passed and click **Create**.
    
*   \[ \] Once the new storage account is provisioned, click **Go to resource**.
    
*   Did you know? If you search for and select Tags in the portal, you can view the resources with a specific tag.
    

Task 4: Configure and test resource locks
-----------------------------------------

In this task, you configure and test a resource lock. Locks prevent either deletions or modifications of a resource.

*   \[ \] Search for and select your resource group.
    
*   \[ \] In the **Settings** blade, select **Locks**.
    
*   SettingValueLock namerg-lockLock type**delete** (notice the selection for read-only)
    
*   \[ \] Navigate to the resource group **Overview** blade, and select **Delete resource group**.
    
*   \[ \] In the **Enter resource group name to confirm deletion** textbox provide the resource group name, az104-rg2. Notice you can copy and paste the resource group name.
    
*   \[ \] Notice the warning: Deleting this resource group and its dependent resources is a permanent action and cannot be undone. Select **Delete**.
    
*   Note: You will need to remove the lock if you intend to delete the resource group.
    

Cleanup your resources
----------------------

If you are working with **your own subscription** take aminute to delete the lab resources. This will ensure resources arefreed up and cost is minimized. The easiest way to delete the labresources is to delete the lab resource group.

*   In the Azure portal, select the resource group, select **Delete the resource group**, **Enter resource group name**, and then click **Delete**.
    
*   Using Azure PowerShell, Remove-AzResourceGroup -Name resourceGroupName.
    
*   Using the CLI, az group delete --name resourceGroupName.
    

Extend your learning with Copilot
---------------------------------

Copilot can assist you in learning how to use the Azure scriptingtools. Copilot can also assist in areas not covered in the lab or whereyou need more information. Open an Edge browser and choose Copilot (topright) or navigate to [_copilot.microsoft.com_](http://copilot.microsoft.com). Take a few minutes to try these prompts.

*   What are the Azure PowerShell and CLI commands for adding and deleting resource locks on a resource group?
    
*   Tabulate the differences between Azure policy and Azure RBAC, include examples.
    
*   What are the steps to enforce Azure policy and remediate resources which are not compliant?
    
*   How can I get a report of Azure resources with specific tags?
    

Key takeaways
-------------

Congratulations on completing the lab. Here are the main takeaways for this lab.

*   Azure tags are metadata that consists of a key-value pair. Tagsdescribe a particular resource in your environment. In particular,tagging in Azure enables you to label your resources in a logicalmanner.
    
*   Azure Policy establishes conventions for resources. Policydefinitions describe resource compliance conditions and the effect totake if a condition is met. A condition compares a resource propertyfield or a value to a required value. There are many built-in policydefinitions and you can customize the policies.
    
*   The Azure Policy remediation task feature is used to bring resources into compliance based on a definition and assignment. Resources thatare non-compliant to a modify or deployIfNotExist definition assignment, can be brought into compliance using a remediation task.
    
*   You can configure a resource lock on a subscription, resource group, or resource. The lock can protect a resource from accidental userdeletions and modifications. The lock overrides any user permissions.
    
*   Azure Policy is pre-deployment security practice. RBAC and resource locks are post-deployment security practice.