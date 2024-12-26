---
title: Working with Outlook Contacts using C++ Email Parser Library
ArticleTitle: Working with Outlook Contacts using C++ Email Parser Library
linktitle: Working with Outlook Contacts
type: docs
weight: 90
url: /cpp/working-with-outlook-contacts/
description: C++ Email Parser Library allows you to create, save and read Outlook contacts and import contacts from MSG and VCard file formats.
---

## **Creating, Saving and Reading Contacts**
Like MapiMessage, Aspose.Email allows you to create Outlook contacts. The MapiContact class provides all the contact related properties required to create an Outlook contact. This article shows how to create, save and read an Outlook contact using the MapiContact class.

### **Create and Save Outlook Contact**
To create a contact and save it to disc:

1. Instantiate a new object of the MapiContact class.
1. Enter contact property information.
1. Add photo data (if any).
1. Save the contact as MSG or VCard format.

The following code snippet shows you how to create and save outlook contact with C++ Email Parser Library or API.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cpp" >}}

### **Reading a MapiContact**
The MapiContact class can be used to load both Outlook MSG and VCard format contacts. The following code snippet shows you how to load Outlook contacts saved as MSG and VCF into a MapiContact.

#### **Loading a Contact from MSG**
The following code snippet shows you how to loading a contact from MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}

#### **Loading a Contact from VCard**
The following code snippet shows you how to loading a contact from vCard.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cpp" >}}
