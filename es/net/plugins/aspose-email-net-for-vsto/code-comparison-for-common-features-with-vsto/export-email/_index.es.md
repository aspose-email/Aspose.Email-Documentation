---
title: "Exportar correo electrónico"
url: /es/net/export-email/
weight: 110
type: docs
---


## **VSTO**
A continuación se muestra el código para exportar el correo electrónico con VSTO Outlook.

``` cs

  string FilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\ExportEmail.msg";

 // Create Application class and get namespace

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Get Inbox information in objec of type MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 Outlook.MailItem item = inbox.Items[0];

 item.SaveAs(FilePath,_missing);      

```
## **Aspose.Email**
A continuación se muestra el código para exportar el correo electrónico mediante aspose.email para.NET.

``` cs

  string FilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\ExportEmail.msg";

 //Create an instance of the MailMessage class

 MailMessage msg = new MailMessage();

 //Export to MHT format

 msg.Save(FilePath, SaveOptions.DefaultMsg);

```
## **Descargar código fuente**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Delete%20Messages)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Descargar Running Example**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)
