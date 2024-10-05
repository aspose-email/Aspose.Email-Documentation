---
title: Извлечение Вложений
type: docs
weight: 120
url: /net/extracting-attachment/
---


## **VSTO**
Ниже приведен код для извлечения вложений с использованием VSTO Outlook.

``` cs

  string AttachmentFilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\";

 // Создайте класс Application и получите пространство имен

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Получите информацию о папке Входящие в объекте типа MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 Outlook.MailItem item = inbox.Items[0];

 for (int i = 1; i <= item.Attachments.Count; i++)

 {

   item.Attachments[i].SaveAsFile(AttachmentFilePath + item.Attachments[i].FileName);

 }

```
## **Aspose.Email**
Ниже приведен код для извлечения вложений с использованием aspose.email для .NET.

``` cs

  string FilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\ExtractAttachment.msg";

 string AttachmentFilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\";

 //Создайте экземпляр MailMessage и загрузите файл электронной почты

 MailMessage mailMsg = MailMessage.Load(FilePath, MailMessageLoadOptions.DefaultEml);

 foreach (Attachment attachment in mailMsg.Attachments)

 {

   //Чтобы отобразить имя файла вложения

   attachment.Save(AttachmentFilePath+attachment.Name);

   Console.WriteLine(attachment.Name);

 }

 mailMsg.From = "sender@sender.com";

 mailMsg.To.Add("receiver@receiver.com");

 SmtpClient client = new SmtpClient("smtp.server.com");

 client.Port = 25;

 client.Username = "UserName";

 client.Password = "password";

 {

   client.Send(mailMsg);

 }

```
## **Скачать Исходный Код**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Extracting%20Attachment)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Скачать Рабочий Пример**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)