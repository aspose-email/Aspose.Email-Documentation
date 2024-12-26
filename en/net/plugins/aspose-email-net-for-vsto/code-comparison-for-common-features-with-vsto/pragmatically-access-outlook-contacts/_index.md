---
title: Pragmatically access Outlook Contacts
ArticleTitle: Pragmatically access Outlook Contacts
type: docs
weight: 180
url: /net/pragmatically-access-outlook-contacts/
---


## **VSTO**
Below is the code to access contact from Outlook progmatically:

``` cs

    Outlook.MAPIFolder folderContacts = this.Application.ActiveExplorer().Session.

   GetDefaultFolder(Outlook.OlDefaultFolders.olFolderContacts);

   Outlook.Items searchFolder = folderContacts.Items;

   int counter = 0;

   foreach (Outlook.ContactItem foundContact in searchFolder)

   {

      if (foundContact.LastName.Contains(findLastName))

      {

         foundContact.Display(false);

         counter = counter + 1;

      }

    }

    MessageBox.Show("You have " + counter +  " contacts with last names that contain " + findLastName + ".");


```
## **Aspose.Email**
The MapiContact class can be used to load both Outlook MSG and VCard format contacts. The following code samples show how to load Outlook contacts saved as MSG and VCF into a MapiContact.

``` cs

     var vcfTest = VCardContact.Load("Jon.vcf");

    MapiContact contact = MapiContact.FromVCard(@"E:\Aspose\Aspose Vs VSTO\Aspose.Emails Vs VSTO Outlook v 1.1\Sample Files\Jon.vcf");

    Console.WriteLine(contact.NameInfo.DisplayName);


```
## **Download Sample Code**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Download Running Code**
- [Codeplex](https://asposevsto.codeplex.com/SourceControl/latest#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Programmatically%20Access%20Outlook%20Contacts)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)
