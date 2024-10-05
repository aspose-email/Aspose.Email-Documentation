---
title: "Прагматический доступ к контактам Outlook"
url: /ru/net/pragmatically-access-outlook-contacts/
weight: 180
type: docs
---


## **VSTO**
Ниже приведен код для программного доступа к контактам Outlook:

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

    MessageBox.Show("У вас " + counter + " контактов с фамилиями, которые содержат " + findLastName + ".");

```
## **Aspose.Email**
Класс MapiContact можно использовать для загрузки контактов в формате Outlook MSG и VCard. Следующий пример кода показывает, как загрузить контакты Outlook, сохраненные в формате MSG и VCF, в MapiContact.

``` cs

     var vcfTest = VCardContact.Load("Jon.vcf");

    MapiContact contact = MapiContact.FromVCard(@"E:\Aspose\Aspose Vs VSTO\Aspose.Emails Vs VSTO Outlook v 1.1\Sample Files\Jon.vcf");

    Console.WriteLine(contact.NameInfo.DisplayName);

```
## **Скачать образец кода**
- [Codeplex](https://asposevsto.codeplex.com/releases/view/616980)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.1)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977)
## **Скачать исполняемый код**
- [Codeplex](https://asposevsto.codeplex.com/SourceControl/latest#Aspose.Email)
- [Github](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Programmatically%20Access%20Outlook%20Contacts)
- [Code.MSDN](https://code.msdn.microsoft.com/AsposeEmail-Vs-VSTO-fa535977/view/SourceCode#content)