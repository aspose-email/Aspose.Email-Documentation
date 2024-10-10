---
title: "Использование рабочей книги Microsoft Excel в качестве тела сообщения и отправка электронной почты"
url: /ru/net/using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email/
weight: 160
type: docs
---


В этой статье используется рабочая книга Microsoft Excel в качестве тела электронной почты и отправляется получателям. Aspose.Email для .NET работает с сетевыми протоколами и функциями Microsoft Outlook и не может обрабатывать рабочие книги Microsoft Excel. Чтобы обойти это, примеры в этой статье используют Aspose.Cells для .NET для загрузки рабочей книги Excel и конвертации ее в поток HTML. Aspose.Email для .NET затем использует поток HTML в теле электронной почты. Программный пример показывает, как отправить рабочий лист Excel в качестве тела электронной почты с использованием Aspose.Cells для .NET и Aspose.Email для .NET.

1. Загрузка рабочей книги Microsoft Excel с использованием класса Workbook из Aspose.Cells
1. Сохраните загруженную книгу в MemoryStream в формате HTML
1. Получите HTML из потока в виде строки
1. Определите новый объект MailMessage и установите его HtmlBody на HTML-контент из шага 3
1. Отправьте электронную почту, используя класс SmtpClient из Aspose.Email для .NET

Исходная рабочая книга Excel выглядит следующим образом:


![todo:image_alt_text](using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email_1.png)



Когда сообщение было отправлено и получено в Microsoft Outlook, оно выглядит как сообщение ниже:


![todo:image_alt_text](using-a-microsoft-excel-worksheet-as-the-message-body-and-sending-email_2.png)



Следующий фрагмент кода показывает, как отправить рабочий лист MS Excel в качестве тела сообщения и отправить электронную почту.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendExcelWorksheetAsMessageBody-SendExcelWorksheetAsMessageBody.cs" >}}