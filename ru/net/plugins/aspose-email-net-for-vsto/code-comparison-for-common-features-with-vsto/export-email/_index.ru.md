---
title: "Экспорт электронной почты"
url: /ru/net/export-email/
weight: 110
type: docs
---


## **VSTO**
Ниже представлен код для экспорта электронной почты с использованием VSTO Outlook.

``` cs

  string FilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\ExportEmail.msg";

 // Создание класса Application и получение пространства имен

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Получение информации о Входящих в объекте типа MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 Outlook.MailItem item = inbox.Items[0];

 item.SaveAs(FilePath,_missing);       

```
## **Aspose.Email**
Ниже представлен код для экспорта электронной почты с использованием aspose.email для .NET.

``` cs

  string FilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\ExportEmail.msg";

 //Создание экземпляра класса MailMessage

 MailMessage msg = new MailMessage();

 //Экспорт в формат MHT

 msg.Save(FilePath, SaveOptions.DefaultMsg);

```
## **Скачать Исходный Код**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Delete%20Messages)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Скачать Рабочий Пример**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)