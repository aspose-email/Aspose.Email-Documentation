---
title: Working with PST Password Protection Properties
type: docs
weight: 100
url: /java/working-with-pst-password-protection-properties/
---

{{% alert color="primary" %}} 

Microsoft Outlook lets users password-protect PST files to restrict access to them. Aspose.Email can detect password protection on a PST file. This article shows how to check a PST for a password and also how to check if the password applied to it is correct.

{{% /alert %}} 

## **Check for Password protection**

The [MapiPropertyTag.PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) value from the [MapiPropertyTag](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/) class is used to check if a file is password protected.

The CRC-32 hash of the password string is stored in the PidTagPstPassword (tag = 0x67ff0003) property in the [MessageStore](https://reference.aspose.com/email/java/com.aspose.email/messagestore/). If this property exists and is non-zero, then the PST is password protected.

The following code snippet shows how to check if a PST file is password protected and whether the given string is a valid password for that PST.

The code snippet below shows two functions, the first checks if the PST is password-protected, and the second shows how to check whether a provided password is correct or not.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-CheckForPasswordProtection.java" >}}

## **Remove/Reset the PR_PST_PASSWORD Property**

Removal of the [PR_PST_PASSWORD](https://reference.aspose.com/email/java/com.aspose.email/mapipropertytag/#PR-PST-PASSWORD) property cannot be achieved as other properties are removed from a message store. Instead, we need to set its value to zero (0) in order to get it removed. The "Store" property of the PST class allows access to the store properties of PST instead of MessageStoreProperties of PST in this case.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-RemovePSTPasswordProperty.java" >}}

## **Set/Change PST Password**

The following code snippet shows you how to set a password on PST files.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordProtectionProperties-SetPSTPassword.java" >}}

## **Password Verification for Password Protected PST Files**

Aspose.Email enables the developers to check if the PST file is password protected and to check if the given password is correct or not. For this, the API provides the [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) property and [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) method. The [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) property returns **true** if the PST file is password protected and **false** if it is not. The [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) method which takes the string password as a parameter and returns **true** if the password is correct and false it is incorrect.

The following code snippet demonstrates the use of [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordProtected--) property and [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/java/com.aspose.email/messagestore/#isPasswordValid-java.lang.String-) method.

### **Sample Code**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-PSTPasswordValidation-1.java" >}}

### **Console Output**

The storage is password protected - True
Password is valid - True
