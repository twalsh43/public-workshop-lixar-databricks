## Setup Task 0 - Log into the Azure Portal

 1. Go to the Azure Portal https://portal.azure.com/ 

 2. If already logged in skip to Task 1 </br>
    Otherwise, paste the username you were given from the email

 <p align="center"> <img src="images/setup-signin.png"/> </p>

 And on the next screen, paste the password you received in the email

## Setup Task 1 - Add Access Policy to Key Vault

 1. Select Resource Groups and select the only resource group

 <p align="center"> <img src="images/setup02-resource-groups.png"/> </p>

 2. Select your Key Vault 
  <p align="center"> <img src="images/setup02-select-key-vault.png"/> </p>

 3. Select Access Policies

 <p align="center"> <img src="images/setup02-access-policy.png"/> </p>

 5. Select “Add Access Policy”
 <p align="center"> <img src="images/setup02-add-access-policy.png"/> </p>

 3. Select Principal → Select none selected. <br>
 Type (or copy from your email) and select the username which you logged into the azure portal with, similar to this account below <br>
odl_user_XXXXXX@msazurelabs.onmicrosoft.com <br>
You will see a different user name than yours throughout this document, but yours will remain the same.

 <p align="center"> <img src="images/setup02-principal-access-policy.png"/> </p>

 4. Select the Select button
 <p align="center"> <img src="images/setup02-select.png"/> </p>


 5. Select Configure from template “Key, Secret, & Certificate Management” and select Add. <b>Ensure to Save in the next step prior to navigating away</b>

 <p align="center"> <img src="images/setup02-configure_from_template.png"/> </p>

 6. <b>Select Save to save your new access policy</b>
 <p align="center"> <img src="images/setup02-save-access-policy.png"/> </p>

 7. Go back to your Resource by by selecting Overview in your Key Vault
 <p align="center"> <img src="images/setup02-overview-key-vault.png"/> </p>

 8. Then select your specific resource group
 <p align="center"> <img src="images/setup02-resource-group-key-vault.png"/> </p>

## Setup Task 2 - Create Container

 1. Select your storage account
 <p align="center"> <img src="images/setup02-select-storage-acc.png"/> </p>

 2. Select containers
 <p align="center"> <img src="images/setup02-select-storage-container.png"/> </p>

 5. Select “+ Containers”, and name the container exactly as below</br>
databricks-workshop
 <p align="center"> <img src="images/setup02-add_container.png"/> </p>

 6. Select create
 <p align="center"> <img src="images/setup02-add_container_name.png"/> </p>

## Setup Task 3 - Copy Storage Account Secret
 1. Within the storage account select Access keys
 <p align="center"> <img src="images/setup02-access-keys.png"/> </p>

 2. Select Show Keys
 <p align="center"> <img src="images/setup02-show-keys.png"/> </p>

 3. Select the copy button to the far right of the first key, for this screen this key has been obfuscated and your key will show fully. 
 <p align="center"> <img src="images/setup02-copy-key.png"/> </p>

 4. Select Overview in your Storage Account and select your specific resource group
 <p align="center"> <img src="images/setup02-resource-group-storage-acc.png"/> </p>

## Setup Task 4 - Add Storage Account Secret
 1. Select your Key Vault 
  <p align="center"> <img src="images/setup02-select-key-vault.png"/> </p>

 2. Within the Key Vault, Select Secrets (not keys)
 <p align="center"> <img src="images/setup02-key-vault-secrets.png"/> </p>

 3. Then Generate and Import
 <p align="center"> <img src="images/setup02-key-vault-generate.png"/> </p>

 4. For the value, paste in the copied key from the storage account in the value textbox. <br>
 NOTE: if it does not successfully paste, go back to the other tab (Storage Account Access Keys), copy the key1 value again, go back to the Key Vault Secrets tab, and paste the Value again.
 <p align="center"> <img src="images/setup02-mysecretADLSKey.png"/> </p>

 5. For name put the following exactly (no spaces) <br>
 mysecretADLSKey
 <p align="center"> <img src="images/setup02-mysecretADLSKey.png"/> </p>

 6. Then select create
  <p align="center"> <img src="images/setup02-add_container_name.png"/> </p>

 7. **IMPORTANT:** Keep this tab open, because we will need to use the Key Vault during the next task.


## This task was a bit involved but grants the following advantages:
- **Data Security:** The Azure Key Vault is a secure place to store the access credentials to our storage account, so outsiders cannot access our data.
- **Allow Databricks Access to Data**: Next, we will create a secure connection between DataBricks and the Key Vault (using a DataBricks Secret Scope). This will allow Databricks to access the Storage Account, where we will be writing our Delta Tables to.