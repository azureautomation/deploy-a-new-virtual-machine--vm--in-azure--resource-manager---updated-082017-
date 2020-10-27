Deploy a new Virtual Machine (VM) in Azure (Resource Manager) (updated 08/2017)
===============================================================================

            

**Simple and Easy way to deploy Azure VM's using Resource Manager API**


**Script has now been updated to include Managed Disks** *** *
**


This is a demo script for deploying Azure Virtual Machines using the Resource Manager (RM) API.


There are other ways (Link below to AzureRM template deployment) to deploy VM's using RM with templates, this is just much easier.


I would still always consider a declarative (Template) approach instead of
**this** imperative approach for deployment.


When deploying in Resource groups I suggest that you use a good naming standards for your resources when deploying them.


E.g. these are my examples only.







**ResourceType**




**Prefix**




**E.g.**






AvailabilitySet




as




asDev3






VirtualMachine




vm




vmDev3-01






VirtualNetwork




vn




vnDev3-01






Subnet




sn




snDev3-01






StorageAccount




sa




sadev3 (must be lower case)






ResourceGroup




rg




rgDev3






KeyvaultVaultName




kv




kvDev3






NetworkInterface




NIC_vm




NIC_VMDev3-01






PublicIPAddress




PublicIP_vm


PublicIP_vng




PublicIP_vmDev3-01


PublicIP_vngDev3






VirtualNetworkGateway




vng




vngDev3






VirtualNetworkGatewayIpConfig




vngip




vngipDev3






VirtualNetworkGatewayConnection




vngc




vncgDev3







** **


This script presumes that you have an **azure subscription **and that you
**are connected**.


You can test by running:


**Get-AzureRMContext**


This script presumes that you have the correct **AzureRM modules** installed.


There is some custom stuff in this demo script that I have not explained, so use what you need, delete the rest.


This script uses some DSC extensions that you would need to deploy before calling them.


#WorksonMyMachine : )


 


**Other scripts for deploying Vm's** *** *
**







Deploy Virtual Machine into Azure (service manager)




[https://gallery.technet.microsoft.com/Deploy-a-new-Virtual-8b524c26](https://gallery.technet.microsoft.com/Deploy-a-new-Virtual-8b524c26)






Deploy Virtual Machine into Azure (resource manager)




[https://gallery.technet.microsoft.com/Deploy-a-new-Virtual-75cd3230](https://gallery.technet.microsoft.com/Deploy-a-new-Virtual-75cd3230)






Deploy Virtual Machine into Hyper-V




[https://gallery.technet.microsoft.com/Deploy-a-new-Virtual-f42812ac](https://gallery.technet.microsoft.com/Deploy-a-new-Virtual-f42812ac)






Deploy Virtual Machine/s into Azure (resource manager) using JSON template.




[https://github.com/brwilkinson/MulitTierArmV4](https://github.com/brwilkinson/MulitTierArmV4)






Script to delete a Virtual Machine and disks and NIC




[https://gallery.technet.microsoft.com/scriptcenter/Delete-Azure-RM-Virtual-fc09d944](https://gallery.technet.microsoft.com/scriptcenter/Delete-Azure-RM-Virtual-fc09d944)







** *** *


 


In order to run this script you will need to **create the keyvault first
**and then the **Keyvault secret *** *


* *#-----------
$rgName = 'myRgName'
$kvName = 'myKVName'

New-AzureRmKeyVault -ResourceGroupName $rgName -VaultName $KVName -Location eastus -Sku premium -EnabledForTemplateDeployment -EnabledForDeployment

$Secret = Read-Host -AsSecureString -Prompt Entercred

Set-AzureKeyVaultSecret -VaultName $KVName -Name Admin -SecretValue $Secret -ContentType txt


Get-AzureKeyVaultSecret -VaultName $KVName  -Name Admin

Then you never have to hard code passwords in scripts.


 

 

        
    
TechNet gallery is retiring! This script was migrated from TechNet script center to GitHub by Microsoft Azure Automation product group. All the Script Center fields like Rating, RatingCount and DownloadCount have been carried over to Github as-is for the migrated scripts only. Note : The Script Center fields will not be applicable for the new repositories created in Github & hence those fields will not show up for new Github repositories.
