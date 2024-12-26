---
title: Working with PST Password Protection Properties
ArticleTitle: Working with PST Password Protection Properties
type: docs
weight: 110
url: /cpp/working-with-pst-password-protection-properties/
---

## **Working with PST Password Protection Properties**
Microsoft Outlook lets users password-protect PST files to restrict access to them. Aspose.Email can detect password protection on a PST file. This article shows how to:

- Remove/Reset the Password property from the PST
- Setting/Changing PST Password
### **Removing/Resetting PR_PST_PASSWORD Property**
Removal of the PR_PST_PASSWORD property cannot be achieved as other properties are removed from a message store. Instead, we need to set its value to zero (0) in order to get it removed. The "Store" property of the PST class allows accessing store properties of PST instead of MessageStoreProperties of PST in this case. The following code snippet shows you how to Remove/Reset PR_PST_PASSWORD Property.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-RemovingPaswordProperty-RemovingPaswordProperty.cpp" >}}
### **Setting Password on PST Files**
The following code snippet shows you how to set the password on PST files.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Outlook-SetPasswordOnPST-SetPasswordOnPST.cpp" >}}
