---
title: Create, Save, and Load Outlook Contacts in C++
ArticleTitle: Create, Save, and Load Outlook Contacts in C++
linktitle: Working with Outlook Contacts
type: docs
weight: 90
url: /cpp/outlook-mapi-contacts/
description: Create, save, and load Outlook contacts in C++ using MapiContact. Work with properties, photos, MSG, and vCard formats.
---


**Aspose.Email for C++** allows you to create and manage Microsoft Outlook contacts programmatically. The [MapiContact](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_contact/) class provides all contact-related properties including names, professional info, addresses, email accounts, phone numbers, categories, custom fields, and photos.

This article demonstrates how to create, save, and read Outlook contacts in MSG and vCard (VCF) formats.


## **Create and Save an Outlook Contact**

To create an Outlook contact and save it to disk, follow the steps below:

1. Instantiate [MapiContact](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_contact/).
2. Populate name, professional, personal, and address details.
3. Add electronic addresses and telephone numbers.
4. Assign categories, mileage, billing, and custom fields.
5. Optionally, embed a contact photo.
6. Save the contact in MSG or vCard (VCF) format.

The following code sample demonstrates how to create an Outlook contact with detailed personal, professional, and organizational information and save it in different formats:

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cpp" >}}

## **Read a Contact using MapiContact**

The [MapiContact](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_contact/) class can load Outlook contacts saved in both MSG and VCF formats.

### **Load a Contact from MSG**

The following code sample demonstrates how to load a contact from an Outlook MSG file and convert it to a [MapiContact](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_contact/) object.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromMSG-LoadingContactFromMSG.cpp" >}}

### **Load a Contact from vCard (VCF)**

The following code sample demonstrates how to load contact information from a vCard (VCF) file using two different approaches in Aspose.Email for C++. It shows both the [VCardContact](https://reference.aspose.com/email/cpp/class/aspose.email.personal_info.v_card.v_card_contact/) class method for direct vCard loading and the [MapiContact](https://reference.aspose.com/email/cpp/class/aspose.email.mapi.mapi_contact/) class method for converting vCard data into an Outlook MAPI contact format, providing flexibility for working with contact data in different application contexts.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cpp" >}}
