---
title: Working with PST Password Protection Properties
type: docs
weight: 100
url: /net/working-with-pst-password-protection-properties/
---

## **Working with PST Password Protection Properties**
Microsoft Outlook lets users password protect PST files to restrict access to them. Aspose.Email can detect password protection on a PST file. This article shows how to:

- [Check for Password Protection of a PST](#check-for-password-protection)
- [Remove/Reset the Password property from the PST](#removingreseting-pr_pst_password-property)
- [Setting/Changing PST Password](#setting-password-on-pst-files)
### **Check for Password protection**
The [MapiPropertyTag.PR_PST_PASSWORD](https://reference.aspose.com/email/net/aspose.email.mapi.mapipropertytag.pr/pst/fields/password) value from the [MapiPropertyTag](https://reference.aspose.com/email/net/aspose.email.mapi/mapipropertytag) class is used to check if a file is password protected. The CRC-32 hash of the password string is stored in the PidTagPstPassword (tag = 0x67ff0003) property in the [MessageStore](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore). If this property exists and is nonzero, then the PST is password protected. The following code snippet shows you how to check if the PST is password protected. It also shows how to check whether the provided password is correct or not.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CheckPasswordProtection-CheckPasswordProtection.cs" >}}
### **Removing/Reseting PR_PST_PASSWORD Property**
Removal of the [PR_PST_PASSWORD](https://reference.aspose.com/email/net/aspose.email.mapi.mapipropertytag.pr/pst/fields/password) property cannot be achieved as other properties are removed from a message store. Instead, we need to set its value to zero (0) in order to get it removed. The "Store" property of the PST class allows access to the store properties of PST instead of MessageStoreProperties of PST in this case. The following code snippet shows you how to Remove/Reset [PR_PST_PASSWORD](https://reference.aspose.com/email/net/aspose.email.mapi.mapipropertytag.pr/pst/fields/password) Property.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RemovingPaswordProperty-RemovingPaswordProperty.cs" >}}
### **Setting Password on PST Files**
The following code snippet shows you how to set a password on PST files.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetPasswordOnPST-SetPasswordOnPST.cs" >}}
## **Password Verification for Password Protected PST Files**
Aspose.Email enables the developers to check if the PST file is password protected and to check if the given password is correct or not. For this, the API provides the [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/properties/ispasswordprotected) property and [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/methods/ispasswordvalid) method. The [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/properties/ispasswordprotected) property returns **true** if the PST file is password protected and **false** if it is not. The [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/methods/ispasswordvalid) method which takes the string password as a parameter and returns **true** if the password is correct and false it is incorrect.

The following code snippet demonstrates the use of [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/properties/ispasswordprotected) property and [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/methods/ispasswordvalid) method.
### **Sample Code**
{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Outlook-PSTPasswordValidation-1.cs" >}}
### **Console Output**
The storage is password protected - True
Password is valid - True
